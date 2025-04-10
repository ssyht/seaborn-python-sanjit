
---

### ✅ Module: Seaborn Libraries (Python)

_There will be four guided questions and answers in this page:_

**Q1: Load Titanic Dataset, Describe, and Analyze Survival**

```python
titanic = sns.load_dataset('titanic')
titanic.describe(include='all')
titanic['survived'].value_counts()
```

**Q2: Subplot – Median and Average Age by Class and Sex**

```python
fig, axes = plt.subplots(1, 2, figsize=(16, 6))

sns.barplot(data=titanic, x='class', y='age', hue='sex', estimator=np.median, ci=90, palette='bright', ax=axes[0])
axes[0].set_title('Median Age by Class and Sex (90% CI)')
axes[0].grid(True)

sns.barplot(data=titanic, x='class', y='age', hue='sex', estimator=np.mean, ci='sd', palette='dark', ax=axes[1])
axes[1].set_title('Average Age by Class and Sex (Std Dev)')
axes[1].grid(True)

plt.tight_layout()
plt.show()

````
**Q3: Regression – Age vs Fare for Adults Paying 10–100**

```python
subset = titanic[(titanic['age'] >= 18) & (titanic['fare'] > 10) & (titanic['fare'] < 100)]

sns.lmplot(data=subset, x='fare', y='age', ci=99,
           scatter_kws={'color': 'lightgray'},
           line_kws={'color': 'darkgreen', 'linewidth': 5})

plt.title('Regression of Age vs Fare (Adults Paying $10–$100)')
plt.grid(True)
plt.show()
```
**Q4: Correlation Heatmap**

```python
corr = titanic.corr(numeric_only=True)
plt.figure(figsize=(10, 6))
sns.heatmap(corr, annot=True, cmap='coolwarm', fmt=".2f")
plt.title('Correlation Heatmap of Titanic Dataset')
plt.show()
```
