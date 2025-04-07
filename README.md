Here's a clean, professional-style **README-style summary** for your dataset cleaning and preprocessing code (based on your provided data — like the Netflix-style dataset):

---

## 🎬 Internship - Day 1  
### 📊 Title: Netflix Shows Dataset Cleaning & Preprocessing  
**📁 Dataset:** A sample of movies and TV shows on Netflix  

---

### 📥 Dataset Source  
The dataset was provided as part of an internship exercise. It contains metadata about Netflix content such as movies and TV shows — including attributes like type, title, director, cast, country, date added, rating, duration, and description.

---

### 🧹 Task Objectives  
The aim of this task was to **clean and prepare the dataset for analysis**, addressing the following issues:

- Missing values  
- Duplicate records  
- Inconsistent formatting in text  
- Incorrect or inconsistent date formats  
- Unclean or inconsistent column names  
- Incorrect data types for numeric/date fields  

---

### 🔧 Steps Performed

#### 1. 📥 Loaded the Dataset  
The dataset was loaded using `pandas.read_csv()`:
```python
df = pd.read_csv("raw_dataset.csv")
```

---

#### 2. 🔍 Initial Inspection  
Used `df.info()` and `df.head()` to explore the dataset and understand the structure.  

- ✅ Total rows: *10*  
- ✅ Total columns: *12*

---

#### 3. 🚫 Missing Values Handled  
Checked missing values using `.isnull().sum()` and handled as follows:

- `director`: Missing values filled with `"Unknown"`  
- `cast`: Filled missing entries with `"Not Available"`  
- `country`: Missing values replaced with `"Unknown"`  

```python
df['director'] = df['director'].fillna('Unknown')
df['cast'] = df['cast'].fillna('Not Available')
df['country'] = df['country'].fillna('Unknown')
```

---

#### 4. 🔁 Duplicate Rows Removed  
```python
df.drop_duplicates(inplace=True)
```
✅ No duplicate rows found after check.

---

#### 5. ✨ Standardized Text Columns  
Standardized and cleaned text fields to remove inconsistencies:
```python
df['type'] = df['type'].str.strip().str.title()
df['country'] = df['country'].str.strip().str.title()
df['rating'] = df['rating'].str.strip().str.upper()
```

---

#### 6. 🕒 Converted Date Format  
Converted the `date_added` column to `datetime` format for accurate analysis:
```python
df['date_added'] = pd.to_datetime(df['date_added'], dayfirst=True, errors='coerce')
```

---

#### 7. 🏷️ Renamed Columns  
Renamed columns to lowercase with underscores for readability:
```python
df.columns = df.columns.str.strip().str.lower().str.replace(" ", "_")
```

---

#### 8. 🔢 Fixed Data Types  
Ensured correct data types:
```python
df['release_year'] = df['release_year'].astype(int)
```

---

### ✅ Summary of Changes  

| Task                        | Status   |
|-----------------------------|----------|
| Missing Values Handled      | ✅       |
| Duplicate Rows Removed      | ✅       |
| Text Fields Standardized    | ✅       |
| Date Format Converted       | ✅       |
| Column Names Renamed        | ✅       |
| Data Types Fixed            | ✅       |

---

### 📌 Conclusion  
The Netflix dataset is now cleaned and consistent, making it ideal for:

- 📊 Dashboard creation  
- 📈 Trend analysis  
- 🤖 Machine learning models  

All transformations ensure the dataset is well-structured and ready for further use.

---

### 💻 Tools Used  
- Python  
- Pandas  
- Jupyter Notebook  

---
