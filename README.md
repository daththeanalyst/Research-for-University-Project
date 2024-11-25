# **Fitness App Analysis Project**

## **Overview**
This project analyzes Google Play Store data to derive insights into the fitness application industry. Using Python for data cleaning and feature engineering, and Power BI for interactive visualizations, the project focuses on assessing the performance, user engagement, and features of fitness apps compared to other app categories.

---

## **Data Source**
The dataset used for this project was obtained from [Google Play Store Dataset](https://www.kaggle.com/lava18/google-play-store-apps) available on Kaggle. It contains details about over 10,000 apps, including their category, ratings, reviews, size, type (free/paid), price, installs, and other metadata.

### Key Details:
- **Number of Records**: 10,841
- **Columns**: 13, including `App`, `Category`, `Rating`, `Reviews`, `Size`, `Installs`, `Type`, and more.
- **Target**: The focus was primarily on apps in the `Health & Fitness` category.

---

## **Data Cleaning Process**
The raw dataset contained inconsistencies such as missing values, improper formatting, and mixed data types. Below are the key steps performed in **Python** for cleaning the data:

1. **Handle Missing Values**:
   - Checked for null values in all columns using `df.isnull().sum()`.
   - Columns with minimal missing values (`Current Ver`, `Android Ver`) were forward/backward-filled.
   - For `Rating`, missing values were filled with the category-wise average rating.

2. **Data Type Standardization**:
   - Converted the `Installs` column:
     - Removed special characters like `+` and `,` using `.str.replace()`.
     - Cast to numeric type using `.astype(float)`.
   - Processed the `Price` column:
     - Removed the `$` symbol.
     - Converted to numeric for analysis.
   - Cleaned the `Reviews` column:
     - Ensured all entries were integers and removed non-numeric anomalies.

3. **Size Standardization**:
   - Converted app sizes from mixed units (e.g., MB, KB) into a unified numeric format in MB.
   - Used a custom function to handle conversions:
     ```python
     def convert_size(size):
         if 'M' in size:
             return float(size.replace('M', ''))
         elif 'K' in size:
             return float(size.replace('K', '')) / 1024
         else:
             return np.nan
     df['Size'] = df['Size'].apply(convert_size)
     ```

4. **Datetime Parsing**:
   - Converted `Last Updated` to a datetime format using `pd.to_datetime()`.
   - Extracted the year from `Last Updated` to create a new `InstallYear` column for time trend analysis.

5. **Categorization**:
   - Created a new column, `Free vs Paid`, by checking if the `Price` column was greater than 0.
     ```python
     df['Free vs Paid'] = df['Price'].apply(lambda x: 'Free' if x == 0 else 'Paid')
     ```

6. **Duplicate Removal**:
   - Identified and removed duplicate entries based on the `App` column.

7. **Target Filtering**:
   - Isolated apps from the `Health & Fitness` category into a separate DataFrame (`fitness_apps`) for specific analysis.

### **Final Cleaned Dataset**
After cleaning, the dataset contained:
- **Columns**: 15 (including new calculated features).
- **Rows**: 10,841 (no loss in records due to cleaning).

---

## **Feature Engineering**
To enhance the insights and perform meaningful comparisons, new calculated features were created:

1. **TotalHealthFitnessInstalls**:
   - Captures the total number of installs for apps in the `Health & Fitness` category.
   - **Purpose**: Analyze the market size and growth potential of fitness apps.

2. **AvgHealthFitnessRating**:
   - Calculates the average rating for apps in the `Health & Fitness` category.
   - **Purpose**: Understand user satisfaction levels in the fitness industry.

3. **AppType**:
   - Categorized apps as `Free` or `Paid` based on their price.
   - **Purpose**: Compare user engagement and installs between free and paid apps.

4. **TotalInstallsByCategory**:
   - Aggregates the total installs for each app category.
   - **Purpose**: Identify the popularity of different categories relative to `Health & Fitness`.

5. **InstallsByCategory**:
   - A comparative measure of installs within categories for visual ranking.
   - **Purpose**: Analyze trends and identify competitive categories.

6. **EngagementIndex**:
   - A calculated column that combines ratings and reviews as a measure of user engagement.
   - **Formula**: `(Rating * Reviews)`.
   - **Purpose**: Evaluate app success based on user interactions.

7. **AvgRatingByCategory**:
   - Calculates the average rating for apps in each category.
   - **Purpose**: Compare satisfaction levels across app categories.

---

## **Visualization Insights**
Using **Power BI**, the following visualizations were created to interpret the data:
![Fitness App Data Visualization](fitness%20app%20data%20visualisation.png)

1. **Installs By Category**:
   - **Type**: Bar Chart
   - **Purpose**: Compare total installs across all app categories and highlight the position of `Health & Fitness`.

2. **Free vs Paid Fitness Applications**:
   - **Type**: Pie Chart
   - **Purpose**: Visualize the distribution of free vs paid apps within the fitness category.

3. **Average Fitness App Rating**:
   - **Type**: Gauge Chart
   - **Purpose**: Display the average user satisfaction score for fitness apps.

4. **Satisfaction Rate by Category**:
   - **Type**: Bar Chart
   - **Purpose**: Compare user ratings across different categories.

5. **Fitness App Downloads by Year**:
   - **Type**: Line Chart
   - **Purpose**: Show the trend of fitness app installs over the years.

6. **Average Rating Per Category**:
   - **Type**: Column Chart
   - **Purpose**: Compare the average user satisfaction ratings across app categories.

---

## **Conclusion**
This project provides actionable insights into the fitness app industry by leveraging data analysis and visualization techniques. The calculated features and dashboards demonstrate the growth, user satisfaction, and engagement trends, making a strong case for developing a fitness app tailored to user preferences.

---
