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

# 2.ARIMA
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
