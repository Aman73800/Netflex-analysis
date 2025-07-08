# 📊 Netflix Data Analysis Project

This project analyzes Netflix content data using Python and the Pandas library. The dataset includes information such as title, genre, director, release year, country, and type (movie/TV show).

---

## 📁 Files Included

* `netflix.ipynb`: Main Jupyter Notebook with all analysis code.
* `netflix_data.csv`: The dataset used for analysis.
* `/img/`: Folder to store generated plots and output images.

---

## 🧪 Requirements

Install the required libraries with:

```bash
pip install pandas matplotlib seaborn
```

---

## 📌 Project Structure and Detailed Code Explanation

---

### 📍 1. **Importing Libraries**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

* **pandas**: For loading and transforming the data.
* **matplotlib**: Used for plotting and basic charting.
* **seaborn**: For advanced and styled visualizations.

---

### 📍 2. **Loading the Dataset**

```python
df = pd.read_csv("netflix_data.csv")
df.head()
```

* Loads the dataset into a Pandas DataFrame.
* `df.head()` previews the first five records.

![Dataset Preview](https://github.com/Aman73800/Netflex-analysis/blob/main/netflix/img/head.png)

---

### 📍 3. **Checking for Missing Values**

```python
df.isnull().sum()
```

* Reveals missing data per column to assess data quality.

![Missing Data](https://github.com/Aman73800/Netflex-analysis/blob/main/netflix/img/null.png)

---

### 📍 4. **Basic Statistical Info**

```python
df.describe(include='all')
```

* Summarizes statistics for numeric and categorical columns.
* Useful to understand distributions and data types.

---

### 📍 5. **Data Cleaning (optional)**

```python
df.dropna(subset=['director', 'country'], inplace=True)
```

* Drops rows missing critical fields like director or country.

---

### 📍 6. **Visualizations**

#### 🔹 Count of Movies vs TV Shows (Based on Duration Watched)

```python
df['Show_Type'] = df['duration_watched'].apply(lambda x: 'TV Show' if x >= 60 else 'Movie')
df['Show_Type'].value_counts().plot(kind='bar', color='skyblue')
plt.title("Movies vs TV Shows")
plt.ylabel("Count")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()
```

* Shows how many entries are movies vs TV shows.

![Type Count](https://github.com/Aman73800/Netflex-analysis/blob/main/netflix/img/M%20vs%20TV.png)

---

#### 🔹 Top 10 Countries by Content Production

```python
top_countries = df['country'].value_counts().head(10)
top_countries.plot(kind='barh', color='lightgreen')
plt.title("Top 10 Countries Producing Netflix Content")
plt.xlabel("Number of Titles")
plt.tight_layout()
plt.show()
```

* Displays the top 10 content-producing countries on Netflix.

![Top Countries](https://github.com/Aman73800/Netflex-analysis/blob/main/netflix/img/10%20gen.png)

---

#### 🔹 Trend of Content Over the Years

```python
df['release_year'] = pd.to_datetime(df['release_year'], format='%Y', errors='coerce')
year_counts = df['release_year'].dt.year.value_counts().sort_index()
year_counts.plot(kind='line', marker='o', color='coral')
plt.title("Content Released Over the Years")
plt.xlabel("Year")
plt.ylabel("Number of Titles")
plt.grid(True)
plt.tight_layout()
plt.show()
```

* Illustrates the trend in content releases over time.

![Year Trend](https://github.com/Aman73800/Netflex-analysis/blob/main/netflix/img/rel%20over%20year.png)

---

## 📂 Output Images

Place all chart screenshots or exports in an `images/` folder and refer to them using markdown image links like:

```markdown
![Alt Text](images/filename.png)
```

Suggested names:

* `data_head.png`
* `null_check.png`
* `type_count.png`
* `top10_countries.png`
* `year_trend.png`

---

## 📌 Conclusion

This project provided insights into Netflix content including:

* Most active content countries
* Ratio of Movies vs TV Shows
* Content trends over the years

You can extend this by analyzing:

* Genres popularity
* Actor/director frequency
* Ratings and runtime analysis

---

## 🧑‍💻 Author

**Aman Yadav**
📧 [ay1995880@gmail.com](mailto:ay1995880@gmail.com)
