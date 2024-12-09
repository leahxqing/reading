# Machine Learning

## A General Procedure in Machine Learning

### 1. Data Exploration

- Summary statistics
- Visualizations (correlation matrix, distribution)

### 2. Data Preprocessing

- Types
    - missing data
      
    - noisy data (disturbing)
        - how: binning, regression, clustering
    - outliers (unusual)
    - duplicate data
    - inconsistent data
- Data similarity & dissimilarity
    - Euclidean / Minkowski / Mahalanobis distance
- Proximity
    - simple matching
    - Jaccard coefficients
    - cosine similarity
    - correlation

- Techniques
    - aggregation, sampling
    - dimensionality reduction
        - high dimensional data → sparse
        - techniques: PCA, Singular Value Decomposition, …
    - feature subset selection
        - techniques: brute-force approach
    - discretization (binarization)
        - one-hot: text feature selection
        - numeric data: binning (top-down, unsupervised), histogram analysis (top-down, unsupervised), clustering analysis (unsupervised)
        - supervised techniques: entropy-based discretization
            - the boundary that minimizes the entropy function
            
            **Information Gain after partitioning**
            
            $$
            I(S,T)=\frac{|S_1|}{|S|}Entropy(S_1)+\frac{|S_2|}{|S|}Entropy(S_2)
            $$
            
            **Entropy Function**
            
            $$
            Entropy(S_1)=-\sum_{i=1}^m p_i \log_2 (p_i)
            $$
            
            Notation: $m$ classes, $p_i$ is the probability of class $i$ in $S_1$
            
        - other unsupervised techniques: interval merging by $\chi^2$ analysis (bottom-up), segmentation by natural partitioning (top-down)
    - variable transformation
        - functional form
        - normalization (归一化) → range [0,1], based on min & max
            - distance-based, such as SVM, KNN, or using PCA → Z-score standardization
        - standardization (标准化), based on mean & sd
        
    

### 3. Feature Engineering

- feature selection
- feature extraction (PCA)
- sampling
- clustering

### 4. Train the Model

- Train Test data split
- Compare different models
    - Models: decision-tree-based, rule-based, memory-based reasoning, neural networks, naive Bayes and Bayesian belief networks, support vector machines
    - Association rules: co-occurrence, not causality [frequent itemsets…]

### 5. Evaluation

- Metrics (MAE, MSE, RMSE, $R^2$, Adjusted $R^2$, Cross-Validated $R^2$)
    - MAE: The Mean absolute error represents the average of the absolute difference between the actual and predicted values in the dataset. It measures the average of the residuals in the dataset.
      
        $$
        \frac{1}{n}\sum_{i=1}^n |y_i-\hat{y}_i|
        $$
        
    - MSE: Mean Squared Error represents the average of the squared difference between the original and predicted values in the data set. It measures the variance of the residuals.
      
        $$
        \frac{1}{n}\sum_{i=1}^n (y_i-\hat{y}_i)^2
        $$
        
    - RMSE: RMSE measures the standard deviation of residuals.
      
        $$
        \sqrt{\frac{1}{n}\sum_{i=1}^n (y_i-\hat{y}_i)^2}
        $$
        
    - $R^2$: The coefficient of determination or R-squared represents the proportion of the variance in the dependent variable which is explained by the linear regression model. When $R²$ is high, it represents that the regression can capture much of variation in observed dependent variables. That’s why we can say the regression model performs well when $R²$ is high.
      
        $$
        R^2=1-\frac{SSR}{SST}
        $$
        
        - **SST** (or TSS): the squared differences between the observed dependent variable and its mean.
        - **SSR** (or RSS): the sum of the differences between the predicted value and the mean of the dependent variable.
        - **SSE** (or ESS): the difference between the observed value and the predicted value.
    - Adjusted $R^2$: a modified version of R square, and it is adjusted for the number of independent variables in the model, and it will always be less than or equal to $R²$.
      
        $$
        R^2_{adj}=1-(1-R^2)*\frac{n-1}{n-p-1}
        $$
        
        - $n$: the number of observations in the data
        - $k$: the number of the independent variables in the data
    - Cross-validated $R^2$: the median value or $R^2$ taken from the cross-validation procedure.
- Classification → confusion matrix (accuracy, TPR, TNR, FPR, FNR), cost matrix → P-R curve (precision & recall), F measure
- Performance: learning curve (accuracy ~ sample size), ROC curve (Receiver Operating Characteristics, TPR & FPR)
- Visualization model performance

### 6. Model Development

- Hyperparameter Tuning
    - e.g., using Grid Search CV
- Cross validation: k subsets, k-fold, leave-one-out (LOOCV)
- Ensample learning

### Reference

https://www.kaggle.com/code/marcinrutecki/regression-models-evaluation-metrics

https://www.kaggle.com/code/siddhvr/data-preprocessing-in-ml