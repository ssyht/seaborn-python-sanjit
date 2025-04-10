
---

###  `page2.md`

**Guided questions & answers from five to seven will be in this page 2**



**Q5: Boxplot of Fare Distribution by Class and Sex (Fare < $200)**

```python
filtered = titanic[titanic['fare'] < 200]

plt.figure(figsize=(10, 8))
sns.boxplot(data=filtered, x='class', y='fare', hue='sex', palette='dark', fliersize=0, whis=[10, 90])
plt.title('Fare Distribution by Class and Sex (Fares < $200)')
plt.grid(True)
plt.show()
```

**Q6: Boxplot of All Numerical Columns (Excluding Fare)**

```python
numerical_cols = titanic.select_dtypes(include='number').drop(columns='fare')
melted = numerical_cols.melt(var_name='feature', value_name='value')

import warnings
warnings.simplefilter(action='ignore', category=FutureWarning)

g = sns.FacetGrid(melted, col="feature", col_wrap=3, sharey=False, height=4)
g.map(sns.boxplot, "value", color="steelblue")
g.set_titles("{col_name}")
g.fig.suptitle("Box Plots of Numerical Features (Excluding Fare)", fontsize=16, y=1.05)

plt.tight_layout()
plt.show()
```

**Q7: Violin Plot (Quartile Interior, Split by Sex)**

```python
filtered = titanic[titanic['fare'] < 200]
plt.figure(figsize=(10, 8))

sns.violinplot(data=filtered, x='class', y='fare', hue='sex',
               split=True, inner='quartile', scale='width', dodge=True, linewidth=1.5)

plt.title('Violin Plot of Fare Distribution by Class and Sex (Fares < $200)')
plt.grid(True)
plt.show()
```

**Answers:**

- Median fare (3rd class women) > 75th percentile fare (3rd class men)
- Highest median: First Class Female
- Lowest median: Third Class Male



---

### ✅ GitHub Commands (in `bash`)

```bash
# Create repo locally
mkdir titanic-seaborn-visuals && cd titanic-seaborn-visuals
git init

# Create files
touch README.md page1.md page2.md

# Paste the markdown into each file or use a text editor

# Add and push to GitHub
git add .
git commit -m "Initial commit of Titanic Seaborn Analysis"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/titanic-seaborn-visuals.git
git push -u origin main
