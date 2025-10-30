# Quick start

## Requirements

### General requirements 

```python
# Development Python Version: 3.12.0
DBRobustClust 
PyDistances
polars
pandas
numpy<=1.26.4
scikit-learn-extra
setuptools
tqdm
PyMachineLearning
pyarrow
matplotlib
seaborn
```

### `models` requirements

```python
PyDistances
polars
pandas
numpy<=1.26.4
scikit-learn-extra
setuptools
tqdm
matplotlib
seaborn
```

### `metrics` requirements 

```python
numpy
```


### `plots` requirements

```python
polars 
numpy
matplotlib
seaborn
```

### `data` requirements

```python
polars
numpy
PyMachineLearning
scikit-learn
```


## Installation

```python
pip install DBRobustClust 
```

To see the available versions of the package go to the release history at PyPi: https://pypi.org/project/DBRobustClust /#history


## Example

```python

import pandas as pd
from DBRobustClust .models import FoldFastKmedoidsGGower

data_url = "https://raw.githubusercontent.com/FabioScielzoOrtiz/DBRobustClust -demo/refs/heads/main/data/madrid_houses_processed.csv"

quant_cols = ['sq_mt_built', 'n_rooms', 'n_bathrooms', 'n_floors', 'buy_price']
binary_cols = ['is_renewal_needed', 'has_lift', 'is_exterior', 'has_parking']
multiclass_cols = ['energy_certificate', 'house_type']

p1 = len(quant_cols)
p2 = len(binary_cols)
p3 = len(multiclass_cols)

data = pd.read_csv(data_url)

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



