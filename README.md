# finalProjectML
ეს პროექტი მიზნად ისახავს წინასწარმეტყველებას მაღაზიების ყოველკვირეული გაყიდვების მოცულობაზე, „Walmart Recruiting - Store Sales Forecasting“ კაგლის კონკურსის მონაცემებზე დაყრდნობით.
გამოყენებული ალგორითმები
DLinear, RandomForestRegressor, LightGBM, XGBOOST, N-BEATS, ARIMA, SARIMA

# 1. RANDOMFORESTREGRESSOR

 # სამუშაო ნაბიჯები
მონაცემების ჩატვირთვა და გაწმენდა

ჩატვირთულია train.csv, test.csv, features.csv, stores.csv

გაერთიანდა ყველა მონაცემი Store და Date სვეტებზე

თარიღიდან გამოთვლილია დამატებითი სვეტები: Year, Month, Week

ცარიელი მნიშვნელობები (Markdown ცვლადებში) ჩანაცვლდა ნულებით

კატეგორიული ცვლადი Type გადაკეთდა რიცხვობრივად (LabelEncoder-ით)

ტრენინგ ვალიდაციის გაყოფა (Train-Test Split)

მოდელი გაწვრთნილია მონაცემების 80%-ზე

შეფასებულია მონაცემების დარჩენილ 20%-ზე

შეფასება — WMAE (Weighted Mean Absolute Error)

შეცდომის დათვლა ითვალისწინებს IsHoliday სვეტს: არდადეგების კვირები 5-ჯერ მეტ წონას იძლევა

მიღებული შეფასება გვიჩვენებს, რამდენად კარგად პროგნოზირებს მოდელი რეალურ გაყიდვებს

# მოდელის გადამზადება და ფინალური პროგნოზირება

მოდელი გადამზადდა სრულ train მონაცემზე

პროგნოზები გამოთვლილია test.csv მონაცემზე

# შედეგები
ვალიდაციაზე მიღებული WMAE გვიჩვენებს მოდელის შესაძლებლობებს გაყიდვების პროგნოზირებაში.

Random Forest გთავაზობთ სტაბილურ შედეგს რამდენიმე ფუნქციის გამოყენებით, ყოველგვარი რთული ტიუნინგის გარეშე.

# 2. ARIMA
### Feature Engineering
- **დროის მახასიათებლები:** Month, Week, DayOfYear
- **Store-Department სტატისტიკა:** Sales_Mean, Sales_Std, Sales_Median, Sales_Min, Sales_Max
- **გარე ფაქტორები:** Temperature, Fuel_Price, CPI, Unemployment
- **არდადეგების მულტიპლიკატორები:** Store-Department სპეციფიული და გლობალური

### Data Splitting
- **Training:** 2010-02-05 to 2012-07-27
- **Validation:** 2012-08-03 to 2012-10-26 (13 კვირა)
- **Grouping:** Store-Department კომბინაციების მიხედვით

##  ARIMA მოდელების იმპლემენტაცია

### რატომ ARIMA?
ARIMA აირჩა რადგან:
- **Time Series ბუნება:** გაყიდვები დროში დამოკიდებულია
- **Trend და Seasonality:** ARIMA უმკლავდება ტენდენციას და სეზონურობას
- **პარამეტრების ინტერპრეტაცია:** p,d,q პარამეტრები მარტივად გასაგებია

### 1) Simple ARIMA (WMAE: 2213.76)
```python
# ბაზური ARIMA(1,1,1) ყველა Store-Dept-ზე
model = ARIMA(ts, order=(1, 1, 1))
# გლობალური არდადეგების მულტიპლიკატორი: 1.074
```

**მუშაობის პრინციპი:**
- მინიმუმ 10 დაკვირვება Store-Dept-ზე
- Weekly aggregation
- Fallback: Store-Dept საშუალო

### 2) Optimized ARIMA (WMAE: 2550.43)
```python
# მრავალი ARIMA კონფიგურაციის ტესტირება
configs = [(1,1,1), (2,1,1), (1,1,2), (0,1,1), (1,0,1), (2,1,2)]
# AIC-ით საუკეთესო მოდელის არჩევა
```

**გაუმჯობესებები:**
- Store-Dept სპეციფიული არდადეგების მულტიპლიკატორები
- ტემპერატურის კორექტირება (>80°C: 0.95x, <30°C: 1.05x)
- მინიმუმ 15 დაკვირვება

### 3) Fast Optimized ARIMA (WMAE: 2152.64)
```python
# შემცირებული კონფიგურაციები სწრაფი ოპტიმიზაციისთვის
configs = [(1,1,1), (2,1,1), (1,1,2)]
# ტემპერატურის ნაკლები გავლენა (0.98x, 1.02x)
```

**ოპტიმიზაციები:**
- მინიმუმ 12 დაკვირვება
- 80% recent + 20% overall average fallback
- სწრაფი პროცესინგი

##  WMAE მეტრიკა

```python
def compute_wmae(y_true, y_pred, is_holiday):
    weights = np.where(is_holiday, 5, 1)  # არდადეგებზე 5x წონა
    return np.sum(weights * np.abs(y_true - y_pred)) / np.sum(weights)
```

# 3. N-BEATS 

## 🔧 მონაცემთა დამუშავება

### Feature Engineering
- **დროის მახასიათებლები:** Year, Month, Week, Day, DayOfWeek, DayOfYear, IsWeekend
- **Store მახასიათებლები:** Type (encoded), Size
- **გარე ფაქტორები:** Temperature, Fuel_Price, MarkDown1-5, CPI, Unemployment
- **არდადეგების მულტიპლიკატორები:** IsHoliday (5x წონა WMAE-ში)

### Data Splitting
- **Training:** 421,570 ჩანაწერი
- **Sequences:** 261,083 სექვენსი
- **Sequence Length:** 52 კვირა (1 წელი)
- **Forecast Length:** 1 კვირა

## N-BEATS მოდელის არქიტექტურა

### რატომ N-BEATS?
N-BEATS აირჩა რადგან:
- **Interpretable:** ბაზისური ფუნქციების ინტერპრეტაცია
- **No Seasonality:** არ საჭიროებს სეზონურობის პარამეტრებს
- **Deep Learning:** 
- **Residual Learning:** ბლოკები ყოველთვის residuals-ზე მუშაობს

### მოდელის სტრუქტურა
```python
class NBeatsModel(nn.Module):
    def __init__(self, input_size=52, forecast_size=1, n_blocks=3, layers=4, layer_size=256):
        # 3 ბლოკი, თითოეული 4 ფენით
        # Generic Basis Function
        # Residual connections
```

**მუშაობის პრინციპი:**
- **Input:** 52 კვირის გაყიდვების მონაცემები
- **Blocks:** 3 ბლოკი თითოეული თავისი ბაზისური ფუნქციით
- **Residuals:** ყოველი ბლოკი residuals-ზე მუშაობს
- **Output:** 1 კვირის პროგნოზი

## მოდელის იმპლემენტაცია

### 1. NBeatsBlock
```python
class NBeatsBlock(nn.Module):
    def __init__(self, input_size, theta_size, basis_function, layers, layer_size):
        # 4 ფენა ReLU activation-ით
        # Theta layer ბაზისური ფუნქციისთვის
```

### 2. GenericBasis
```python
class GenericBasis(nn.Module):
    def forward(self, theta):
        # Backcast: input_size ზომის
        # Forecast: forecast_size ზომის
        return backcast, forecast
```

### 3. WalmartDataset
```python
class WalmartDataset(Dataset):
    def __init__(self, data, sequence_length=52, forecast_length=1):
        # Store-Dept grouping
        # Sliding window sequences
        # Holiday weights (5x for holidays)
```

##  ტრენინგის პარამეტრები

```python
SEQUENCE_LENGTH = 52      # 1 წელი
FORECAST_LENGTH = 1       # 1 კვირა
BATCH_SIZE = 32
LEARNING_RATE = 0.001
EPOCHS = 50
```

### ტრენინგის პროცესი
- **Loss Function:** MSE
- **Optimizer:** Adam
- **Device:** CUDA (GPU)
- **WMAE Tracking:** ყოველ epoch-ზე

## შედეგები

### ტრენინგის პროგრესი
- **Epoch 0:** WMAE: 1914.79
- **Epoch 10:** WMAE: 1444.74
- **Epoch 20:** WMAE: 1353.40
- **Epoch 30:** WMAE: 1299.69
- **Epoch 40:** WMAE: 1254.77
- **Final:** WMAE: 1228.61

### მოდელის უპირატესობები
- **სწრაფი ტრენინგი:** GPU-ზე ოპტიმიზებული
- **კარგი WMAE:** 1228.61 
- **Interpretable:** ბაზისური ფუნქციების ანალიზი
- **Scalable:** მრავალი Store-Dept კომბინაცია


##  MLflow Tracking

```python
# ექსპერიმენტების ლოგირება
mlflow.log_param("model", "N-BEATS")
mlflow.log_param("sequence_length", 52)
mlflow.log_metric("final_wmae", 1228.61)
```
# 3. DLinear

##  მონაცემთა დამუშავება

### Feature Engineering
- **გარე ფაქტორები:** Temperature, Fuel_Price, CPI, Unemployment
- **დროის მახასიათებლები:** Week, Year
- **არდადეგების მულტიპლიკატორები:** IsHoliday (5x წონა WMAE-ში)
- **MarkDown ფაქტორები:** MarkDown1-5 (ფასდაკლებები)

### Data Preprocessing
```python
# Log transformation for target variable
y_raw = np.log1p(store_df[target_col].values)

# StandardScaler for features
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X_raw)

# Forward fill for missing values
df = df.fillna(method='ffill')
```

### Data Splitting
- **Input Length:** 12 კვირა
- **Output Length:** 1 კვირა
- **Train/Val Split:** 80/20 (shuffle=False)
- **Store Focus:** Store 1 (პილოტი)

##  DLinear მოდელის არქიტექტურა

### რატომ LSTM?
LSTM აირჩა რადგან:
- **Sequential Data:** გაყიდვები დროში დამოკიდებულია
- **Long-term Dependencies:** შორეული კავშირების დამახსოვრება
- **Vanishing Gradient:** LSTM უმკლავდება gradient vanishing პრობლემას
- **Memory Cells:** მნიშვნელოვანი ინფორმაციის შენახვა

### მოდელის სტრუქტურა
```python
class LSTMForecaster(nn.Module):
    def __init__(self, n_features, hidden_dim=64, n_layers=2, output_len=1, dropout=0.2):
        self.lstm = nn.LSTM(
            input_size=n_features,
            hidden_size=hidden_dim,
            num_layers=n_layers,
            batch_first=True,
            dropout=dropout
        )
        self.fc = nn.Linear(hidden_dim, output_len)
```

**მუშაობის პრინციპი:**
- **Input:** 12 კვირის features (12, n_features)
- **LSTM Layers:** 2 ფენა, 64 hidden units
- **Dropout:** 0.2 overfitting-ის თავიდან ასაცილებლად
- **Output:** 1 კვირის პროგნოზი

## 📈 მოდელის იმპლემენტაცია

### Sequence Creation
```python
def make_sequences(X, y, input_len=12, output_len=1):
    # Sliding window approach
    # Input: 12 weeks of features
    # Output: 1 week prediction
```

### ტრენინგის პარამეტრები
```python
INPUT_LEN = 12          # 12 კვირა input
OUTPUT_LEN = 1          # 1 კვირა output
BATCH_SIZE = 32
LEARNING_RATE = 5e-4
EPOCHS = 30
```

### ტრენინგის პროცესი
- **Loss Function:** L1Loss (MAE)
- **Optimizer:** Adam
- **Device:** CUDA (GPU)
- **Validation:** ყოველ epoch-ზე

## 📊 შედეგები

### ტრენინგის პროგრესი
- **Epoch 1:** Train L1: 3.0910, Val L1: 1.3851
- **Epoch 10:** Train L1: 1.2996, Val L1: 1.3723
- **Epoch 20:** Train L1: 1.2988, Val L1: 1.3683
- **Epoch 30:** Train L1: 1.3002, Val L1: 1.3684

### WMAE შედეგები
```python
# Store 1-ის შედეგი
WMAE (Store 1): 18,232.87

# MLflow tracking-ში
WMAE: 37,452,165.20 (შესაძლოა overfitting)
```

### მოდელის უპირატესობები
- **Sequential Learning:** დროში დამოკიდებულებების ქმნა
- **Feature Integration:** მრავალი ფაქტორის გათვალისწინება
- **Memory Efficient:** LSTM-ის მეხსიერების უნარი
- **Scalable:** სხვა stores-ზე გამოყენება

## 🔍 MLflow Tracking

```python
# ექსპერიმენტების ლოგირება
mlflow.log_param("input_len", 12)
mlflow.log_param("output_len", 1)
mlflow.log_param("model_type", "DLinear")
mlflow.log_metric("WMAE", wmae)
```

##  შედეგების ანალიზი

### პრობლემები
- **Overfitting:** მაღალი WMAE MLflow-ში
- **Store Specific:** მხოლოდ Store 1-ზე ტესტირება
- **Feature Scaling:** log transformation შეიძლება არ იყოს ოპტიმალური

### გაუმჯობესებები
- **Multi-store Training:** ყველა store-ზე ტრენინგი
- **Hyperparameter Tuning:** უკეთესი პარამეტრების მოძიება
- **Ensemble Methods:** სხვა მოდელებთან კომბინაცია
