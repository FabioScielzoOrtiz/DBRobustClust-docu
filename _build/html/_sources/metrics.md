# `metrics`

## `adjusted_accuracy`

```
Computes the adjusted accuracy as the maximum accuracy  of the ones obtained for all the possible permutations of the cluster labels (`y_pred`).

Parameters (inputs)
----------
y_pred: a numpy array with the predictions of the response.
y_true: a numpy array with the true values of the response.

Returns (outputs)
-------
adj_accuracy: the value of the best accuracy.
adj_cluster_labels: the clusters labels associated to the best accuracy.
```


### Example 

```python
fast_kmedoids = FastKmedoidsGGower(n_clusters=4, method='pam', init='heuristic', max_iter=100, random_state=111,
                                   frac_sample_size=0.01, p1=4, p2=2, p3=2, 
                                   d1='robust_mahalanobis', d2='jaccard', d3='hamming', 
                                   robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20)

fast_kmedoids.fit(X) 

cluster_labels_fast_kmedoids = fast_kmedoids.labels_

adj_accuracy_fast_kmedoids, adj_cluster_labels_fast_kmedoids = adjusted_accuracy(y_pred=cluster_labels_fast_kmedoids, y_true=Y)
```
```python
cluster_labels_fast_kmedoids
```
```
array([0, 2, 2, ..., 2, 1, 1], dtype=int64)
```
```python
adj_cluster_labels_fast_kmedoids
```
```
array([1, 3, 3, ..., 3, 2, 2], dtype=int64)
```
```python
adj_accuracy_fast_kmedoids
```
```
0.8741142857142857
```
