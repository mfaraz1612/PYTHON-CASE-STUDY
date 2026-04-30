import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

np.random.seed(42)

students = [f"Student_{i}" for i in range(1, 21)]
subjects = ['Math', 'Physics', 'Chemistry', 'English', 'Computer Science']

scores = np.random.randint(40, 100, size=(20, 5))

df = pd.DataFrame(scores, columns=subjects, index=students)

df['Total_Score'] = df[subjects].sum(axis=1)
df['Average_Score'] = df[subjects].mean(axis=1)

subject_stats = pd.DataFrame({
    'Mean': df[subjects].mean(),
    'Median': df[subjects].median(),
    'Standard Deviation': df[subjects].std()
})

print("--- Subject-Wise Statistical Analysis ---")
print(subject_stats.round(2))
print("\n")

sorted_df = df.sort_values(by='Total_Score', ascending=False)
high_performers = sorted_df.head(3)
low_performers = sorted_df.tail(3)

print("--- Top 3 High-Performing Students ---")
print(high_performers[['Total_Score', 'Average_Score']])
print("\n--- Bottom 3 Low-Performing Students ---")
print(low_performers[['Total_Score', 'Average_Score']])
print("\n")

plt.figure(figsize=(15, 12))

plt.subplot(2, 2, 1)
subject_stats['Mean'].plot(kind='bar', color='skyblue', edgecolor='black')
plt.title('Average Score per Subject', fontsize=14)
plt.ylabel('Average Score')
plt.xticks(rotation=45)
plt.grid(axis='y', linestyle='--', alpha=0.7)

plt.subplot(2, 2, 2)
plt.plot(df.index, df['Total_Score'], marker='o', color='coral', linestyle='-', linewidth=2)
plt.title('Total Scores of All Students', fontsize=14)
plt.ylabel('Total Score')
plt.xticks(rotation=90)
plt.grid(axis='both', linestyle='--', alpha=0.5)

plt.subplot(2, 2, 3)
plt.hist(df['Average_Score'], bins=6, color='lightgreen', edgecolor='black')
plt.title('Distribution of Average Student Scores', fontsize=14)
plt.xlabel('Average Score Range')
plt.ylabel('Number of Students')
plt.grid(axis='y', linestyle='--', alpha=0.7)

plt.subplot(2, 2, 4)
excellent = len(df[df['Average_Score'] >= 80])
good = len(df[(df['Average_Score'] >= 60) & (df['Average_Score'] < 80)])
needs_improvement = len(df[df['Average_Score'] < 60])

labels = ['Excellent (>=80)', 'Good (60-79)', 'Needs Improvement (<60)']
sizes = [excellent, good, needs_improvement]
colors = ['gold', 'lightblue', 'lightcoral']
explode = (0.1, 0, 0) 

plt.pie(sizes, explode=explode, labels=labels, colors=colors, autopct='%1.1f%%', startangle=140, shadow=True)
plt.title('Overall Performance Breakdown', fontsize=14)

plt.tight_layout()
plt.show()

print("--- Meaningful Insights Drawn from Data ---")
best_subject = subject_stats['Mean'].idxmax()
worst_subject = subject_stats['Mean'].idxmin()

print(f"1. Highest Scoring Subject: {best_subject} has the highest class average ({subject_stats.loc[best_subject, 'Mean']:.2f}), indicating strong student comprehension in this area.")
print(f"2. Area for Improvement: {worst_subject} has the lowest class average ({subject_stats.loc[worst_subject, 'Mean']:.2f}), suggesting a potential need for syllabus revision or extra tutoring.")
print(f"3. Class Consistency: The standard deviation is highest in {subject_stats['Standard Deviation'].idxmax()}, meaning the scores are the most spread out (some students did very well, others very poorly).")
print(f"4. Top Achievers: {excellent} out of {len(df)} students achieved an overall average of 80% or higher.")
