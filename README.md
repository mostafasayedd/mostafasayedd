import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


df = pd.read_excel('hollywood movies.xlsx')
df.columns = df.columns.str.strip()

print("First 5 rows of the dataset:")
print(df.head())

gross_col = 'Revenue(INR)'
budget_col = 'Budget(INR)'

top_10 = df.sort_values(by=gross_col, ascending=False).head(10)
plt.figure(figsize=(12,6))
sns.barplot(x=gross_col, y='Movie_Name', data=top_10, palette='viridis')
plt.title('Top 10 Movies by Revenue (INR)')
plt.xlabel('Revenue (INR)')
plt.ylabel('Movie Title')
plt.tight_layout()
plt.show()

plt.figure(figsize=(8,6))
sns.scatterplot(data=df, x=budget_col, y=gross_col)
plt.title('Budget vs Revenue')
plt.xlabel('Budget (INR)')
plt.ylabel('Revenue (INR)')
plt.tight_layout()
plt.show()

plt.figure(figsize=(8,6))
sns.histplot(df[budget_col], bins=30, kde=True, color='teal')
plt.title('Distribution of Movie Budgets')
plt.xlabel('Budget (INR)')
plt.ylabel('Number of Movies')
plt.tight_layout()
plt.show()
