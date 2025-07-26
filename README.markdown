# Exploratory Data Analysis (EDA) Report for Book Sales Dataset

## Introduction
This report presents the findings from an Exploratory Data Analysis (EDA) conducted on the `Books_Data_Clean.csv` dataset using a Jupyter Notebook (`Book_Sales.ipynb`). The dataset contains information about book sales, including attributes such as publishing year, book name, author, language, author rating, book ratings, sales metrics, and publisher details. The analysis focuses on books published after 1990, as specified in the notebook, and aims to uncover patterns, trends, and insights from the data.

![image alt](https://github.com/Raka-Deb/Book-Sales-Analysis-/blob/b777d90e89ee388b267a83551579e4aaf99b820c/stack-of-books-on-a-brown-background-concept-for-world-book-day-photo.jpg)


## Dataset Overview
The dataset includes 1070 records initially, with the following columns:
- **index**: Unique identifier for each record.
- **Publishing Year**: Year the book was published (float, with some negative values indicating potential data issues).
- **Book Name**: Title of the book.
- **Author**: Author(s) of the book.
- **language_code**: Language of the book (e.g., 'en-US', 'eng').
- **Author_Rating**: Rating of the author (e.g., 'Novice', 'Intermediate').
- **Book_average_rating**: Average rating of the book (scale: 0-5).
- **Book_ratings_count**: Number of ratings the book received.
- **genre**: Genre of the book (e.g., 'genre fiction', 'fiction').
- **gross sales**: Total sales revenue in dollars.
- **publisher revenue**: Revenue earned by the publisher in dollars.
- **sale price**: Price per unit of the book.
- **sales rank**: Rank of the book based on sales.
- **Publisher**: Name of the publisher.
- **units sold**: Number of units sold.

After filtering for books published after 1990, the dataset is reduced to **748 records**.

## Key Findings from Descriptive Statistics
The descriptive statistics (`df.describe()`) provide insights into the numerical columns of the filtered dataset (books published after 1990):

### 1. **Publishing Year**
- **Range**: 1991 to 2016.
- **Mean**: 2005.88, indicating most books in the dataset were published in the mid-2000s.
- **Standard Deviation**: 6.36, suggesting a moderate spread of publication years within this period.
- **Implication**: The dataset focuses on relatively recent publications (within a 25-year span), which may reflect modern publishing trends.

### 2. **Book Average Rating**
- **Range**: 2.97 to 4.77 (on a 0-5 scale).
- **Mean**: 3.9968, indicating that most books have an average rating close to 4, suggesting generally positive reception.
- **Standard Deviation**: 0.255, showing low variability in ratings, with most books clustered around the mean.
- **Implication**: The books in the dataset are generally well-rated, with few outliers at the lower end.

### 3. **Book Ratings Count**
- **Range**: 27,308 to 206,792.
- **Mean**: 93,197.59, indicating a significant number of ratings per book on average.
- **Standard Deviation**: 30,982.71, suggesting variability in the popularity or exposure of books.
- **Implication**: Some books are significantly more reviewed than others, possibly indicating bestsellers or widely recognized titles.

### 4. **Gross Sales**
- **Range**: $104.94 to $47,795.
- **Mean**: $1,757.99, showing a wide range of sales performance.
- **Standard Deviation**: $3,952.51, indicating high variability in sales revenue, likely driven by a few high-performing books.
- **Implication**: The sales distribution is skewed, with a few books generating significantly higher revenue.

### 5. **Publisher Revenue**
- **Range**: $0 to $28,677.
- **Mean**: $806.74, much lower than gross sales, indicating that publishers receive a fraction of the total revenue.
- **Standard Deviation**: $2,270.13, showing high variability, similar to gross sales.
- **Implication**: Publisher revenue varies widely, possibly due to differences in profit-sharing agreements or book pricing.

### 6. **Sale Price**
- **Range**: $0.99 to $25.89.
- **Mean**: $4.88, indicating that most books are priced affordably.
- **Standard Deviation**: $3.55, showing moderate variability in pricing.
- **Implication**: The dataset includes both low-cost and premium-priced books, reflecting diverse market segments.

### 7. **Sales Rank**
- **Range**: 3 to 1,273.
- **Mean**: 627.96, suggesting a broad range of sales performance.
- **Standard Deviation**: 364.05, indicating variability in how books rank in sales.
- **Implication**: The dataset includes both top-selling and lower-ranked books, providing a comprehensive view of market performance.

### 8. **Units Sold**
- **Range**: 106 to 61,560 units.
- **Mean**: 9,920.13 units, showing that, on average, books sell in the thousands.
- **Standard Deviation**: 15,505.26, indicating high variability, with some books selling significantly more units than others.
- **Implication**: A few books are likely bestsellers, driving the high variability in units sold.

## Analysis of Units Sold Over Time
The notebook includes a line plot visualizing the total units sold by publishing year (`df.groupby("Publishing Year")["units sold"].sum().plot(kind="line", marker="o")`). Key observations from the plot:

- **Trend**: The total units sold fluctuate across the years, with noticeable peaks and troughs.
- **Peaks**: Certain years (e.g., around 2007 and 2011) show higher total units sold, suggesting periods of strong market performance or the release of popular titles.
- **Declines**: Some years exhibit lower sales, indicating potential market fluctuations or fewer high-selling books.
- **Implication**: The book market appears to have cyclical patterns, possibly influenced by major releases, economic factors, or publishing trends.

## Additional Insights from Data Exploration
### 1. **Data Quality**
- The dataset initially included books with publishing years as early as -560, which were removed by filtering for years after 1990. This suggests potential data quality issues (e.g., erroneous or historical entries) in the original dataset.
- The presence of a single missing value in `Publishing Year` (1070 total records, 1069 non-null) indicates minor data incompleteness.

### 2. **Genre Distribution**
- The dataset includes genres like 'genre fiction' and 'fiction'. Further analysis could explore the distribution of genres and their impact on sales or ratings.
- Example: Books like *Beowulf* and *Batman: Year One* are classified as 'genre fiction', while *When You Are Engulfed in Flames* is 'fiction', suggesting nuanced genre categorizations.

### 3. **Publisher Analysis**
- Publishers like HarperCollins, Amazon Digital Services, Hachette Book Group, and Penguin Group appear in the dataset. Analyzing sales by publisher could reveal which publishers dominate the market.
- Example: HarperCollins published top-selling books like *Beowulf* and *Batman: Year One*, indicating a strong presence in genre fiction.

### 4. **Author Rating**
- The dataset categorizes authors as 'Novice' or 'Intermediate'. Exploring the relationship between author rating and book performance (e.g., sales, ratings) could provide insights into market preferences.
- Example: *Go Set a Watchman* by Harper Lee (Novice) has a lower average rating (3.31) than *Batman: Year One* by Frank Miller et al. (Intermediate, 4.23), suggesting that author experience may influence book quality or reception.

### 5. **Language Code**
- The dataset includes language codes like 'en-US' and 'eng'. Most books appear to be in English, but further analysis could confirm if language impacts sales or ratings.

## Recommendations for Further Analysis
1. **Correlation Analysis**: Examine correlations between numerical variables (e.g., `Book_average_rating`, `sale price`, `units sold`) to identify factors driving sales.
2. **Genre Impact**: Analyze sales and ratings by genre to determine which genres are most popular or profitable.
3. **Publisher Performance**: Compare publishers based on total units sold, gross sales, or average book ratings to identify market leaders.
4. **Temporal Trends**: Investigate specific years with high or low sales to understand external factors (e.g., economic conditions, major book releases).
5. **Visualization Enhancements**: Add more visualizations, such as histograms for `sale price` or bar plots for `units sold` by publisher, to uncover additional patterns.
6. **Data Cleaning**: Address potential data quality issues, such as negative publishing years or missing values, to ensure robust analysis.

## Conclusion
The EDA reveals a dataset rich with insights into book sales trends post-1990. Key findings include a wide range of sales performance, generally positive book ratings, and fluctuating sales trends over time. The dataset's focus on recent publications and diverse attributes (e.g., genre, publisher, author rating) provides opportunities for deeper analysis to inform publishing strategies or market predictions. Further exploration of correlations, genre impacts, and publisher performance is recommended to maximize the dataset's value.
