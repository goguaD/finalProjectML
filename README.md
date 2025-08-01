# finalProjectML

მონაცემები:
train.csv: ყოველკვირეული გაყიდვების მონაცემები 2010-დან to 2012-მდე.

test.csv: სატესტო მონაცემები.

features.csv: შემდეგი დამატებითი ინფორმაცია: ტემპერატურა, ბენზინის ფასი, CPI(The Consumer Price Index), უმუშევრობა, ფასდაკლებები, დღესასწაულები

stores.csv: დამატებითი ინფორმაცია ყველა მაღაზიაზე: მაღაზიის ტიპები და ზომები.

sampleSubmission.csv: საბმიშენის ფორმატი.

## Exploratory Data Analysis (EDA)

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
<img width="1011" height="560" alt="image" src="https://github.com/user-attachments/assets/be499e84-3480-4339-9e20-fc33ea78f3bb" />

<img width="904" height="556" alt="image" src="https://github.com/user-attachments/assets/6a982b29-4635-49b0-95cb-798b28c77b6f" />

#### 3. დეპარტამენტების ტრენდები
- **გაყიდვების მაღალი კონცენტრაცია**: რამდენიმე დეპარტამენტი დომინირებს გაყიდვების მოცულობით
- **Department Variability**: Activity across departments varies significantly and shows seasonal patterns
- **Performance Patterns**: Different departments exhibit unique seasonal behaviors and sales cycles
<img width="998" height="560" alt="image" src="https://github.com/user-attachments/assets/1d75d591-832b-4460-8e46-3904e1db2a24" />
<img width="1184" height="684" alt="image" src="https://github.com/user-attachments/assets/24a0d08c-8d09-48d5-b1b8-6d9bab729224" />

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
<img width="783" height="679" alt="image" src="https://github.com/user-attachments/assets/36d8a6d7-be44-4cf7-b97e-5af09be4b97f" />
<img width="1484" height="1604" alt="image" src="https://github.com/user-attachments/assets/4ae3d80b-7d9e-47f0-928e-7e2f8ee01e1f" />


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

# XGBoost Model Experiment 



## Dataset

## Model Architecture

### 1. Data Preprocessing Pipeline


#### MissingMarkdownHandler

**პრობლემა:**
- დატასეტი შეიცავს 5 ფასდაკლების სვეტს, რომელიც სხვადასხვა ტიპის ფასდაკლებას არნიშნავენ
- ამ სვეტებში ძალიან ხშირია მისინგ ველიუები
- Missing value-ები აუცილებლად არ ნიშნავს, რომ მაშინ ფასდაკლება არ ყოფილა, შეიძლება
- ინფორმაცია უბრალოდ არ შეგროვებულა, ან ეს ფასდაკლების ტიპი ზოგ მაღაზიაში ან დეპარტამენტში არ ყოფილა და ა.შ.
ასეთ შემთხვევაში ხუთივესთვის შევქმენი ახალი სვეტები - `MarkDown1_was_missing` (1/0), ეს ინარჩუებს იმას, რომ
ინფორმაცია არ გვაქვს. შემდეგ მისინგ ველიუს მნიშვნელობას 0-ით ვცვლი.
 



#### MissingValueImputer

**Problem Context:**
- The dataset contains numerical columns with missing values: Temperature, Fuel_Price, CPI, Unemployment
- Test data shows significant missing values (e.g., CPI and Unemployment have only 76,902 non-null values out of 115,064 total records)
- These are time-series data where temporal continuity is important
- Different columns may have different missing value patterns and business implications
- დატასეტი შეიცავს რიცხვით სვეტებს ცარიელი მნიშვნელობებით: ტემპერატურა, საწვავის ფასი, მომხმარებელთა ფასების ინდექსი, უმუშევრობა
- time-series მონაცემებისთვის დროითი უწყვეტობა მნიშვნელოვანია

1. **Forward-Fill (ffill):**
   ```python
   X_copy[col] = X_copy[col].fillna(method='ffill')
   ```
   - ავსებს გამოტოვებულ მნიშვნელობებს ბოლო ცნობილი მნიშვნელობით
   - ვთვლით, რომ მნიშვნელობების დროის მცირე მონაკვეთში დრამატულად არ შეიცვლება, განსაკუთრებით CPI და უმუშევრობის შემთხვევაში 
  
 

2. **Backward-Fill (bfill):**
   ```python
   X_copy[col] = X_copy[col].fillna(method='bfill')
   ```
   - ავსებს გამოტოვებულ მნიშვნელობებს შემდეგი ცნობილი მნიშვნელობით
   - ვთვლით, რომ მნიშვნელობების დროის მცირე მონაკვეთში დრამატულად არ შეიცვლება, განსაკუთრებით CPI და უმუშევრობის შემთხვევაში 
  

3. **Mean Imputation (Fallback):**
   ```python
   if X_copy[col].isnull().any() and col in self.means:
       X_copy[col] = X_copy[col].fillna(self.means[col])
   ```
   - იყენებს სვეტის საშუალო მნიშვნელობას ბოლო გამოსავალის სახით.
   - ვიყენებ მხოლოდ მაშინ, თუ დროითი მეთოდები ვერ აგვარებს ყველა გამოტოვებულ მნიშვნელობას.


**ლოგიკა:**
- **ტემპერატურა**: მოკლე პერიოდებში ამინდი სტაბილურია
- **საწვავის ფასი**: სტანდარტულად ნელ-ნელა იცვლება
- **CPI**: Consumer Price Index დროთა განმავლობაში ნელ-ნელა იცვლება
- **უმუშევრობა**: ასევე



#### AdvancedDateFeatureExtractor

- გაყიდვები ავლენს ძლიერ დროით ტენდენციებს 
- სადღესასწაულო პერიოდებს არაპროპორციული გავლენა აქვთ გაყიდვების მაჩვენებლებზე
- ეკონომიკური ინდიკატორები (სმფ, უმუშევრობა) გარკვეულ გავლენას ახდენენ მომხმარებელთა ხარჯვის ქცევაზე
- მარტივი თარიღების მახასიათებლები ვერ ასახავს საცალო ვაჭრობის ნიმუშების რთულ ციკლურ ბუნებას
**Multi-Dimensional Feature Engineering:**

### 1. **დავაამატე დროითი ფიჩერები:**
```python
X_copy['Year'] = X_copy[self.date_column].dt.year
X_copy['Month'] = X_copy[self.date_column].dt.month
X_copy['Day'] = X_copy[self.date_column].dt.day
X_copy['DayOfWeek'] = X_copy[self.date_column].dt.dayofweek
X_copy['Week'] = X_copy[self.date_column].dt.isocalendar().week.astype(int)
X_copy['Quarter'] = X_copy[self.date_column].dt.quarter
X_copy['DayOfYear'] = X_copy[self.date_column].dt.dayofyear
```

### 2. **ციკლური ენქოუდინგი (Sin/Cos Transformations):**
```python
X_copy['Month_sin'] = np.sin(2 * np.pi * X_copy['Month'] / 12)
X_copy['Month_cos'] = np.cos(2 * np.pi * X_copy['Month'] / 12)
X_copy['Week_sin'] = np.sin(2 * np.pi * X_copy['Week'] / 52)
X_copy['Week_cos'] = np.cos(2 * np.pi * X_copy['Week'] / 52)
X_copy['DayOfWeek_sin'] = np.sin(2 * np.pi * X_copy['DayOfWeek'] / 7)
X_copy['DayOfWeek_cos'] = np.cos(2 * np.pi * X_copy['DayOfWeek'] / 7)
```
- ინარჩუნებს ციკლურ ბუნებას და კარგად იჭერს სეზონურ გადასვლებს

### 3. **სეზონური კლასიფიკაციები:**
```python
X_copy['Season'] = X_copy['Month'].map({
    12: 0, 1: 0, 2: 0,    # Winter
    3: 1, 4: 1, 5: 1,     # Spring
    6: 2, 7: 2, 8: 2,     # Summer
    9: 3, 10: 3, 11: 3    # Fall
})
```
- სეზონები დავამატე თვეების მიხედვით, მცირედი გაუმჯობესებისთვის

### 4. **Calendar Event Flags:**
```python
X_copy['IsWeekend'] = (X_copy['DayOfWeek'] >= 5).astype(int)
X_copy['IsMonthEnd'] = (X_copy[self.date_column].dt.is_month_end).astype(int)
X_copy['IsMonthStart'] = (X_copy[self.date_column].dt.is_month_start).astype(int)
```

### 5. **არდადეგების პერიოდი:**
```python
def _is_holiday_period(self, date):
    month, day = date.month, date.day
    if month == 11 and day >= 22:  # Thanksgiving week
        return 1
    elif month == 12:              # Christmas season
        return 1
    elif month == 1 and day <= 7:  # New Year
        return 1
    elif month == 9 and day <= 7:  # Labor Day
        return 1
    elif month == 5 and day >= 25: # Memorial Day
        return 1
    else:
        return 0
```
- უფრო ბუნებრივია, რომ კონკრეტული ერთი დღესასწაულის დღის მაგივრად ზოგადად მაგ დღესასწაულამდე პერიოდი განვიხილოთ, როცა საქმე გაყიდვებს ეხება

### 6. **Economic Feature Engineering:**
```python
# MarkDown Intensity
X_copy['Total_MarkDown'] = X_copy[markdown_cols].sum(axis=1)
X_copy['MarkDown_Intensity'] = X_copy['Total_MarkDown'] / (X_copy['Total_MarkDown'].mean() + 1e-8)
X_copy['HasMarkDown'] = (X_copy['Total_MarkDown'] > 0).astype(int)

# Economic Indicators
X_copy['Fuel_CPI_Ratio'] = X_copy['Fuel_Price'] / (X_copy['CPI'] + 1e-8)
X_copy['Economic_Index'] = (X_copy['CPI'] * 0.4 + (100 - X_copy['Unemployment']) * 0.6) / 100
```
- ეკონომიკურმა ფიჩერებმა მინიმალური კორელაცია აჩვენეს სეილებზე და შევეცადე ოპტიმალურად გამომეყენებინა

საბოლოო ჯამში გამოვიყენე MissingMarkdownHandler, MissingValueImputer, AdvancedDateFeatureExtractor, SmartLabelEncoder. 
არ გამოვიყენე კოლელაციის მატრიცა, ამ შემტხვევაში, დატაში იქნებოდა მაღალ-კორელაციაში მყოფი სვეტები, რომლებიც საჭიროა და დამახასიათებელია
Time-series პრედიქშენისთვის. თავიდან გამოვიყენე გრიდ სერჩი პარამეტრებისთვის, დავტოვე რამდენიმე საუკეთესო ვარიანტი და
ბოლოს მაგეებზე ვქენი კიდე ერთხელ.

### 3. XGBoost Model 

```python
xgb_base_params = {
    'n_estimators': 200,               # ბუსტინგის რაუნდების/ხეების რაოდენობა
    'subsample': 0.8,                  # ყველა ხე გამოიყენებს ტრეინის 80 პროცენტს, ოვერფიტის საწინააღმდეგოდ
    'colsample_bytree': 0.8,           # ყველა ხე გამოიყენებს ფიჩერების 80 პროცენტს
    'min_child_weight': 1,             # 	წონების მინიმალური ჯამი, რომელიც საჭიროა შვილობილ ნოუდში.
    'eval_metric': 'mae',              # Mean Absolute Error
    'early_stopping_rounds': 50        # 50 რაუნდის შემდეგ თუარ მოხდა გაუმჯობესება, შეწყვეტს
}
```

#### Grid Search
- **max_depth**: [6, 8] - რაც უფრო ღრმაა ხე მით უფრო კომპლექსურია მოდელი, მაგრამ უფრო მიდრეკილია overfit-ისკენ.
- **learning_rate**: [0.05, 0.1] - რამდენად სწრაფად სწავლობს ჩვენი მოდელი შეცდომაზე. 

## Model Training 

### 1. Time Series Split
- **Training**: 2010-02-05 - 2012-06-30
- **Validation**: 2012-07-01 - 2012-10-26

### 2. Weighted Loss Function
- **Holiday**: 5x 
- **Regular**: 1x 

### 3. Validation
- TimeSeriesSplit დროზე დამოკიდებული ვალიდაციისთვის და სწორი პროგნოზირებისთვის

## Results

### Model Performance Comparison

| Model Configuration | Learning Rate | Max Depth |
|-------------------|---------------|-----------|
| XGBoost_0.05_6    | 0.05          | 6         |
| XGBoost_0.05_8    | 0.05          | 8         |
| XGBoost_0.1_6     | 0.1           | 6         | 
| **XGBoost_0.1_8** | **0.1**       | **8**     |

### საუკეთესო მოდელი
- **Best Validation WMAE**: 2586.06
- **Best Parameters**: learning_rate=0.1, max_depth=8
- **Training WMAE**: 2313.77 (ოვერფიტისკენ მიდის)


### Feature Importance 

1. **Weekly_Sales_lag_1** (34.86%) - წინა კვირის სეილები
2. **Weekly_Sales_lag_4** (33.56%) - 4 კვირის სეილები
3. **Weekly_Sales_lag_52** (8.38%) - წლის
4. **IsHoliday** (2.65%) - დღესასწაული
5. **Week** (2.31%) - კვირა


# LightGBM Model Experiment 

## განსხვავებები XGBoost Experiment-ისგან

### 1. Model Architecture


**Base Parameters:**
```python
lgb_base_params = {
    'objective': 'regression',             
    'metric': 'mae',                        # Mean Absolute Error
    'n_estimators': 2000,                   # ბუსტინგის რაუნდების რაოდენობა
    'learning_rate': 0.02,                  # ბეევრად დაბალი დასწავლის დონე
    'feature_fraction': 0.8,                # იგივე colsample_bytree
    'bagging_fraction': 0.8,                # იგივე subsample
    'bagging_freq': 1,                      # ბეგინგის სიხშირე
    'boosting_type': 'gbdt',                # Gradient boosting decision tree
    'max_depth': -1,                        # არ აქვს ლიმიტი
}
```


#### Hyperparameter Grid Search
- **num_leaves**: [32, 64, 128] (LightGBM-ისთვის დამახასიათებლი პარამეტრი)
- თუ XGBoost მაქსმალურ სიღრმეს იყენებს ხის კომპლექსურობის გასაკონტროლებლად, LightGBM იყენებს ფოთლების რაოდენობას

### 2. Model Training Strategy

**იგივენაირად:**
- Time Series Split (2010-02-05 to 2012-06-30 - training, 2012-07-01 to 2012-10-26 - validation)
- Weighted Loss Function
- TimeSeriesSplit validation

**LightGBM-ის ოპტიმიზაციები:**
- **Leaf-wise tree growth**: უფრო ეფექტური ვიდრე დონეებად ზრდა
- **Histogram-based algorithm**: სწრაფი ტრენინგი დიდ დატასეტებზე

### 3. შედეგები


| Model Configuration | Num Leaves | Learning Rate | Validation WMAE |
|-------------------|------------|---------------|-----------------|
| LightGBM_32       | 32         | 0.02          | 2034.72         |
| LightGBM_64       | 64         | 0.02          | 1814.54         |
| **LightGBM_128**  | **128**    | **0.02**      | **1797.79**     |

#### Best Model Performance
- **Best Validation WMAE**: 1797.79
- **Best Parameters**: num_leaves=128, learning_rate=0.02, n_estimators=2000

# Prophet Model Experiment 

## Overview

This repository contains a Prophet-based time series forecasting experiment for Walmart store sales. Prophet is a specialized time series forecasting tool developed by Facebook (Meta) that excels at handling seasonal patterns, holiday effects, and trend changes. Unlike XGBoost and LightGBM which are general-purpose machine learning algorithms, Prophet is specifically designed for time series forecasting with built-in capabilities for seasonality and holiday modeling.
Prophet არის Facebook-ის (Meta) მიერ შემუშავებული სპეციალიზებული დროითი სერიების პროგნოზირების ინსტრუმენტი, რომელიც უმკლავდება სეზონურ პატერნებს, დღესასწაულების ეფექტებს და ტრენდების ცვლილებებს. XGBoost-ისა და LightGBM-ისგან განსხვავებით, რომლებიც ზოგადი დანიშნულების კლასიკური მლ ალგორითმებია, Prophet სპეციალურად შექმნილია დროითი სერიების პროგნოზირებისთვის, სეზონურობისა და დღესასწაულების მოდელირების ჩაშენებული შესაძლებლობებით.


## როგორ მუშაობს Prophet

### 1. Prophet's Mathematical Foundation

სამი მთავარი კომპონენტი:

```python
y(t) = g(t) + s(t) + h(t) + ε(t)
```

სადაც:
- **g(t)**: ტრენდი (linear ან logistic ზრდა)
- **s(t)**: სეზონური კომპონენტი 
- **h(t)**: დღესასაულები (holiday effects)
- **ε(t)**: ცდომილება
- 
### 2.

#### Trend Component (g(t))
- ავტომატურად ხვდება როცა ტრენდი მიმართულებას ცვლის
- მუშაობს წრფივ და არაწრფივ ტრენდებზე

#### Seasonal Component (s(t))
- იყენებს Fourier სერიებს პერიოდული პატერნების მოდელირებისთვის
- სხვადასხა სიხშირის სეზონურობას იჭერს - წელი, სეზონი, თვე, კვირა

#### Holiday Component (h(t))
- იცის ცნობილი დღესასწაულების დღეები
- ითვალისწინებს ამ დღესასწაულების გარშემო პერიოდს

### 3. Prophet Model 

#### Base Parameters
```python
model = Prophet(
    holidays=walmart_holidays,    
    yearly_seasonality=True,          
    weekly_seasonality=True,     
    daily_seasonality=False,    
    seasonality_mode='multiplicative'  
)
```

#### Key Configuration Differences from Other Models:
- **No hyperparameter tuning**: default-ებით კარგად მუშაობს
- **Seasonality modes**: 'additive' vs 'multiplicative' (ავირჩიეთ multiplicative გაყიდვებისთვის)

თავიდან, როცა რეგრესორებს არ ვიყენებდი პრეპროცესინგის ნაწილი საერთოდ არ მქონდა, რადგან პროფეტი მისინგ მნიშვნელობებს თვითონ ხედავს და თან სეზონურობასაც თვითონ იჭერს, ამიტომ არ დამჭირვებია დამატებითი დროზე დამოკიდებული ფიჩერების შექმნა, უბრალოდ გადავეცი დღესასწაულების კალენდარი. 
### 4. Data Requirements and Format

#### Prophet-ისთვის დამახასიათებელიდატას ფორმატი
```python
# Prophet requires specific column names
prophet_data = df.rename(columns={
    'Date': 'ds',           # Date column must be named 'ds'
    'Weekly_Sales': 'y'     # Target column must be named 'y'
})
```

#### Required Columns:
- **ds**: Date column (datetime format)
- **y**: Target variable (numeric)
- **Additional regressors**: სხვა რეგრესორები

### 5. Multi-Model Approach

#### Store-Department Specific Models
XGBoost-ისგან და LightGBM-ისგან განსხვავებით, Prophet ერთ მოდელს არ იყენებს მთელ დატაზე, ის ყოფს მოდელებს ყველა მაღაზია-დეპარტამენტი კომბინაციისთვის:

```python
# Train individual models for each store-department combination
for store, dept in combinations:
    train_data = data[(data['Store'] == store) & (data['Dept'] == dept)]
    
    model = Prophet(
        holidays=walmart_holidays,
        yearly_seasonality=True,
        weekly_seasonality=True,
        daily_seasonality=False,
        seasonality_mode='multiplicative'
    )
    
    # Add external regressors
    for regressor in extra_regressors:
        model.add_regressor(regressor)
    
    model.fit(train_data)
    models[(store, dept)] = model
```

#### Fallback Strategy
გავტესტე ეს მიდგომაც, რათა მაქსიმალურად გამომეყენებინა დატა,იმ შემთხვევაში თუ მცირე მონაცემები მნიშვნელოვანიიქნებოდა საბოლოო შედეგისთვის, თუმცა ტრენინგის დროს ვნახე, რომ 
თვითონს ეს სტრატეგიაც ისეთ ადეკვატურ შედეგს არ მაძლევდა, როგორსაც ველოდი (დიდი შეცდომა ჯდებოდა) და შემდეგ მის გარეშე რომ დავატრენინგე დიდი გავლენა მანდაც ვერ დავინახე. ბოლოს მას შემდეგ რაც ფასადკლებების სვეტები დავამატე რეგრესორად პრეპროცესინგის ნალების ჰენდლინგ ნაწილი გავატარე დატას, რადგან ფასდაკლებების ვეტებს განსხვავებული მიხედვა ჭირდებოდათ.
### 6. გარე რეგრესორები

```python
# Add external regressors to the model
extra_regressors = [
    'Temperature', 'Fuel_Price', 'CPI', 'Unemployment',
    'MarkDown1', 'MarkDown2', 'MarkDown3', 'MarkDown4', 'MarkDown5',
    'IsHoliday', 'Size', 'Type_encoded'
]

for regressor in extra_regressors:
    if regressor in prophet_train.columns:
        model.add_regressor(regressor)
```


### 7. Holiday Modeling

#### Custom კალენდარი
```python
# Define Walmart-specific holidays
walmart_holidays = pd.DataFrame({
    'holiday': 'Super Bowl',
    'ds': pd.to_datetime(['2010-02-07', '2011-02-06', '2012-02-05']),
    'lower_window': -1,
    'upper_window': 1
})
```

#### Holiday Effects:
- **Pre-Holiday**: გაყიდვები იზრდება
- **Holiday Day**: გაყიდვები პიკშია
- **Post-Holiday**: გაყიდვები მცირდება
- **Window Effects**: ამ ყველაფერს მოდელი იჭერს

### 8. Model Training Strategy

#### Same as Other Models:
- **Time Series Split**: 2010-02-05 to 2012-06-30 for training, 2012-07-01 to 2012-10-26 for validation
- **Weighted Loss Function**: 5x weight for holiday periods

#### Prophet-Specific Approach:
- **Individual Models**: სხვადასხვა მოდელი ყველა კომბინაციისთვის
- **Automatic Seasonality**

### 9. Results

#### Model Performance
- **Best Validation WMAE**: 2878.93
- **Model Count**: 3,371
- **Coverage**: 97.4% of Store-Dept combinations covered


#### შესრულების მახასიათებლები:
- **ძლიერი მხარეები**: შესანიშნავია სეზონური პატერნების და დღესასწაულების ეფექტების აღსაქმელად
- **შეზღუდვები**: ნაკლებად მოქნილია რთული ფუნქციების ერთმანეთთან ურთიერთქმედების დროს
- **მასშტაბირება**: მოითხოვს ბევრი მოდელის ტრენინგს და ბევრ დროს


#### Prophet-ის უნიკალური უპირატესობები:
- სეზონური პატერნების ავტომატურად ამოცნობა და მოდელირება
- ჩაშენებული დღესასწაულის ეფექტის მოდელირება
- ტენდენციის ცვლილებების მარტივად იდენტიფიცირება
- ტრენდების, სეზონურობის და დღესასწაულების ეფექტების მკაფიო დაშლა

# Deep Learning

## N-BEATS

• **მოდელის სპეციფიკა:** N-BEATS მოდელი თითოეული (store, dept) წყვილისთვის ინდივიდუალურად იქმნება, რადგან თითოეულს უნიკალური გაყიდვების ისტორიული პატერნი გააჩნია. ეს უზრუნველყოფს მაღალ სიზუსტეს თითოეული დროითი სერიისთვის.

• **მონაცემთა დამუშავება:** N-BEATS არქიტექტურა არ საჭიროებს კომპლექსურ feature engineering-ს. მოდელი მუშაობს პირდაპირ `weekly_sales`-ის ისტორიულ მონაცემებზე. მთავარი მოთხოვნაა მონაცემების ქრონოლოგიური სიზუსტე, რისთვისაც ვიყენებთ **ტემპორალურ გაყოფას (Temporal Split)**.

• **მონაცემების გაყოფა:** test/validation - 70/30 (ქრონოლოგიურად).

### არქიტექტურა და პარამეტრები

N-BEATS-ის არქიტექტურა დაფუძნებულია სტეკების (stacks) იდეაზე, სადაც თითოეული სტეკი სწავლობს მონაცემების კონკრეტულ კომპონენტს (ტრენდი, სეზონურობა).

| პარამეტრი | მნიშვნელობა | აღწერა |
|---|---|---|
| **`stack_types`** | `['trend', 'seasonality', 'generic']` | მოდელი შედგება 3 ძირითადი სტეკისგან: ტრენდის, სეზონურობის და ზოგადი პატერნების ამოსაცნობად. |
| **`input_size` (Backcast)** | 24 | მოდელი იყენებს ბოლო 24 კვირის მონაცემს მომავლის პროგნოზირებისთვის. |
| **`h` (Forecast)** | 4 | მოდელის მიზანია მომდევნო 4 კვირის გაყიდვების პროგნოზირება. |
| **`batch_size`** | 128 | ერთ ჯერზე მუშავდება 128 დროითი სერია, რაც აჩქარებს ტრენინგს და ასტაბილურებს გრადიენტებს. |
| **`early_stop_patience`** | 5 ეპოქა | ტრენინგი ავტომატურად ჩერდება, თუ ვალიდაციის ცდომილება 5 ეპოქის განმავლობაში არ უმჯობესდება. |
| **`scaler_type`** | `StandardScaler` / `RobustScaler` | მონაცემების სკალირება ხდება ნორმალიზაციისთვის. |
| **`learning_rate`** | 0.001 | სწავლების სიჩქარე, რომელიც კონტროლდება `ReduceLROnPlateau` სქემით. |
---

### Hyperparameter Tuning და შედეგები

ჩატარდა ჰიპერპარამეტრების ოპტიმიზაცია საუკეთესო შედეგის მისაღებად:

• **Input Size-ის გაზრდა:** გავზარდეთ `input_size`, რათა მოდელმა მეტი ისტორიული კონტექსტი გაითვალისწინოს.

• **Batch Size-ის ოპტიმიზაცია:** შევარჩიეთ ოპტიმალური `batch_size` სტაბილური და სწრაფი სწავლისთვის.

• **Scaler-ის შერჩევა:** `weekly_sales` მონაცემები შეიცავს ბევრ outlier-ს. `RobustScaler`-მა აჩვენა საუკეთესო შედეგი, რადგან ის ნაკლებად მგრძნობიარეა ექსტრემალური მნიშვნელობების მიმართ, `StandardScaler`-თან შედარებით.

#### საბოლოო შედეგი:

**Validation WMAE: 1648.15**

---

### შედეგების ვიზუალიზაცია

ქვემოთ მოცემულია მოდელის მუშაობის ამსახველი გრაფიკები, რომლებიც დაგენერირდა `Correct_N_BEATS.ipynb` ფაილში.

**1. ტრენინგის პროგრესი (Train vs Validation Loss)**
*გრაფიკი გვიჩვენებს, თუ როგორ მცირდებოდა ცდომილება ტრენინგის პროცესში, რაც მიუთითებს წარმატებულ სწავლაზე.*

**2. პროგნოზის შედარება რეალურ მონაცემებთან (Sample Forecast)**
*აქ ჩანს, თუ რამდენად ახლოსაა მოდელის პროგნოზი რეალურ გაყიდვებთან კონკრეტული მაგალითისთვის.*

**3. პროგნოზებისა და რეალური გაყიდვების Scatter Plot**
*იდეალურ შემთხვევაში, წერტილები უნდა განლაგდეს დიაგონალურ ხაზზე, რაც მაღალ სიზუსტეზე მიუთითებს.*
<img width="551" height="177" alt="Screenshot 2025-08-01 at 3 06 15 AM" src="https://github.com/user-attachments/assets/7d8ff74d-aedd-4d72-85c6-1a9ac08c92e4" />

---

## DLinear (Multivariate)

• **მოდელის სპეციფიკა:** გამოყენებული DLinear მოდელი წარმოადგენს სტანდარტული არქიტექტურის გაძლიერებულ ვერსიას. მისი მთავარი იდეაა დროითი სერიის დაშლა ორ კომპონენტად: **ტრენდად** და **სეზონურობად**. თითოეული კომპონენტისთვის მოდელი სწავლობს ცალკე წრფივ ფენას, რაც საშუალებას აძლევს უკეთ გააანალიზოს მონაცემების სტრუქტურა. N-BEATS-ის მსგავსად, მოდელი ინდივიდუალურად იქმნება თითოეული (store, dept) წყვილისთვის.

• **მონაცემთა დამუშავება:** N-BEATS-ისგან განსხვავებით, ეს DLinear მოდელი აქტიურად იყენებს **გარე მახასიათებლებს (external features)**, რათა გააუმჯობესოს პროგნოზის სიზუსტე. გამოყენებული მახასიათებლებია:
  - **დროითი მახასიათებლები:** `IsHoliday`, `Temperature`, `Fuel_Price`.
  - **ფასდაკლებების მონაცემები:** `MarkDown1`-`MarkDown5`.
  - **ისტორიული გაყიდვები:** **Lag features** (წინა კვირების გაყიდვები), რაც მოდელს ეხმარება წარსული დინამიკის გათვალისწინებაში.
მონაცემები სკალირდება `StandardScaler`-ით.

• **მონაცემების გაყოფა:** train/validation - 75/25 (ქრონოლოგიურად).

### არქიტექტურა და პარამეტრები

| პარამეტრი | მნიშვნელობა | აღწერა |
|---|---|---|
| **`SEQ_LEN`** (Lookback) | 32 | მოდელი იყენებს ბოლო 32 კვირის მონაცემს პროგნოზისთვის. |
| **`PRED_LEN`** (Forecast) | 1 | მოდელის მიზანია მომდევნო 1 კვირის გაყიდვების პროგნოზირება. |
| **`BATCH_SIZE`** | 8 | მცირე ბაჩი გამოიყენება უკეთესი განზოგადებისთვის. |
| **`LEARNING_RATE`** | 0.001 | სწავლების სიჩქარე, რომელიც კონტროლდება `CosineAnnealing` სქემით. |
| **`EPOCHS`** | 200 | ტრენინგის ეპოქების მაქსიმალური რაოდენობა. |
| **`DROPOUT`** | 0.1 | რეგულარიზაციის მეთოდი გადამეცადების (overfitting) შესამცირებლად. |
| **`KERNEL_SIZE`** | 5 | მოძრავი საშუალოს ბირთვის ზომა ტრენდის კომპონენტის გამოსაყოფად. |
| **`LOSS_FUNCTION`** | `HuberLoss` | ცდომილების ფუნქცია, რომელიც ნაკლებად მგრძნობიარეა ექსტრემალური მნიშვნელობების მიმართ. |

### მოდელის შეფასება

• **ჰიბრიდული მიდგომა:** DLinear-ის ეს ვერსია აერთიანებს დროითი სერიების კლასიკურ დაშლას (decomposition) და ღრმა სწავლების უნარს, გამოიყენოს გარე ფაქტორები.

• **შედეგი:** მოდელი ფასდება ტოპ 20 `(store, dept)` წყვილზე, რომლებსაც საკმარისი მონაცემები აქვთ. საბოლოო მეტრიკა, **საშუალო WMAE**, გამოითვლება ამ წყვილებზე მიღებული შედეგების საფუძველზე. ეს მიდგომა ამოწმებს, რამდენად შეუძლია გარე ფაქტორების დამატებას გააუმჯობესოს პროგნოზი სუფთა დროითი მოდელთან (N-BEATS) შედარებით. მიუხედავად იმისა, რომ DLinear უფრო მარტივია, მისი მთავარი ძალა გარე კონტექსტის გათვალისწინებაშია.

• **ვიზუალიზაცია:** თანდართული სურათები აჩვენებს DLinear მოდელის ტრენინგის პროცესს და პროგნოზის შედეგს. ტრენინგის გრაფიკი გვიჩვენებს, რომ მოდელი წარმატებით სწავლობს (ცდომილება მცირდება), ხოლო პროგნოზის გრაფიკზე ჩანს, რომ მოდელი იჭერს გაყიდვების ზოგად ტრენდს.
<img width="855" height="547" alt="image" src="https://github.com/user-attachments/assets/e6ba5d0c-5026-434b-9e43-70ca29fd44b2" />
<img width="1032" height="547" alt="image" src="https://github.com/user-attachments/assets/05dae219-56b2-4976-ba52-f8820591fc41" />
**Average WMAE: 4100.47**

### რატომ აჩვენა N-BEATS-მა უკეთესი შედეგი?

N-BEATS-მა (WMAE: 1648.15) მნიშვნელოვნად აჯობა DLinear-ს (WMAE: 4100.47) ორი მთავარი მიზეზის გამო:
1.  **არქიტექტურა:** N-BEATS-ის ღრმა, სტეკირებული სტრუქტურა (`trend`, `seasonality` stacks) ბევრად უკეთ უმკლავდება რთულ დროით პატერნებს, ვიდრე DLinear-ის მარტივი წრფივი ფენები.
2.  **Feature Engineering:** N-BEATS-ი ავტომატურად სწავლობს საჭირო მახასიათებლებს პირდაპირ გაყიდვების ისტორიიდან. DLinear-ის შემთხვევაში, დამატებულმა გარე ფაქტორებმა (`Fuel_Price`, `MarkDowns` და ა.შ.) სავარაუდოდ არეულობა გამოიწვია და მოდელის სიზუსტე შეამცირა, იმის ნაცვლად რომ გაეუმჯობესებინა.

მოკლედ, N-BEATS-ის სპეციალიზებული არქიტექტურა უფრო ეფექტური აღმოჩნდა ამ ამოცანისთვის, რადგან ის არ იყო დამოკიდებული პოტენციურად გარე მახასიათებლებზე.
## Time Series Models

### ARIMA

• **მოდელის სპეციფიკა:** ARIMA (Autoregressive Integrated Moving Average) არის კლასიკური სტატისტიკური მოდელი, რომელიც გამოიყენება დროითი სერიების გასაანალიზებლად და პროგნოზირებისთვის. Deep Learning მოდელების მსგავსად, ARIMA მოდელიც ინდივიდუალურად იქმნება თითოეული `(store, dept)` წყვილისთვის, რათა ზუსტად გაითვალისწინოს მათი უნიკალური ისტორიული მონაცემები.

• **მონაცემთა დამუშავება:**
  - **დასრულებული დროითი სერია:** თითოეული წყვილისთვის იქმნება სრული, უწყვეტი ყოველკვირიანი დროითი სერია. გამოტოვებული თარიღები ივსება ინტერპოლაციით.
  - **ხმაურის შემცირება:** მონაცემები გადის გასწორებას (smoothing) მოძრავი საშუალოს (rolling mean) გამოყენებით, რათა შემცირდეს შემთხვევითი ხმაური.
  - **სტაციონარულობის შემოწმება:** მოდელის გამოყენებამდე, დროითი სერია მოწმდება სტაციონარულობაზე გაძლიერებული დიკი-ფულერის (ADF) ტესტით.

• **მონაცემების გაყოფა:** train/validation - 80/20 (ქრონოლოგიურად).

**ტერმინების განმარტება:**
*   **ინტერპოლაცია (Interpolation):** გამოტოვებული მონაცემების შევსების მეთოდი. მაგალითად, ორ კვირას შორის ცარიელი მონაცემის შევსება არსებულ წერტილებზე დაყრდნობით.
*   **ხმაური (Noise):** მონაცემებში არსებული შემთხვევითი, უმნიშვნელო რყევები, რომლებიც არ არის ძირითადი ტრენდის ან სეზონურობის ნაწილი.




### არქიტექტურა და პარამეტრები

| პარამეტრი | მნიშვნელობა | აღწერა |
|---|---|---|
| **`(p,d,q)`** (Order) | Auto-selected | მოდელის რიგი (p: ავტორეგრესია, d: ინტეგრირება, q: მოძრავი საშუალო) ავტომატურად შეირჩევა თითოეული დროითი სერიისთვის **Grid Search**-ის მეშვეობით, საუკეთესო **AIC** (Akaike Information Criterion) მნიშვნელობის მისაღებად. |
| **Ensemble Forecasting** | 3 მოდელი | საბოლოო პროგნოზი მიიღება 3 განსხვავებული ARIMA მოდელის შედეგის გასაშუალოებით, რაც ზრდის პროგნოზის სტაბილურობას. |
| **ტრენინგი** | ტოპ 50 წყვილი | მოდელი იქმნება და ფასდება ტოპ 50 `(store, dept)` წყვილზე, რომლებსაც ყველაზე მეტი მონაცემი აქვთ. |

### მოდელის შეფასება

• **კლასიკური მიდგომა:** ARIMA წარმოადგენს კლასიკურ, სტატისტიკაზე დაფუძნებულ მეთოდს, რომელიც ეფექტურია, როდესაც დროით სერიას აქვს მკაფიო სტრუქტურა და არ არის დამოკიდებული რთულ გარე ფაქტორებზე.

• **ინტერპრეტაცია:** Deep Learning მოდელებისგან განსხვავებით, ARIMA-ს პარამეტრები და შედეგები ადვილად ინტერპრეტირებადია.

• **ვიზუალიზაცია:** თანდართული სურათი გვიჩვენებს ARIMA-ს პროგნოზის მაგალითს (Store 45, Dept 97). ჩანს, რომ მოდელი იჭერს გაყიდვების ზოგად დონეს, მაგრამ უჭირს კონკრეტული ყოველკვირეული რყევების ზუსტად პროგნოზირება.
<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/4bd76872-72d5-471b-863f-0869c54dafb9" />

**Average WMAE: 2353.48**
### SARIMAX

• **მოდელის სპეციფიკა:** SARIMAX არის ARIMA მოდელის გაფართოება, რომელიც დამატებით ითვალისწინებს **სეზონურობას** და **გარე ფაქტორებს (Exogenous Variables)**. ეს მას უფრო მძლავრს ხდის რთული დროითი სერიებისთვის.

• **მონაცემთა დამუშავება:**
  - **გარე ფაქტორები:** მოდელი იყენებს დამატებით მახასიათებლებს, როგორიცაა `Temperature`, `Fuel_Price`, `CPI`, და `Unemployment`.
  - **მონაცემების შევსება:** გამოტოვებული მნიშვნელობები ივსება წინა (`ffill`) და მომდევნო (`bfill`) მნიშვნელობებით.

• **მონაცემების გაყოფა:** train/validation - 80/20 (ქრონოლოგიურად).

### არქიტექტურა და პარამეტრები

| პარამეტრი | მნიშვნელობა | აღწერა |
|---|---|---|
| **`(p,d,q)`** (Non-seasonal) | Auto-selected | არასეზონური პარამეტრები, რომლებიც ავტომატურად შეირჩევა **Grid Search**-ით. |
| **`(P,D,Q,s)`** (Seasonal) | Auto-selected | სეზონური პარამეტრები, სადაც `s=52` (წლიური სეზონურობა), ასევე შეირჩევა **Grid Search**-ით. |
| **ტრენინგი** | ტოპ 20 წყვილი | მოდელი იქმნება და ფასდება ტოპ 20 `(store, dept)` წყვილზე, რომლებსაც ყველაზე მაღალი ჯამური გაყიდვები აქვთ. |

### მოდელის შეფასება

• **სირთულე და სიზუსტე:** SARIMAX ბევრად ძლიერია ვიდრე ARIMA, რადგან მას შეუძლია სეზონური პატერნების და გარე ფაქტორების გათვალისწინება. თუმცა, ამ სირთულის გამო, მისი ტრენინგი გაცილებით მეტ დროს მოითხოვს.

**Average WMAE: 18046.86**

### ARIMA vs. SARIMA vs. SARIMAX

*   **ARIMA:** საბაზისო მოდელი, რომელიც ითვალისწინებს მხოლოდ დროითი სერიის შიდა კავშირებს (ავტორეგრესია, ინტეგრირება, მოძრავი საშუალო).
*   **SARIMA:** ARIMA-ს ემატება **სეზონურობის კომპონენტი (S)**, რაც საშუალებას აძლევს მოდელს გაითვალისწინოს განმეორებადი ციკლები (მაგ., წლიური).
*   **SARIMAX:** SARIMA-ს ემატება **გარე ფაქტორები (X)**, რაც მოდელს საშუალებას აძლევს, პროგნოზირებისას დაეყრდნოს დამატებით ინფორმაციას (მაგ., ტემპერატურა, საწვავის ფასი).
## მოდელების შედარება: Deep Learning vs. Classical ML vs. Time Series

| თვისება | Deep Learning (N-BEATS, DLinear) | კლასიკური ML (XGBoost, LightGBM) | Time Series მოდელები (ARIMA, SARIMA) |
|---|---|---|---|
| **მონაცემთა ტიპი** | მუშაობს როგორც დროით, ისე ზოგად ტაბულურ მონაცემებზე. | ძირითადად ტაბულურ მონაცემებზე; დროითი ასპექტი მოითხოვს ხელით დამუშავებას. | მხოლოდ დროით სერიებზე (Univariate/Multivariate). |
| **Feature Engineering** | **ავტომატური:** თავად სწავლობს მახასიათებლებს მონაცემებიდან. | **ხელით:** საჭიროებს მახასიათებლების შექმნას (მაგ. lags, moving averages). | **არ სჭირდება:** მუშაობს პირდაპირ დროითი სერიის სტატისტიკურ თვისებებზე (p, d, q). |
| **მონაცემების გაყოფა** | **ტემპორალური (Temporal Split):** ინარჩუნებს დროით თანმიმდევრობას (მაგ. 70%-30%). | **შემთხვევითი (Random Split):** ხშირად გამოიყენება, თუ დროითი ასპექტი იგნორირებულია. | **ტემპორალური:** ყოველთვის გამოიყენება დროითი თანმიმდევრობის შესანარჩუნებლად. |
| **არაწრფივობა** | **მაღალი:** ღრმა ფენების წყალობით, შეუძლიათ რთული, არაწრფივი პატერნების შესწავლა. | **შეზღუდული:** ხეზე დაფუძნებული მოდელები მონაცემებს მარტივი წესებით ყოფენ. | **ძირითადად წრფივი:** ARIMA ეფუძნება წრფივ კავშირებს. |
| **გარე ფაქტორები** | **მარტივი ინტეგრაცია:** ადვილად ითვალისწინებს დამატებით მახასიათებლებს (features). | **მარტივი ინტეგრაცია:** ითვალისწინებს დამატებით მახასიათებლებს. | **შეზღუდული:** SARIMAX-ს შეუძლია, მაგრამ ინტეგრაცია უფრო რთულია. |
| **ინტერპრეტაცია** | **რთული ("შავი ყუთი"):** რთულია იმის გაგება, თუ როგორ იღებს გადაწყვეტილებას. | **შედარებით მარტივი:** ხეების ლოგიკა ან მახასიათებლების მნიშვნელოვნება გასაგებია. | **ძალიან მარტივი:** პარამეტრებს (p, d, q) და კომპონენტებს (ტრენდი, სეზონი) აქვთ მკაფიო სტატისტიკური ახსნა. |

მოკლედ, **Deep Learning** მოდელები გამოირჩევიან მოქნილობითა და რთული პატერნების ავტომატურად შესწავლის უნარით. **კლასიკური ML** მოდელები ეფექტურია ტაბულურ მონაცემებზე და მოითხოვს მეტ ხელით ჩარევას. **Time Series** მოდელები კი სპეციალიზებული და მაღალ ინტერპრეტირებადია, თუმცა ნაკლებად მოქნილი.

