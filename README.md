# QuantComps
Utilities and tools for (quantitative) metric comparisons in MRI

Example usage for computing element-wise correlation across 6 metrics. Outputs an hdf5 file with correlation matrix of type n_element X n_element where the upper diagonal is filled and lower is mostly 0s (also contains overlap of varying size depending on the size used for chunking)

```
import numpy as np
import pandas as pd
import quantcomps as qcomps

d = np.random.rand(50000,6) #the data, 50,000 elements with 6 measurements in each element
df = pd.DataFrame(d,columns=['1','2','3','4','5','6']) #convert to pandas dataframe to allow faster computation of zscores (not sure if this ends up being super useful in the end)
res = qcomps.calc_corrs(df,data_dir = '.',out_fname_tail='50k') #uses a manual dot product correlation computation on zscored data (across metrics, not elements)
```
