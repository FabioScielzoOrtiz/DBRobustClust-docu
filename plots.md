# `plots`

## `clustering_MDS_plot_one_method`


### Example

```python
X, Y = make_blobs(n_samples=35000, centers=4, cluster_std=[2,2,2,3], n_features=8, random_state=123)
X = pd.DataFrame(X)      
X.columns = [f"X{i}" for i in range(1, X.shape[1]+1)]

# Se convierten dos variables cuantitativas a binarias, y otras dos a multiclase, discretizandolas.
X['X5'] = pd.cut(X['X5'], bins=[X['X5'].min()-1, X['X5'].mean(), X['X5'].max()+1], labels=False)
X['X6'] = pd.cut(X['X6'], bins=[X['X6'].min()-1, X['X6'].mean(), X['X6'].max()+1], labels=False)
X['X7'] = pd.cut(X['X7'], bins=[X['X7'].min()-1, X['X7'].quantile(0.25), X['X7'].quantile(0.50), X['X7'].quantile(0.75), X['X7'].max()+1], labels=False)
X['X8'] = pd.cut(X['X8'], bins=[X['X8'].min()-1, X['X8'].quantile(0.25), X['X8'].quantile(0.50), X['X8'].quantile(0.75), X['X8'].max()+1], labels=False)   

X_outliers, outliers_idx_X1 = outlier_contamination(X, col_name='X1', prop_above=0.1, sigma=3, random_state=123)
X_outliers, outliers_idx_X2 = outlier_contamination(X_outliers, col_name='X2', prop_below=0.1, sigma=5, random_state=123)

X = X_outliers.copy()
```
```python
mds = MDS(n_components=2, dissimilarity='precomputed', random_state=111) 

fastGGower = FastGGowerDistMatrix(frac_sample_size=0.03, random_state=111, p1=4, p2=2, p3=2, 
                                  d1='robust_mahalanobis', d2='sokal', d3='hamming', 
                                  robust_method='trimmed', alpha=0.08)
fastGGower.compute(X)

X_mds = mds.fit_transform(fastGGower.D_GGower)
```

```python
fast_kmedoids = FastKmedoidsGGower(n_clusters=4, method='pam', init='heuristic', max_iter=100, random_state=111,
                                   frac_sample_size=0.01, p1=4, p2=2, p3=2, 
                                   d1='robust_mahalanobis', d2='jaccard', d3='hamming', 
                                   robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20)

fast_kmedoids.fit(X) 

cluster_labels_fast_kmedoids = fast_kmedoids.labels_
```
```python
clustering_MDS_plot_one_method(X_mds=X_mds, y_pred=cluster_labels_fast_kmedoids[fastGGower.sample_index], 
                               y_true=None, title="MDS visualization of clustering results", 
                               accuracy=None, time=None, 
                               figsize=(8,7), bbox_to_anchor=(1,1), 
                               title_size=13, title_weight='bold', 
                               points_size=45, title_height=1, 
                               save=False, legend_size=9)
```
![My Local Image](images/clustering_MDS_plot_one_method.png "Example Image")



```python

```
```

```

## `clustering_MDS_plot_multiple_methods`


### Example


```python

```
```

```


```python

```
```

```