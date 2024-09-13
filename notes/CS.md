---
title: 'Parametric Regression Analysis'
date: 2024-04-29
permalink: /posts/ml/
tags:
  - Machine Learning
  - Python
---

Reading Note for *Introduction to Computational Science*.

## Overfitting & Underfitting
- Cross Validation
    - Hold-out
    - K-fold
- How to solve the overfitting issue
    - Increase observations
    - Feature selection
    - Dimension decreasing
        - e.g.: Principal Component Analysis (PCA)
    - Regularization
        - Ridge
        - Lasso


## OLS
- Loss function
    
    $$
    RSS=\sum_{i=1}^n(y_i-\beta_0-\sum_{j=1}^p\beta_jx_{ij})^2
    $$
    
- Matrix form：
  - Loss function (the object function to minimize)
      
      $$
      \hat{\beta}=\mathbf{argmin}_{\beta}||\mathbf{X}\beta-\mathbf{y}||_2^2
      $$
    
- Analytical solution：
    
    $$
    \hat{\beta}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}
    $$
        

## Ridge Regression

- Loss function
    
    $$
    \sum_{i=1}^n(y_i-\beta_0-\sum_{j=1}^p\beta_jx_{ij})^2+\lambda\sum_{j=1}^p\beta_j^2=RSS+\lambda\sum_{j=1}^p\beta_j^2
    $$
    
- Matrix form：
    
    $$
    \hat{\beta}=\mathbf{argmin}_{\beta}||\mathbf{X}\beta-\mathbf{y}||_2^2+||\beta^p||_2^2
    $$
    
- $$ \beta^p $$ denotes the $$p$$ dimensional vector after regularization
    - A shrinkage penalty $$ (\lambda\sum_{j=1}^p\beta_j^2) $$, $$ \lambda $$ is the hyperparameter
    - the square root of the shrinkage penalty is L2 norm
- Ridge Regression mainly overcomes the multicollinearity issue of OLS
    - High correlation: features in $$ \mathbb{X} $$ are highly correlated (high VIF: Variance Inflation Factor)
    - Analytical solution:
        
        $$
        \hat{\beta}=(\mathbf{X}^T\mathbf{X}+\lambda\mathbf{I}^p)^{-1}\mathbf{X}^T\mathbf{y}
        $$
        
- Parameter Tuning — $$ \lambda $$
    - Ridge Trace
- Example: Residents’ Welfare
    
    ```python
    import pandas as pd
    import numpy as np
    # read csv files x, y
    # skelearn model: train_test_split
    from skelearn.model_selection import train_test_split
    X_train, X_test, y_train, y_test = train_test_split(x,y, test_size=.3. random_state=728)
    ```
## LASSO

- Loss function

$$
\sum_{i=1}^n(y_i-\beta_0-\sum_{j=1}^p\beta_jx_{ij})^2+\lambda\sum_{j=1}^p|\beta_j|=RSS+\lambda\sum_{j=1}^p|\beta_j|
$$

- Matrix form

$$
\hat{\beta}=\mathbf{argmin}_{\beta}||\mathbf{X\beta-y}||_2^2+||\beta^p||_2^2
$$

- $$ \lambda\sum_{j=1}^p|\beta_j| $$
: L1 norm
- Lasso will also induce the shrinkage of the coefficient to be 0. The larger the $$\lambda$$, the greater effect of shrinkage.
- The difference between ridge and lasso:
    - The coefficient won't be exactly 0 in ridge while lasso could attain this $$\rightarrow$$ to get a **Sparse Model**
  
## Elastic Net

- Loss Function

$$
RSS+\lambda((1-\alpha)\sum_{j=1}^p\beta_j^2+\alpha\sum_{j=1}^p|\beta_j|)
$$

- Matrix Form

$$
\hat{\beta}=\mathbf{argmin}_{\beta}||\mathbf{X\beta-y}||_2^2+\lambda(1-\alpha)||\beta^p||_2^2+\lambda\alpha||\beta^p||_2^2
$$

- $$ \alpha=0$$: rigde，$$ \alpha=1 $$: lasso
