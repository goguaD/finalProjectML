# finalProjectML

მონაცემები:
train.csv: ყოველკვირეული გაყიდვების მონაცემები 2010-დან to 2012-მდე.

test.csv: სატესტო მონაცემები.

features.csv: შემდეგი დამატებითი ინფორმაცია: ტემპერატურა, ბენზინის ფასი, CPI(The Consumer Price Index), უმუშევრობა, ფასდაკლებები, დღესასწაულები

stores.csv: დამატებითი ინფორმაცია ყველა მაღაზიაზე: მაღაზიის ტიპები და ზომები.

sampleSubmission.csv: საბმიშენის ფორმატი.

## Exploratory Data Analysis (EDA)
<img width="1243" height="496" alt="image" src="https://github.com/user-attachments/assets/fa3ff40c-afa2-463d-ad21-7a79c963de20" />

### Key Findings and Patterns

#### 1. გაყიდვების განაწილება
- **სეზონური პატერნები**: ცალსახა სეზონური პიკები ყველაზე დიდ გავლენას ახდენს ყოველკვირეულ გაყიდვებზე
- **დღესასწაულების სეზონური გავლენა**: ნოემბერი-დეკემბრის პერიოდში ცალსახა პიკს ვხედავთ
- **ყოველწლიური ტრენდები**: გაყიდვები შუა წელში მცირდება და წლის ბოლოს, არდადეგების პერიოდში იზრდება
<img width="1243" height="496" alt="image" src="https://github.com/user-attachments/assets/05bd2140-198f-4264-91a8-a0c1c203b850" />

#### 2. მაღაზიების პერფორმანსი
- **მაღაზიის ტიპები**: A ტიპის მაღაზიები საშუალოდ ყველაზე დიდ შემოსავალს ნახულობენ
- **მაღაზიების ზომასთან კორელაცია**: დიდი მაღაზიები მეტ შემოსავალს იღებენ, თუმცა შედარებით ნაკლები კორელაცია აქვთ გაყიდვების ზრდასთან
<img width="577" height="459" alt="image" src="https://github.com/user-attachments/assets/2b8f97bc-caee-4007-818b-b6959f8d4344" />

<img width="904" height="556" alt="image" src="https://github.com/user-attachments/assets/6a982b29-4635-49b0-95cb-798b28c77b6f" />

#### 3. დეპარტამენტების ტრენდები
- **გაყიდვების მაღალი კონცენტრაცია**: რამდენიმე დეპარტამენტი დომინირებს გაყიდვების მოცულობით
- **Department Variability**: Activity across departments varies significantly and shows seasonal patterns
- **Performance Patterns**: Different departments exhibit unique seasonal behaviors and sales cycles
<img width="998" height="560" alt="image" src="https://github.com/user-attachments/assets/1d75d591-832b-4460-8e46-3904e1db2a24" />

#### 4. Holiday and Markdown Effects
- **დღესასწაულების გავლენა**: დღესასწაულებს დიდი გავლენა აქვს გაყიდვებზე
- **ფასდაკლებების გავლენა**: ფასდაკლებებს დადებითი გავლენა აქვს ზოგ კვირაში გაყიდვებზე
- **სეზონური პიკები**: მნიშვნელოვანი დღესასწაულები გაყოდვების პიკებს ქმნიან 
<img width="724" height="621" alt="image" src="https://github.com/user-attachments/assets/da02aa87-b546-40e4-a145-5a4465aeccb2" />
<img width="577" height="487" alt="image" src="https://github.com/user-attachments/assets/79911c33-22b1-407d-b1e6-dcf2660402ae" />

#### 5. ეკონომიკური ფაქტორების ანალიზო
- **ნაკლები გავლენა**: CPI, საწვავის ფასს, და უმუშევრობას მინიმალურიეფექტი აქვს
- **კორელაზია**: ეკონომიკურ ინდიკატორებს ძალიან სუსტი კორელაცია აქვთ ყოველკვირეულ გაყიდვებთან
- **ტემპერატურა**: ექსტრემალურ მონაცემებზე საშუალო კორელაცია აქვს


#### 7. Time Series Characteristics
- **ავტოკორელაცია**: ავტოკორელაციის პატერნები იმას მიუთითებს, რომ უახლოესი გაყიდვები მნიშვნელოვანია პროგნოზირებისთვის, ამიტომ გამოსადეგი იქნება ლეგ ფიჩერები. 
- **სეზონურობა**: ცალსახა კვირეული და თვიური პატერნებია დატასეტში
<img width="577" height="467" alt="image" src="https://github.com/user-attachments/assets/87a5e0ce-b77c-4caf-a684-a81b829aec3c" />
<img width="623" height="464" alt="image" src="https://github.com/user-attachments/assets/b420cc42-d0c9-49c2-a171-38183b492a71" />

#### 8. Feature Correlation Analysis
- **აღსანიშნავი კორელაციები**: მაღაზიის ტიპი,ზომა, და დღესასწაულები
- **სუსტი კორელაციები**: ეკონომიკური ინდიკატორები (CPI, უმუშევრობა, საწვავის ფასი) 
- **ფასდაკლების ეფექტი**: სხვადასხვა ფასდაკლებების ტიპები სხვაასხვა კორელაციაში მოდიან გაყოდვებთან
<img width="1983" height="1226" alt="image" src="https://github.com/user-attachments/assets/210543d8-682c-44ce-85ec-0677dd119ade" />


# finalProjectML
ეს პროექტი მიზნად ისახავს წინასწარმეტყველებას მაღაზიების ყოველკვირეული გაყიდვების მოცულობაზე, „Walmart Recruiting - Store Sales Forecasting“ კაგლის კონკურსის მონაცემებზე დაყრდნობით.
გამოყენებული ალგორითმები
DLinear, RandomForestRegressor, LightGBM, XGBOOST, N-BEATS, ARIMA, Prophet

მონაცემები:
train.csv: ყოველკვირეული გაყიდვების მონაცემები 2010-დან to 2012-მდე.

test.csv: სატესტო მონაცემები.

features.csv: შემდეგი დამატებითი ინფორმაცია: ტემპერატურა, ბენზინის ფასი, CPI(The Consumer Price Index), უმუშევრობა, ფასდაკლებები, დღესასწაულები

stores.csv: დამატებითი ინფორმაცია ყველა მაღაზიაზე: მაღაზიის ტიპები და ზომები.

sampleSubmission.csv: საბმიშენის ფორმატი.

Exploratory Data Analysis (EDA)

რამდენიმე მნიშვნელოვანი პატერნი:

გაყიდვების განაწილება:

ყოველკვირეულ გაყიდვებზე უდიდეს გავლენას ახდენს სეზონური პიკები.

ცალსახა სეზონური პიკებია ნოემბერი-დეკემბრის პერიოდში.

გაყიდვები მცირდება წელიწადის შუაში და იზრდება დღესასწაულებზე.

მაღაზიების ანალიზი:

A ტიპის მაღაზიები საშუალოდ მეტ შემოსავალს იღებს.

უფრო დიდი მაღაზიები ნაკლებად კორელაციაშა გაყიდვების ზრდასთან.

დეპარტამენტების ტრენდები:

გაყიდვებში რამდენიმე დეპარტამენტი დომინირებს.

დეპარტამენტებში აქტივობა ერთმანეთისგან განსხვავებული და სეზონურია.

დღესასწაულები და ფასდაკლებები:

დღესასწაულების პერიოდში ცალსახად მეტია გაყიდვები.

ფასდაკლებები ზოგიერთ კვირაში დადებით გავლენას ავლენს გაყიდვებზე.

ეკონომიკური ნაწილი:

CPI, ბენზინის ფასი, და უმუშევრობა დიდად გავლენას არ ახდენს ყოველკვირეულ გაყიდვებზე.


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

# Deep Learning

## N-BEATS

• ყველა (store, dept) კომბინაციას აქვს თავისი გაყიდვების პატერნი, ამიტომ შევქმენით უნიკალური მოდელი ყოველი წყვილისთვის.

• მონაცემები დავტვირთეთ ისე, რომ ქრონოლოგიურად სწორი ყოფილიყო, რადგან ეს N-BEATS-ისთვის აუცილებელია. N-BEATS არ საჭიროებს მონაცემთა გაწმენდას (NaN-ების დამუშავება), feature engineering-ს ან სხვა preprocessing-ის პროცესებს, რადგან ის მხოლოდ წარსულ weekly_sales-ის მონაცემებს იყენებს მომავლის პროგნოზირებისთვის.

• test/validation - 70/30

| პარამეტრი | მნიშვნელობა | აღწერა |
|----------|-------------|--------|
| h | 4 | მომავალი დროის ნაბიჯების რაოდენობა პროგნოზირებისთვის (მაგ., შემდეგი 4 კვირა). |
| input_size | 24 | რამდენი წარსული დროის ნაბიჯი გამოიყენება მომავლის პროგნოზირებისთვის. |
| start_padding_enabled | True | საშუალებას აძლევს პროგნოზირების დაწყებას მაშინაც კი, როცა input_size 24-ზე ნაკლებია. |
| max_steps | 5000 | ტრენინგის იტერაციების მაქსიმალური ზღვარი (ყველა batch-ში). ეს ზღვარი არ ნიშნავს, რომ მოდელი აუცილებლად ბოლომდე ივარჯიშებს. |
| batch_size | 128 | ერთ step-ში ერთად დამუშავებული დროითი სერიების რაოდენობა. დიდი batch-ები (128) უფრო სტაბილურ გრადიენტებს იძლევა, მაგრამ მეტ მეხსიერებას იყენებს. |
| early_stop_patience_steps | 200 | ტრენინგი შეჩერდება, თუ validation loss არ გაუმჯობესდება 200 ნაბიჯის განმავლობაში. |
| scaler_type | 'standard' | ნორმალიზაციის უკეთესი მახასიათებლებისთვის, რაც ეხმარება ნეირონულ ქსელს უფრო სწრაფი და სტაბილური კონვერგენციისთვის. |
| val_check_steps | 100 | რამდენად ხშირად აფასებს მოდელი validation-ს. |

**Validation WMAE: 1736.3801971897966**

## hyperparameter tuning

• გავზარდე input size, რათა მოდელმა მეტი წარსული ინფორმაცია მიიღოს და უკეთ ამოიცნოს პატერნები.
• გავზარდე training step უკეთესი კონვერგენციისთვის.

• გავზარდე batch_size უფრო სტაბილური გრადიენტებისთვის.

• შევამცირე batch_size უფრო ხშირი განახლებებისთვის.

• შევაფასე სხვადასხვა სკალერები, მათ შორის MinMax და Robust Scaler.

საუკეთესო შედეგი RobustScaler-მა აჩვენა, რადგან weekly_sales-ს ბევრი outlier აქვს. StandardScaler-ის დროს ეს outlier-ები ხელს უშლიდა საშუალოს და ვარიაციის სწორ განაწილებას, ხოლო RobustScaler უკეთ უმკლავდება მათ.

**Validation WMAE: 1648.15**
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
