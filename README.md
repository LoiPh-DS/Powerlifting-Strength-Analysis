# Powerlifting Strength Analysis

## Overview

This project analyzes Raw USAPL powerlifting performances from the OpenPowerlifting dataset to explore how bodyweight relates to strength and how squat, bench press, and deadlift contribute to overall performance.

The project combines data cleaning, exploratory analysis, regression, binned summaries, rolling statistics, and interactive Altair visualizations.

## Research Questions

1. **Which lift scales best with bodyweight?**
2. **At what bodyweight does total strength begin to show diminishing returns?**
3. **How do squat, bench press, and deadlift proportions differ between male and female lifters?**

## Dataset

The source OpenPowerlifting file contained approximately **4.0 million meet-result records**. The analysis was narrowed to Raw, full-power USAPL performances and filtered for valid competition and demographic fields.

Key cleaning decisions included:

- Raw equipment only
- Full-power (`SBD`) performances only
- USAPL federation only
- Disqualified performances removed
- Missing age and weight-class records removed
- Analysis restricted to male and female lifters
- One best performance retained for each matching Name–Sex combination

The resulting analytical dataset contains approximately **93,000 lifters**.

The full source dataset is intentionally not stored in this repository because of its size.

## Tools

- Python
- pandas
- NumPy
- Altair
- Jupyter Notebook

## Key Findings

### 1. Squat scales most strongly with bodyweight

Regression analysis shows that squat has the steepest relationship with bodyweight within both male and female lifters. The interactive visualization allows the user to switch between squat, bench press, and deadlift and compare male, female, and pooled results.

An important secondary finding is that pooled male and female regression slopes differ substantially from sex-specific slopes, demonstrating why subgroup filtering matters when interpreting bodyweight–strength relationships.

### 2. Total strength shows diminishing returns at heavier bodyweights

Median Total increases rapidly across lighter and middle bodyweights, but the marginal increase becomes smaller and less consistent among heavier lifters.

Using 5 kg bodyweight bins and a three-bin rolling average of marginal strength gains, the analysis identifies approximate diminishing-return regions of:

- **Women:** 80–90 kg
- **Men:** 105–120 kg

These are descriptive regions rather than biological cutoffs.

### 3. Lift composition differs primarily through bench and deadlift contribution

Average lift shares show that squat contributes a similar proportion of Total for male and female lifters. The larger difference is in the balance between bench press and deadlift:

- Female lifters have a larger average deadlift share.
- Male lifters have a larger average bench press share.
- Squat share is comparatively similar between groups.

## Methodological Notes

The project uses one best performance per matching Name–Sex combination, which reduces repeated observations but is not a guaranteed unique-athlete identifier. Results are descriptive and should not be interpreted as causal effects of bodyweight or sex.

For the Task 1 scatterplot, a stratified sample of 3,000 male and 3,000 female observations is displayed for responsiveness, while regression statistics are calculated from the complete cleaned analytical dataset.

For Task 2, bodyweight is grouped into 5 kg bins. Bins with fewer than 100 lifters are excluded, and a centered three-bin rolling average is used to reduce noise when evaluating marginal gains.

## Repository Structure

```text
powerlifting-strength-analysis/
├── README.md
├── powerlifting_strength_analysis_portfolio.ipynb
├── visualizations/
│   ├── task1_strength_scaling.html
│   ├── task2_diminishing_returns.html
│   └── task3_lift_composition.html
└── data/
    └── README.md
```

## Running the Notebook

1. Download the OpenPowerlifting dataset from the official OpenPowerlifting data source.
2. Reproduce the filtering and cleaning steps described in the project.
3. Save the cleaned analytical file as `openpowerlifting_usapl_clean.csv`.
4. Install the required Python packages:

```bash
pip install pandas numpy altair jupyter
```

5. Open `powerlifting_strength_analysis_portfolio.ipynb` and run the notebook from top to bottom.

## Interactive Visualizations

The notebook uses Altair dropdown filters and hover tooltips. For the best viewing experience, run the notebook locally or export the final charts as standalone HTML files.

## Limitations

- The analysis is observational and does not establish causality.
- Name–Sex combinations are used to reduce duplicate lifters but are not true athlete IDs.
- Results are specific to the filtered Raw USAPL sample.
- Diminishing-return regions depend partly on analytical choices such as 5 kg bins and rolling-average smoothing.
- Unobserved factors such as training experience, height, body composition, and anthropometry may contribute to the observed patterns.

## Author

Portfolio project demonstrating data cleaning, statistical analysis, interactive visualization, and communication of analytical findings using Python.
