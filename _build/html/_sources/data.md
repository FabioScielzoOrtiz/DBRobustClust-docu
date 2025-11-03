# `data`

## `outlier_contamination`

```
Contaminates with outliers a data matrix.

Parameters (inputs)
----------
X: a pandas/polars series. It represents a statistical variable.
col: the name of a column of `X`.
prop_below: proportion of outliers generated in the below part of `X`. Only used if below = True.
prop_above: proportion of outliers generated in the above part of `X`. Only used if above = True.
sigma: parameter that controls the upper bound of the generated above outliers and the lower bound of the lower outliers.
random_state: controls the random seed of the random elements.

Returns (outputs)
-------
X_new: the resulting variable after the outlier contamination of `X`.
outlier_idx_below: the index of the below outliers.
outlier_idx_above: the index of the above outliers.
```