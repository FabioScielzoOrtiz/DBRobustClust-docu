# `models`

## `FastKmedoidsGGower`

```
Implements the Fast-K-medoids algorithm based on the Generalized Gower distance.

-------------------
Constructor method
-------------------

Parameters: (inputs)
-----------

n_clusters: the number of clusters.

method: the k-medoids clustering method. Must be in ['pam', 'alternate']. PAM is the classic one, more accurate but slower.

init: the k-medoids initialization method. Must be in ['heuristic', 'random']. Heuristic is the classic one, smarter burt slower.

max_iter: the maximum number of iterations run by k-medodis.

frac_sample_size: the sample size in proportional terms.

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['matching'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

alpha : a real number in [0,1] that is used if `method` is 'trimmed' or 'winsorized'. Only needed when d1 = 'robust_mahalanobis'.

epsilon: parameter used by the Delvin algorithm that is used when computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

n_iters: maximum number of iterations used by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

fast_VG: whether the geometric variability estimation will be full (False) or fast (True).

VG_sample_size: sample size to be used to make the estimation of the geometric variability.

VG_n_samples: number of samples to be used to make the estimation of the geometric variability.

random_state: the random seed used for the (random) sample elements.

y_type: the type of response variable. Must be in ['quantitative', 'binary', 'multiclass'].

-----------
Fit method: 
-----------

Fits the fast k-medoids algorithm to `X`, and `y`, if needed.

Parameters: (inputs)
-----------

X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.

y: a pandas/polars series or a numpy array. Represents a response variable. Is not required.

weights: the sample weights. Only used if provided and d1 = 'robust_mahalanobis'.  

---------------
Predict method:
---------------

Predicts clusters for `X` observation by assigning them to their nearest cluster (medoid) according to Generalized Gower distance.

Parameters: (inputs)
-----------

X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.

Returns: (outputs)
--------

predicted_clusters: the predicted clusters of each observation of `X`.
```

### Example

```python
import pandas as pd
from FastKmedoids.models import FastKmedoidsGGower

data_url = "https://raw.githubusercontent.com/FabioScielzoOrtiz/FastKmedoids-demo/refs/heads/main/data/madrid_houses_processed.csv"

quant_cols = ['sq_mt_built', 'n_rooms', 'n_bathrooms', 'n_floors', 'buy_price']
binary_cols = ['is_renewal_needed', 'has_lift', 'is_exterior', 'has_parking']
multiclass_cols = ['energy_certificate', 'house_type']

p1 = len(quant_cols)
p2 = len(binary_cols)
p3 = len(multiclass_cols)

data = pd.read_csv(data_url)
```
```python
fast_kmedoids = FastKmedoidsGGower(n_clusters=3, method='pam', init='heuristic', max_iter=100, random_state=123,
                                   frac_sample_size=0.01, p1=5, p2=4, p3=2, 
                                   d1='robust_mahalanobis', d2='jaccard', d3='hamming', 
                                   robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20)
fast_kmedoids.fit(X=data_pd) 

fast_kmedoids.labels_
```
```
array([2, 1, 1, ..., 0, 0, 0], dtype=int64)
```

```python
fast_kmedoids = FastKmedoidsGGower(n_clusters=3, method='pam', init='heuristic', max_iter=100, random_state=123,
                                   frac_sample_size=0.01, p1=5, p2=4, p3=2, 
                                   d1='euclidean', d2='sokal', d3='hamming', 
                                   robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20)
fast_kmedoids.fit(X=data_pd) 

fast_kmedoids.labels_
```
```
array([0, 2, 2, ..., 0, 1, 2], dtype=int64)
```

```python
fast_kmedoids = FastKmedoidsGGower(n_clusters=3, method='pam', init='heuristic', max_iter=100, random_state=123,
                                   frac_sample_size=0.01, p1=5, p2=4, p3=2, 
                                   d1='canberra', d2='sokal', d3='hamming', 
                                   robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20)
fast_kmedoids.fit(X=data_pd) 

fast_kmedoids.labels_
```
```
array([1, 0, 0, ..., 0, 2, 0], dtype=int64)
```


## `FoldFastKmedoidsGGower`

```
Implements the K-Fold Fast-K-medoids algorithm based on the Generalized Gower distance.

-------------------
Constructor method
-------------------

Parameters: (inputs)
-----------

n_clusters: the number of clusters.

method: the k-medoids clustering method. Must be in ['pam', 'alternate']. PAM is the classic one, more accurate but slower.

init: the k-medoids initialization method. Must be in ['heuristic', 'random']. Heuristic is the classic one, smarter burt slower.

max_iter: the maximum number of iterations run by k-medodis.

frac_sample_size: the sample size in proportional terms.

p1, p2, p3: number of quantitative, binary and multi-class variables in the considered data matrix, respectively. Must be a non negative integer.

d1: name of the distance to be computed for quantitative variables. Must be an string in ['euclidean', 'minkowski', 'canberra', 'mahalanobis', 'robust_mahalanobis']. 

d2: name of the distance to be computed for binary variables. Must be an string in ['sokal', 'jaccard'].

d3: name of the distance to be computed for multi-class variables. Must be an string in ['matching'].

q: the parameter that defines the Minkowski distance. Must be a positive integer.

robust_method: the method to be used for computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

alpha : a real number in [0,1] that is used if `method` is 'trimmed' or 'winsorized'. Only needed when d1 = 'robust_mahalanobis'.

epsilon: parameter used by the Delvin algorithm that is used when computing the robust covariance matrix. Only needed when d1 = 'robust_mahalanobis'.

n_iters: maximum number of iterations used by the Delvin algorithm. Only needed when d1 = 'robust_mahalanobis'.

fast_VG: whether the geometric variability estimation will be full (False) or fast (True).

VG_sample_size: sample size to be used to make the estimation of the geometric variability.

VG_n_samples: number of samples to be used to make the estimation of the geometric variability.

random_state: the random seed used for the (random) sample elements.

y_type: the type of response variable. Must be in ['quantitative', 'binary', 'multiclass'].

n_splits: number of folds to be used.

shuffle: whether data is shuffled before applying KFold or not, must be in [True, False]. 

kfold_random_state: the random seed for KFold if shuffle = True.
          
-----------
Fit method:
-----------

Fits the fast k-medoids algorithm to `X` (and `y` if needed).

Parameters: (inputs)
-----------

X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.

y: a pandas/polars series or a numpy array. Represents a response variable. Is not required.

weights: the sample weights. Only used if provided and d1 = 'robust_mahalanobis'.  

---------------
Predict method:
---------------

Predicts clusters for `X` observation by assigning them to their nearest cluster (medoid) according to Generalized Gower distance.

Parameters: (inputs)
-----------

X: a pandas/polars data-frame or a numpy array. Represents a predictors matrix and is required. The first p1 predictors must be the quantitative, followed by the p2 binary predictors, and finally the p3 multiclass predictors.
```

### Example

```python
import pandas as pd
from FastKmedoids.models import FoldFastKmedoidsGGower

data_url = "https://raw.githubusercontent.com/FabioScielzoOrtiz/FastKmedoids-demo/refs/heads/main/data/madrid_houses_processed.csv"

quant_cols = ['sq_mt_built', 'n_rooms', 'n_bathrooms', 'n_floors', 'buy_price']
binary_cols = ['is_renewal_needed', 'has_lift', 'is_exterior', 'has_parking']
multiclass_cols = ['energy_certificate', 'house_type']

p1 = len(quant_cols)
p2 = len(binary_cols)
p3 = len(multiclass_cols)

data = pd.read_csv(data_url)
```
```python
kfold_fast_kmedoids = FoldFastKmedoidsGGower(n_clusters=3, method='pam', init='heuristic', max_iter=100, random_state=123,
                                             frac_sample_size=0.1, n_splits=10, shuffle=True, kfold_random_state=123,
                                             p1=p1, p2=p2, p3=p3, d1='robust_mahalanobis', d2='jaccard', d3='hamming', 
                                             robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20,
                                             fast_VG=False, VG_sample_size=1000, VG_n_samples=5)
kfold_fast_kmedoids.fit(X=data) 

kfold_fast_kmedoids.labels_
```
```
array([0, 1, 1, ..., 1, 1, 1])
```

```python
kfold_fast_kmedoids = FoldFastKmedoidsGGower(n_clusters=3, method='pam', init='heuristic', max_iter=100, random_state=123,
                                             frac_sample_size=0.1, n_splits=10, shuffle=True, kfold_random_state=123,
                                             p1=p1, p2=p2, p3=p3, d1='euclidean', d2='sokal', d3='hamming', 
                                             robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20,
                                             fast_VG=False, VG_sample_size=1000, VG_n_samples=5)
kfold_fast_kmedoids.fit(X=data_pd)

kfold_fast_kmedoids.labels_
```
```
array([1, 2, 2, ..., 2, 2, 2])
```

```python
kfold_fast_kmedoids = FoldFastKmedoidsGGower(n_clusters=3, method='pam', init='heuristic', max_iter=100, random_state=123,
                                             frac_sample_size=0.1, n_splits=10, shuffle=True, kfold_random_state=123,
                                             p1=p1, p2=p2, p3=p3, d1='canberra', d2='sokal', d3='hamming', 
                                             robust_method='trimmed', alpha=0.05, epsilon=0.05, n_iters=20,
                                             fast_VG=False, VG_sample_size=1000, VG_n_samples=5)
kfold_fast_kmedoids.fit(X=data_pd) 

kfold_fast_kmedoids.labels_
```
```
array([2, 2, 2, ..., 0, 1, 2])
```