# Lorentz-atractor-blind-fault-detection-dataset
A small synthetic benchmark for blind anomaly detectors for industrial time series 

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

The dataset consists of four csv pandas dataframes: 

- `df_train.csv`: The Dataframe of features for training 
- `df_train_labels.csv` : The Dataframe of labels for training 
- `df_test.csv`: The Dataframe of features for test 
- `df_test_labels.csv` : The Dataframe of labels for test
