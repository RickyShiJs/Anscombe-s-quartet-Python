# Anscombe-s-quartet-Python

##
This code is to expliain Anscombe's quartet refer to https://en.wikipedia.org/wiki/Anscombe%27s_quartet
To prove why we need data visualization

``` python
var (
# This code is to expliain Anscombe's quartet refer to https://en.wikipedia.org/wiki/Anscombe%27s_quartet
# To prove why we need data visualization
import matplotlib.pyplot as plt
import numpy as np
from sklearn import linear_model
from scipy.stats import pearsonr, tvar
import warnings
warnings.filterwarnings(action="ignore", module="scipy", message="^internal gelsd")

#Anscombe's quartet datasets
data1_X = [10.0,8.0,13.0,9.0,11.0,14.0,6.0,4.0,12.0,7.0,5.0]
data1_Y = [8.04,6.95,7.58,8.81,8.33,9.96,7.24,4.26,10.84,4.82,5.68]

data2_X = [10.0,8.0,13.0,9.0,11.0,14.0,6.0,4.0,12.0,7.0,5.0]
data2_Y = [9.14,8.14,8.74,8.77,9.26,8.10,6.13,3.10,9.13,7.26,4.74]

data3_X = [10.0,8.0,13.0,9.0,11.0,14.0,6.0,4.0,12.0,7.0,5.0]
data3_Y = [7.46,6.77,12.74,7.11,7.81,8.84,6.08,5.39,8.15,6.42,5.73]

data4_X = [8.0] * 7 +[19.0] + [8.0] * 3
data4_Y = [6.58,5.76,7.71,8.84,8.47,7.04,5.25,12.50,5.56,7.91,6.89]

def calc(data_X,data_Y):
    "This function is calculate the mean ,variance, correlation,liner regression"
    print "x mean: ", np.mean(data_X) # Mean for X
    print "x variance: ", tvar(data_X) # Sample Variance for X
    print "y mean: ", np.mean(data_Y) # Mean for Y
    print "y variance: ", tvar(data_Y)  # Sample Variance for Y
    print "x and y correlation coefficient: ", pearsonr(np.array(data_X),np.array(data_Y))[0]

    # Build the liner model liner regression
    regr = linear_model.LinearRegression()
    # fit
    regr.fit(np.array(data_X).reshape(-1, 1), np.array(data_Y).reshape(-1, 1))
    a, b = regr.coef_, regr.intercept_
    print("liner regresstion: y=%.2fx+%.2f" %(a,b))

print "Dataset1 :"
print "==================="
calc(data1_X, data1_Y)
print "\nDataset2 :"
print "==================="
calc(data2_X, data2_Y)
print "\nDataset3 :"
print "==================="
calc(data3_X, data3_Y)
print "\nDataset4 :"
print "==================="
calc(data4_X, data4_Y)

```

##Result
```
Dataset1 :
===================
x mean:  9.0
x variance:  11.0
y mean:  7.50090909091

y variance:  4.12726909091
x and y correlation coefficient:  0.816420516345
liner regresstion: y=0.50x+3.00

Dataset2 :
===================
x mean:  9.0
x variance:  11.0
y mean:  7.50090909091
y variance:  4.12762909091
x and y correlation coefficient:  0.816236506
liner regresstion: y=0.50x+3.00

Dataset3 :
===================
x mean:  9.0
x variance:  11.0
y mean:  7.5
y variance:  4.12262
x and y correlation coefficient:  0.81628673949
liner regresstion: y=0.50x+3.00

Dataset4 :
===================
x mean:  9.0
x variance:  11.0
y mean:  7.50090909091
y variance:  4.12324909091
x and y correlation coefficient:  0.816521436889
liner regresstion: y=0.50x+3.00
```
