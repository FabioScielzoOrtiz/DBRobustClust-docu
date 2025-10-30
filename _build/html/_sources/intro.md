# `db_robust_clust`

In the era of big data, data scientists are trying to solve real-world problems using multivariate
and heterogeneous datasets, i.e., datasets where for each unit multiple variables of different
nature are observed. Clustering may be a challenging problem when data are of mixed-type and
present an underlying correlation structure and outlying units.

In the paper ***Grané, A., Scielzo-Ortiz, F.: Fast k-medoids and q-Fold Fast k-medoids: New distance-based clustering algorithms for large mixed-type data, Submitted to Journal of Classification (2024)***, new efficient clustering algorithms able to deal with big data are developed and implemented in a **new Python package**, called `db_robust_clust`, hosted in the official PyPI page https://pypi.org/project/db_robust_clust/. 

Their performance is analyzed in rather complex
mixed-type datasets, whose size go from 35k to 1M, with outlier contamination and different
patterns of underlying correlation structure. The simulation study comprises four computational
experiments, where the stability, accuracy and efficiency of the new algorithms is tested and
compared to existing clustering alternatives. Adjusted accuracy and adjusted rand index are
used to evaluate the goodness of the partitions, and Multidimensional Scaling (MDS)
configurations are given to visualize clustering results.

The package is located in Python Package Index (PyPI), the standard repository of packages for the Python programming language: https://pypi.org/project/db_robust_clust/

```{tableofcontents}
```
