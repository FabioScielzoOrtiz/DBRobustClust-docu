# `metrics`

## `adjusted_accuracy`

```  
Computes the adjusted score (accuracy, balanced accuracy, etc.) as the maximum
score obtained across all possible permutations of the cluster labels (`y_pred`).

Parameters
----------
y_pred : numpy.ndarray
    Predicted cluster labels.
y_true : numpy.ndarray
    True class labels.
metric : callable, default=accuracy_score
    Function to compute the metric. Must accept (y_true, y_pred) and return a float.

Returns
-------
adj_score : float
    The best score obtained across all permutations.
adj_cluster_labels : numpy.ndarray
    The cluster labels permuted according to the best permutation.
```