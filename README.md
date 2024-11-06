# Importing pandas
import pandas as pd

# Loading student-por.xlsx
df=pd.read_excel(r'C:\Users\adity\OneDrive\Documents\student-por.xlsx.xlsx')

# Displaying the first 5 rows
print('first five rows:')
print(df.head(5))

# Displaying number of columns
print('\ncolumn names:')
print(df.columns)

# Displaying data types
print('\nData types:')
print(df.dtypes)

# Displaying summary statistics
print('\nSummary statistics')
print(df.describe())

# Displaying info about data frame
print('\nDataFrame info:')
print(df.info())

# CALCULATING MEAN, MEDIAN AND STANDARD DEVIATION

# Loading the Excel file
file_path = r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx'
data = pd.read_excel(r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx')

# Displaying column names to check for correct naming
print("Column names:", data.columns)

# Calculating the mean, median, and standard deviation for each subject
math_mean = data['math score'].mean()
math_median = data['math score'].median()
math_std = data['math score'].std()

reading_mean = data['reading score'].mean()
reading_median = data['reading score'].median()
reading_std = data['reading score'].std()

writing_mean = data['writing score'].mean()
writing_median = data['writing score'].median()
writing_std = data['writing score'].std()

# Display the results
print(f"Math - Mean: {math_mean}, Median: {math_median}, Standard Deviation: {math_std}")
print(f"Reading - Mean: {reading_mean}, Median: {reading_median}, Standard Deviation: {reading_std}")
print(f"Writing - Mean: {writing_mean}, Median: {writing_median}, Standard Deviation: {writing_std}")

# MAXIMUM AND MINIMUM FOR EACH SUBJECT

# Loading the Excel file
file_path = r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx'  # Update the path if the file is in a different location
data = pd.read_excel(file_path)

# Displaying column names to check for correct naming
print("Column names:", data.columns)

# Calculating the minimum and maximum scores for each subject
math_min = data['math score'].min()
math_max = data['math score'].max()

reading_min = data['reading score'].min()
reading_max = data['reading score'].max()

writing_min = data['writing score'].min()
writing_max = data['writing score'].max()

# Displaing the results
print(f"Math - Minimum: {math_min}, Maximum: {math_max}")
print(f"Reading - Minimum: {reading_min}, Maximum: {reading_max}")
print(f"Writing - Minimum: {writing_min}, Maximum: {writing_max}")

# CREATING HISTOGRAM FOR THE DISTRIBUTION OF SCORES IN MATH,READING AND WRITING

import matplotlib.pyplot as plt

# Loading the Excel file
file_path = r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx'
data = pd.read_excel(r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx')

# Checking column names to ensure they match
print("Column names:", data.columns)

# Plot histograms for each subject
plt.figure(figsize=(15, 5))

# Math score histogram
plt.subplot(1, 3, 1)
plt.hist(data['math score'], bins=10, color='skyblue', edgecolor='black')
plt.title('Math Score Distribution')
plt.xlabel('Scores')
plt.ylabel('Frequency')

# Reading score histogram
plt.subplot(1, 3, 2)
plt.hist(data['reading score'], bins=10, color='lightgreen', edgecolor='black')
plt.title('Reading Score Distribution')
plt.xlabel('Scores')
plt.ylabel('Frequency')

# Writing score histogram
plt.subplot(1, 3, 3)
plt.hist(data['writing score'], bins=10, color='salmon', edgecolor='black')
plt.title('Writing Score Distribution')
plt.xlabel('Scores')
plt.ylabel('Frequency')

# Showing the plots
plt.tight_layout()
plt.show()

# PLOTTING THE BAR CHART SHOWING THE E=RELATIONSHIP BETWEEN MATH SCORES AND READING SCORES

# Loading the Excel file
file_path = r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx'
data = pd.read_excel(r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx')

# Calculating the average score for each subject by gender
average_scores = data.groupby('gender')[['math score', 'reading score', 'writing score']].mean()

# Plotting the bar chart
average_scores.plot(kind='bar', figsize=(10, 6), color=['skyblue', 'lightgreen', 'salmon'], edgecolor='black')

# Adding chart title and labels
plt.title('Average Scores by Gender')
plt.xlabel('Gender')
plt.ylabel('Average Score')
plt.xticks(rotation=0)
plt.legend(title="Subjects")

# Displaying the bar chart
plt.show()

# USING THE SCATTER PLOT

# Defining the file path and load the Excel file
file_path = r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx'
data = pd.read_excel(r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx')

# Creating a scatter plot for math scores vs. reading scores
plt.figure(figsize=(8, 6))
plt.scatter(data['math score'], data['reading score'], color='purple', alpha=0.5, edgecolor='k')

# Adding titles and labels
plt.title('Relationship Between Math Scores and Reading Scores')
plt.xlabel('Math Score')
plt.ylabel('Reading Score')

# Displaying the plot
plt.show()

# ANALYSING THE EFFECT OF PARENTAL EDUCATION LEVEL ON THE AVERAGE SCORES

# Loading the Ecxel file
file_path = r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx'
data = pd.read_excel(r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx')

# Grouping data by parental level of education and calculate the average scores for each level
average_scores_by_education = data.groupby('parental level of education')[['math score', 'reading score', 'writing score']].mean()

# Displaying the result
print(average_scores_by_education)

# COMPARING THE PERFORMANCE OF STUDENTS WHO COMPLETED THE TEST PREPARATION COURSE VERSUS THOSE WHO DID NOT

# Loading the Excel file
file_path =r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx'
data = pd.read_excel(r'C:\Users\adity\OneDrive\Documents\StudentsPerformance.xlsx')

# Separate data into two groups: those who completed the course and those who did not
completed_course = data[data['test preparation course'] == 'completed']
no_course = data[data['test preparation course'] == 'none']

# Calculate average scores for each group in math, reading, and writing
average_scores = {
    'Completed Course': completed_course[['math score', 'reading score', 'writing score']].mean(),
    'No Course': no_course[['math score', 'reading score', 'writing score']].mean()
}

# Convert to DataFrame for easier comparison
average_scores_df = pd.DataFrame(average_scores)

# Display the average scores
print(average_scores_df)

