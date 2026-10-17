# Online Food Delivery: Customer Behaviour Analysis

An exploratory data analysis (EDA) in Python of customers who use online food delivery. The project looks at **who these customers are** and **which groups are more likely to say "Yes" to ordering**, using demographic and feedback data.

## Objective

To explore how a customer's background (age, gender, marital status, occupation, income, education, family size and location) relates to their online food ordering behaviour.

**Key questions**
- What kind of customers use online food delivery the most?
- Which groups are more likely to say **Yes** to ordering?

## Dataset

- **Raw size:** 388 rows x 14 columns, with no missing values
- **After cleaning:** 285 rows (103 duplicate rows removed)
- **Location:** customers appear to be in Bengaluru, India (based on the coordinates and 560xxx pin codes)
- **Source:** `[EDIT: add the dataset source and link]`

| Column | Description |
|--------|-------------|
| Age | Customer age (18 to 33) |
| Gender | Female / Male |
| Marital Status | Single / Married / Prefer not to say |
| Occupation | Student / Employee / Self Employed / House wife |
| Monthly Income | No Income to More than 50000 (Rs.) |
| Educational Qualifications | Uneducated to Ph.D |
| Family size | Number of people in the household (1 to 6) |
| Customer Type | New / Regular / Frequent |
| latitude, longitude, Pin code | Customer location |
| Output | Whether the customer said **Yes** or **No** to ordering (target of the analysis) |
| Feedback | Positive / Negative |

## Methodology

1. **Data inspection:** shape, missing values, duplicates, summary statistics
2. **Data cleaning:** removed 103 duplicate rows and dropped `Unnamed: 13`, an exact copy of `Output`
3. **Exploratory analysis:** customer counts per group, Yes/No split, share of Yes by group, and feedback vs. output
4. **Feature engineering:** created seven new columns
   - `Age Group` (18-21, 22-24, 25-27, 28+)
   - `Income Level` (0 to 4) and `Education Level` (0 to 4)
   - `Family Type` (Small: 3 or fewer, Large: 4 or more)
   - `Is Student`, `Is Married`, `Positive Feedback` (1/0 flags)
5. **Pattern analysis:** compared the share of Yes across the new groups

## Key Findings

### Who the customers are

![Customers in each group](https://github.com/KinneryAnyanga/Online-Food-Ordering-Analysis/commit/25334cc0c5cdf6b3a0227ce1d154d48766380a97)

- The average customer is about 24 years old with a family of about 3
- Roughly half are students, and most are single and have no income
- About 94% are Regular or Frequent customers; only a few are New

### Overall response

About **76% of customers (217 of 285) said Yes** and 24% (68) said No, so the data is imbalanced towards Yes.

### Who says Yes more often

![Share of Yes by marital status, occupation and income](https://github.com/KinneryAnyanga/Online-Food-Ordering-Analysis/commit/25334cc0c5cdf6b3a0227ce1d154d48766380a97)

| Group | Share of Yes |
|-------|-------------|
| Single | 85% |
| Married | 61% |
| Students | 88% |
| Non-students | 65% |
| No income | 85% |
| Income above Rs.25,000 | about 63% to 64% |

### Patterns across the new features

![Share of Yes by age group, family type and income level](https://github.com/KinneryAnyanga/Online-Food-Ordering-Analysis/commit/25334cc0c5cdf6b3a0227ce1d154d48766380a97)

- **Age:** 22-24 has the highest Yes-rate (88%); it drops to 65% at 25-27 and 62% at 28+
- **Income:** the Yes-rate falls as income rises
- **Family type:** almost no difference (77% small vs. 75% large)
- Age, income, student status and marital status overlap heavily, since students are young, single and have no income

### Feedback is the strongest signal

![Feedback by output](https://github.com/KinneryAnyanga/Online-Food-Ordering-Analysis/commit/25334cc0c5cdf6b3a0227ce1d154d48766380a97)

- Customers with **positive feedback said Yes 87%** of the time
- Customers with **negative feedback said Yes only 28%** of the time
- About 81% of all feedback was positive

## Conclusion

- Most customers are young, single students with no income
- Single people and students say Yes more often than married people and employees
- Gender and customer type make little difference
- Customers who give positive feedback mostly say Yes

## Recommendations

- Keep the existing customer base with better service, since good service leads to positive feedback and repeat orders
- Introduce incentives aimed at students and single customers
- Keep food and delivery prices pocket-friendly for the young, low-income customer base

## Limitations

- Small sample (285 customers after cleaning), mostly young students from one city, so results may not generalise
- The analysis is descriptive: it shows associations, not causes
- Overlapping features (age, income, student status) make it hard to separate their individual effects

## Getting Started

**Requirements:** Python 3.8+, Jupyter, and the libraries below.

```bash
git clone https://github.com/KinneryAnyanga/Online-Food-Ordering-Analysis.git
cd Online-Food-Ordering-Analysis
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Online_Food_Delivery_Analysis.ipynb
```

## Tools

Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook

## Future Work

- Build a classification model (e.g. logistic regression) to predict Yes/No
- Test whether the differences between groups are statistically significant
- Build an interactive dashboard

## Author

**Kinnery Anyanga** · [GitHub](https://github.com/KinneryAnyanga)
