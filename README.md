# Robust Statistics -- Automated Anomaly Detection

## Objective

I wanted to see how summary statistics and outlier detection methods behave on the California Housing data, and what happens to them when some of the prices are corrupted.

## Methodology

- I loaded the California Housing data (20,640 observations).
- I computed six summary statistics: mean, median, 10% trimmed mean, standard deviation, IQR and MAD. I grouped them by whether extreme values pull them (mean, standard deviation) or leave them mostly alone (median, trimmed mean, IQR, MAD).
- I wrote Tukey Fences by hand, using Q1 - k*IQR and Q3 + k*IQR, to flag price outliers.
- I ran Isolation Forest to flag anomalies using all numeric columns together.
- I compared the rows flagged by Tukey Fences with the rows flagged by Isolation Forest.
- I ran a contamination experiment: I corrupted 5% of the observations and measured how much each summary statistic changed.

## Key Findings

- The two outlier methods flag different observations. Tukey Fences look at one column at a time, while Isolation Forest looks at the whole row, so a row can be flagged by one method and not the other.
- After I corrupted 5% of the data, the mean shifted by [YOUR VALUE]%. The median shifted by only [YOUR VALUE]%.
- The statistics that resist extreme values held up under the 5% corruption. The mean and standard deviation did not.
- A flag from either method does not tell me a row is wrong. I would check whether a flagged value is a data error or a real observation before removing anything.
