# pollution-apriori-association-rules
Apriori association rule mining on global pollution and energy recovery data, validated with hold-out, cross-validation and shuffle controls
# Global Pollution Analysis and Energy Recovery – Apriori Association Rules

Mining association rules between pollution levels (air, water, soil, CO₂, industrial waste), energy consumption and energy recovery across countries with the **Apriori algorithm**, and testing whether the discovered rules are genuine or just chance.

## Project Workflow

**Phase 1 – Data Preprocessing and Feature Engineering**
- Cleaning and imputation, label encoding of Country and Year, scaled pollution indices
- Energy consumption per capita
- Yearly pollution trend vs. energy recovery
- Severity categories (Low / Medium / High) using tercile thresholds learned from training data only

**Phase 2 – Apriori Association Rules**
- Frequent itemsets and rules (`mlxtend`) with support, confidence and lift
- Significance testing per rule (one-sided Fisher / hypergeometric test, Benjamini-Hochberg FDR correction)
- Focus on rules linking pollution levels to energy-recovery levels
- Visualizations: frequent itemsets, support vs confidence, lift heat-map, rule network

**Phase 3 – Evaluation and Validation**
- 80/20 hold-out validation: rules mined on training data are re-measured on unseen data
- 5-fold cross-validation with out-of-fold lift and rule stability
- **Shuffle control:** the same analysis on column-shuffled data (no real associations) shows how many "strong" rules pure noise produces

**Phase 4 – Reporting and Insights**
- Comparison of Apriori with the CNN from the delivery project (different task types, so compared on approach, validation and trustworthiness rather than raw scores)
- Recommendations generated from the validated results

## Method Notes

- The dataset has an energy-recovered *amount* (GWh), not a *type* of recovery, so rules relate pollution to recovery *level* (Low / Medium / High).
- Thresholds and imputation values are fitted on training data only.
- A rule counts as evidence only if it is significant after FDR correction, carries over to unseen data, and exceeds what shuffled data produces.

## Results

*(Fill in after running the notebook on the real dataset.)*

| Check | Real data | Shuffled data |
|---|---|---|
| Frequent itemsets / rules | – | – |
| Strong rules (lift ≥ 1.2) | – | – |
| Significant rules (q < 0.05) | – | – |
| Train-test lift correlation | – | – |
| Stable cross-validation rules | – | – |

Top pollution → energy-recovery rule: –

## Limitations

- About 200 country-year records: each rule rests on a handful of records, so rules are unstable.
- Terciles are an arbitrary way to define Low / Medium / High; different thresholds can change the rules.
- Many rules are tested at once and rules share items, so they are not independent.
- Associations are not causal.

## Dataset

`Global_Pollution_Analysis.csv` should be placed in the project root next to the notebook.
Download link: https://drive.google.com/file/d/1AEMcCWzJ24fc26Q761SEOa1sOsZiJBC5/view?usp=sharing



Python, pandas, NumPy, SciPy, scikit-learn, mlxtend, NetworkX, Matplotlib, Seaborn
