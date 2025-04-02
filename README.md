## Title:
Machine Learning approach for predicting Original extract concentration from Near-Infrared Spectroscopy of Beer Samples
## Objective:
Near-Infrared Spectroscopy (NIRS) is a non-destructive analytical technique used to measure a sample’s chemical composition by analyzing its absorption in the near-infrared region. This method relies on molecular vibrations to identify and quantify chemical compounds with minimal sample preparation.<br>
NIRS is widely used for quality control in the food and beverage industry, including beer production. One key application is predicting the original extract (or gravity) of beer, which correlates with the final alcohol content after fermentation. This makes NIRS a valuable tool for monitoring and optimizing the brewing process.
This project aims to develop a machine learning-based model to predict the original extract (gravity) of beer using Near-Infrared (NIR) spectroscopy data. The original extract concentration is a crucial quality parameter in the brewing industry, as it indicates the substrate potential for yeast fermentation and serves as a taxation parameter. By leveraging NIR spectral data, this project builds a predictive model to estimate the extract concentration accurately, enabling real-time quality control and process optimization in brewing.
## Datasets:
The dataset used in this project is sourced from Kaggle and contains Near-Infrared (NIR) spectroscopy data for beer samples.<br>
https://www.kaggle.com/datasets/robertoschimmenti/beer-nir/data <br>
The dataset includes:
* Wavelengths (1100–2500 nm, step size 2 nm): Representing the absorbance spectra of beer samples.
* Original Extract Concentration (% Plato): The target variable, indicating the concentration of extract mainly sugars derived from malt but also contain other soluble material in wort.<br>
Every 1°P produce approximately 0.4% alcohol by volume , 12°P wort produces 5% alcohol depending on the extent to which sugars are fermented out.
   
* 80 Samples: With 576 spectral features per sample, corresponding to different wavelengths.

## Project Workflow
### 1. Data Preprocessing
Load the dataset and check for missing values.

### 2. Exploratory Data Analysis (EDA)
* Spectral Analysis: Visualizing raw spectra to observe absorbance patterns.
* Power Spectral Density (PSD) Analysis: Identifying noise components in spectral data.
* Statistical Insights: Understanding the distribution of original extract values.

### 3. Filtering & Noise Reduction
* Apply Savitzky-Golay filter for smoothing and differentiation.
* Investigate the effects of filtering on spectral data.

### 4. Dimensionality Reduction
* Use Principal Component Analysis (PCA) to reduce high-dimensional spectral data.
* Retain components explaining 95% variance for efficient feature extraction.

### 5. Model Building - Partial Least Squares (PLS) Regression
* Train a PLS regression model, which is well-suited for spectroscopy data.
* Evaluate performance using Mean Squared Error (MSE) and R² Score.
* Analyze PLS regression coefficients to identify significant wavelengths.

### 6.Building a Machine Learning Pipeline
A pipeline is created to streamline the entire process:

* Savitzky-Golay filtering (smoothing & differentiation)
* Standardization (scaling the spectral data)
* Principal Component Analysis (PCA)
* PLS regression model

This pipeline ensures that new data follows the same preprocessing steps as the training data before making predictions.

### 7. Testing on Unseen Data
The model was tested on unseen data (unseen_NIR), which consists of the first 6 rows of the original dataset. This was done to validate the performance of the trained pipeline in predicting the original extract concentration.

### 8. Saving the Model
The trained pipeline was saved using joblib as NIR_model.pkl, allowing it to be used for future predictions without retraining.

## Results :<br>
Model Performance:<br>

Mean Squared Error (MSE): 0.0382
R² Score: 0.9387

### Technologies Used<br>
Python Libraries:<br>

* pandas, numpy (Data Processing)
* matplotlib, seaborn (Visualization)
* scipy.signal (Savitzky-Golay Filtering)
* sklearn.decomposition (PCA)
* sklearn.cross_decomposition (PLS Regression)
* sklearn.pipeline (Machine Learning Pipeline)
* joblib (Model Saving & Loading)

### Future Work
* Implement real-time monitoring system for brewery production.
* Compare PLS regression with neural networks for improved accuracy.
* Explore advanced denoising techniques for better signal processing.

## Contributions
Feel free to contribute! If you find a bug or want to improve the model, open an issue or submit a pull request.
