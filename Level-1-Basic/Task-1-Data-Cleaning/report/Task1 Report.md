# Task 1: Data Cleaning & Preprocessing

## Dataset: Social Media Sentiment Dataset

---

### 1. Overview

The dataset contains social media posts from Twitter, Instagram, and Facebook with sentiment labels, engagement metrics (retweets, likes), timestamps, and geographic data. After loading, the dataset had 176 rows and 14 columns.

---

### 2. Issues Found

After loading the data with pandas and running `df.info()` and `df.head()`, I noticed several issues:

1. **Unnamed column** — An index column `Unnamed: 0` was present, which doesn't carry any analytical value.
2. **Inconsistent whitespace** — Text columns like `Platform`, `Country`, `Sentiment`, `User`, `Hashtags`, and `Text` had trailing and leading spaces (e.g., `' Twitter '`, `' USA       '`).
3. **Timestamp format** — The `Timestamp` column was stored as `object` (string) instead of `datetime`.
4. **Data types** — `Retweets` and `Likes` were stored as `float64`, and `Year`, `Month`, `Day`, `Hour` were also float. These should be integers.
5. **Sentiment column complexity** — The `Sentiment` column had over 30 unique values (Positive, Negative, Anger, Fear, Sadness, Joy, Love, Happiness, Disgust, etc.), which makes analysis difficult.
6. **Missing values** — Checked with `df.isnull().sum()` and found that no columns had null values, so no imputation was needed.
7. **Duplicates** — Checked with `df.duplicated().sum()` and found duplicates, which were removed.

---

### 3. Cleaning Steps

**Step 1 — Removed unnecessary column:**
```python
df.drop("Unnamed: 0", axis=1, inplace=True)
```

**Step 2 — Stripped whitespace from all text columns:**
```python
df["Text"] = df["Text"].str.strip()
df["Sentiment"] = df["Sentiment"].str.strip()
df["User"] = df["User"].str.strip()
df["Platform"] = df["Platform"].str.strip()
df["Hashtags"] = df["Hashtags"].str.strip()
df["Country"] = df["Country"].str.strip()
```
This fixed the inconsistency in `Platform` and `Country` values — now `'Twitter'`, `'Instagram'`, `'Facebook'` are clean and standardized.

**Step 3 — Missing values:**
```python
df.isnull().sum()
```
All columns returned 0 null values. No imputation or row removal was necessary.

**Step 4 — Removed duplicates:**
```python
df.duplicated().sum()
df.drop_duplicates(inplace=True)
```

**Step 5 — Converted Timestamp to datetime:**
```python
df["Timestamp"] = pd.to_datetime(df["Timestamp"])
```

**Step 6 — Type conversion:**
```python
df["Retweets"] = df["Retweets"].astype(int)
df["Likes"] = df["Likes"].astype(int)
df["Year"] = df["Year"].astype(int)
df["Month"] = df["Month"].astype(int)
df["Day"] = df["Day"].astype(int)
df["Hour"] = df["Hour"].astype(int)

df["Platform"] = df["Platform"].astype("category")
df["Sentiment"] = df["Sentiment"].astype("category")
df["Country"] = df["Country"].astype("category")
```

---

### 4. Feature Engineering

**Sentiment simplification:**

The original `Sentiment` column had 30+ unique emotion labels. I created a mapping dictionary to group them into 3 main categories — Positive, Negative, and Neutral — so that analysis and visualization become more meaningful.

```python
sentiment_map = {
    "Positive": "Positive", "Happiness": "Positive", "Joy": "Positive",
    "Love": "Positive", "Admiration": "Positive", "Gratitude": "Positive",
    "Hope": "Positive", "Excitement": "Positive", "Amusement": "Positive",
    "Enjoyment": "Positive", "Affection": "Positive", "Awe": "Positive",
    "Surprise": "Positive", "Acceptance": "Positive", "Adoration": "Positive",
    "Anticipation": "Positive", "Calmness": "Positive", "Enthusiasm": "Positive",
    "Pride": "Positive", "Elation": "Positive", "Euphoria": "Positive",
    "Contentment": "Positive", "Serenity": "Positive", "Empowerment": "Positive",
    "Compassion": "Positive", "Tenderness": "Positive", "Reverence": "Positive",
    "Fulfillment": "Positive", "Arousal": "Positive", "Kind": "Positive",
    
    "Negative": "Negative", "Anger": "Negative", "Fear": "Negative",
    "Sadness": "Negative", "Disgust": "Negative", "Disappointed": "Negative",
    "Bitter": "Negative", "Shame": "Negative", "Confusion": "Negative",
    "Despair": "Negative", "Grief": "Negative", "Loneliness": "Negative",
    "Jealousy": "Negative", "Resentment": "Negative", "Frustration": "Negative",
    "Boredom": "Negative", "Anxiety": "Negative", "Intimidation": "Negative",
    "Helplessness": "Negative", "Envy": "Negative", "Regret": "Negative",
    
    "Neutral": "Neutral"
}

df["Sentiment_Category"] = df["Sentiment"].map(sentiment_map)
```

After mapping, I checked for any unmapped values with `df["Sentiment_Category"].isnull().sum()` — all values were successfully categorized.

---

### 5. Visualizations

I created the following visualizations using seaborn and matplotlib, and exported them as PNG images for the report:

**1. Sentiment Distribution:**
```python
plt.figure(figsize=(8, 5))
ax = sns.countplot(data=df, x="Sentiment_Category", palette="Set2",
                   order=["Positive", "Negative", "Neutral"])
plt.title("Sentiment Distribution", fontsize=14, fontweight="bold")
plt.xlabel("Sentiment")
plt.ylabel("Count")
for container in ax.containers:
    ax.bar_label(container)
plt.savefig(r"D:\projects\codveda project\plots\sentiment_distribution.png",
            dpi=300, bbox_inches="tight")
plt.show()
```

**2. Sentiment by Platform:**
```python
plt.figure(figsize=(10, 6))
sns.countplot(data=df, x="Platform", hue="Sentiment_Category", palette="Set2")
plt.title("Sentiment by Platform", fontsize=14, fontweight="bold")
plt.xlabel("Platform")
plt.ylabel("Count")
plt.legend(title="Sentiment")
plt.savefig(r"D:\projects\codveda project\plots\sentiment_by_platform.png",
            dpi=300, bbox_inches="tight")
plt.show()
```

---

### 6. Output

The cleaned dataset was saved as:
```python
df.to_csv(r"D:\projects\codveda project\csv\cleaned_sentiment_data.csv", index=False)
```

**Final dataset shape:** 176 rows × 14 columns (after adding `Sentiment_Category`).

---

### Summary

The original raw dataset had several quality issues including inconsistent formatting, an unnecessary index column, and overly complex sentiment labels. After cleaning, standardizing data types, and engineering a simplified sentiment category, the dataset is now ready for further analysis. The key transformation was reducing 30+ emotion labels into 3 actionable categories, which makes the data much easier to work with in downstream tasks.