# Interactive Identification of Granular Materials using Force Measurements

This repository provides the dataset associated with the paper "_Interactive Identification of Granular Materials using Force Measurements_", by Samuli Hynninen, Tran Nguyen Le, and Ville Kyrki. Matlab code for feature extraction and classification will be added soon.

# Dataset File Structure
## force_torque_dataset_full.csv
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

data = np.loadtxt('force_torque_dataset_full.csv', delimiter=',')
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
## force_torque_data_all_axes_\<material\>.csv
If you are interested in data from axes other than the x-axis, you can find it in material-specific files. Due to GitHub's file size limitations, all the data cannot be consolidated into a single file. The file structure remains similar to the previous setup, with one recording per row. However, each row now has a length of $1600 \times 6 + 1 = 9601$, representing data sequentially from all sensor axes. The order is as follows: x-axis force, y-axis force, z-axis force, x-axis torque, y-axis torque, z-axis torque. You can load the data using the following scripts:
```matlab
% Matlab

classes = {'dry_peas', 'rice', 'wheat_flour', 'clay_granule', ...
             'oat_flakes', 'potting_gravel', 'sunflower_seeds', ...
             'breadcrumbs', 'macaroni', 'fine_sugar', 'cat_litter'};

class_size = 62;
num_classes = 11;

data = zeros([class_size*num_classes 9601]);

for i = 0:num_classes-1
    st_idx = i*class_size + 1;
    end_idx = st_idx + class_size-1;

    class_data = readmatrix(['force_torque_data_all_axes_' classes{i+1} '.csv']);
    data(st_idx:end_idx, :) = class_data;
end


```


