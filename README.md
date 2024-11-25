# Research-for-University-Project
# **Fitness App Analysis Project**

## **Overview**
This project analyzes Google Play Store data to derive insights into the fitness application industry. Using Python for data cleaning and feature engineering, and Power BI for interactive visualizations, the project focuses on assessing the performance, user engagement, and features of fitness apps compared to other app categories.

---

## **Data Cleaning Process**
The dataset provided contained raw data with inconsistencies, null values, and unclean formats. Here’s the step-by-step process undertaken to clean and prepare the data for analysis:

1. **Handle Missing Values**:
   - Identified columns with missing values (`Current Ver`, `Android Ver`) and replaced them with appropriate defaults or used forward/backward filling methods.

2. **Standardizing Columns**:
   - Converted `Installs` column by removing non-numeric characters (like `+` and `,`) and cast it to numeric type.
   - Cleaned the `Size` column by converting sizes (e.g., MB, KB) to a standard numeric format (all in MB).

3. **Parsing Dates**:
   - The `Last Updated` column was converted to datetime format.
   - Extracted the year from `Last Updated` to create a new column called `InstallYear` for trend analysis.

4. **Numeric Conversion**:
   - Converted `Reviews` and `Price` columns to numeric types after removing unwanted characters.

5. **Categorization**:
   - Created a new `Free vs Paid` column by categorizing apps as either `Free` or `Paid` based on the `Price` column.

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

8. **Free vs Paid**:
   - Indicates whether an app is `Free` or `Paid`.
   - **Purpose**: Identify the proportion of free and paid apps and analyze their installs.

---
## **Visualization Insights**
Using **Power BI**, the following visualizations were created to interpret the data in this visual:
![Uploading fitness app data visualisation .png…]()
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
