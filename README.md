# Lorentz-attractor-blind-fault-detection-dataset
A small synthetic benchmark for blind anomaly detectors for industrial time series 

[![DOI](https://zenodo.org/badge/650177436.svg)](https://zenodo.org/badge/latestdoi/650177436)

## Description of the dataset 

This is a synthetic dataset that might be used to challenge **Blind anomaly detector for time series **

The dynamical system for which the dataset is created is the famous Lorentz attractor which is governed by the following set of Ordinary Differential Equations:

$$
\begin{align}
\dot x_1&=\sigma(x_2-x_1) \\
\dot x_2&=x_1({\color{red} \rho}-x_3)-x_2 \\
\dot x_3&=x_1x_2-{\color{blue} \beta} x_3 
\end{align} 	
$$

where $\sigma$, $\rho$ and $\beta$ are the parameters that might be affected by unpredictable changes one would like to detect thanks to the anomaly detector using the two measurement sensors defined by $s_1=x_1$ and $s_2=x_3$. The raw version of the time series is given in the figure below:

<p align="center">
  <img src="https://github.com/mazenalamir/lorentz-atractor-blind-fault-detection-dataset/blob/main/images/fig_lorentz_0.png" width="50%">
</p>

Note that green regions corresponds to nominal parameters (normalized values = 1) while the red regions correspond to changes in the values of the parameters to be detected by the anomalies detector. 

The dataset consists of four csv pandas dataframes: 

- `df_train.csv`: The Dataframe of features for training 
- `df_train_labels.csv` : The Dataframe of labels for training 
- `df_test.csv`: The Dataframe of features for test 
- `df_test_labels.csv` : The Dataframe of labels for test

In order to read the dataframe, use the following pandas command 

```python 
import pandas as pd
df_train = pd.read_csv('df_train.csv', inde_col=0)
```

The following images shows the columns in the `df_train` and `df_test_label` dataframes

- `df_train`

=============

<p align="left">
  <img src="https://github.com/mazenalamir/lorentz-atractor-blind-fault-detection-dataset/blob/main/images/df_train.png" width="30%">
</p>

- `df_test_label`

=============

<p align="left">
  <img src="https://github.com/mazenalamir/lorentz-atractor-blind-fault-detection-dataset/blob/main/images/df_test_labels.png" width="20%">
</p>

### Important information on test data

> Please note that the training data lies in the first block of the `df_test`dataset. If you want to draw statistic, it is important to know that the first 6-th part of the test data is simply the training data. It is therefore expected that you get *nice* results on this part of the test data.

## Benchmark Description

Use the training dataset `df_train`in order to fit your anomalies detector. 
Use the test dataset `df_test`to predict the presence or not of anomalies in dataset. 
Compare your prediction to the column `label`of the dataframe `df_test_labels`. Note that `0`represent normal data while `1`represent anomalous data. 
The prediction can be performed over a moving window spanning the time series or using point-wise prediction. 
The nominal benchmark involves only the columns `x1`and `x3`of the dataframe, but you might feel free to use less or more columns. 
The other columns in the `df_test_labels` are provided as extra columns that explains the origin of the anomalies. 

If interested in having more rich set of anomalies values, please contact me. 





