# Interactive Identification of Granular Materials using Force Measurements

This repository provides the dataset associated with the paper "_Interactive Identification of Granular Materials using Force Measurements_", by Samuli Hynninen, Tran Nguyen Le, and Ville Kyrki. Matlab code for feature extraction and classification will be added soon.

# Dataset File Structure
Each recorded force-torque signal consists of 1600 samples, representing a 3.2-second recording at a sample rate of 500 Hz. The dataset file contains one recording per row, with the corresponding class number as the last element in that row. To access the n-th recording and its class, use the following:

```matlab
% Matlab

data = readmatrix('force_torque_dataset_full.csv');
sample = data(n, 1:1600);
class_number = data(n, 1601);
```
or

```python
# Python

import numpy as np

data = np.loadtxt('force_torque_dataset_full.csv')
sample = data(n-1, 0:1600)
class_number = data(n-1, 1600)
```

The class-material correspondence table is as follows:

```
1  : Dry peas
2  : Rice
3  : Wheat flour
4  : Clay granule
5  : Oat flakes
6  : Potting gravel
7  : Sunflower seeds
8  : Breadcrumbs
9  : Macaroni
10 : Fine sugar
11 : Cat litter
```

