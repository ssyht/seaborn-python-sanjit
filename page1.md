
---

### ✅ Module: Seaborn Libraries (Python)

_There will be four guided questions and answers in this page:_

**Q1: Load Titanic Dataset, Describe, and Analyze Survival
**
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
