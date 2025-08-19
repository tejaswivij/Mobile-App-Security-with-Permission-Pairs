# Security assessment of Android mobile applications based on Permission Pairs
This repo contains an official Python implementation of our paper: Recommender System for Secure Mobile Application based on Permission Pairs using Explainable Artificial Intelligence
 ![Image Alt](https://github.com/tejaswivij/Mobile-App-Security-with-Permission-Pairs/blob/main/framework.jpg?raw=true)
 
The figure above illustrates the overall workflow of our proposed system. In this system, permission pairs of apps are treated as features. The system comprises four modules: (i) feature extraction, (ii) feature selection and model building, (iii) evaluation of risk scores for permission pairs, and (iv) the recommendation module. The first three modules act as preliminary steps to obtain relevant inputs that influence the final recommendation.

## **Prerequisites: **

Before running this project, ensure you have the following:
    
OS: Ubuntu 20.04+ / Windows 10+ / macOS (Linux preferred for research workflows)

AndroZoo account for accessing APKs

Python 3.0+

Pandas

NumPy

Jupyter Notebook for .ipynb files

## **Module 1: Feature Extraction**

In this module, we collect .apk files from AndroZoo and extract permissions from the AndroidManifest.xml file of each app.

Next, generate a feature vector representing app behaviour.

### **Collecting APK Files from AndroZoo and creating a feature vector**

AndroZoo is a growing collection of millions of Android applications collected from various sources (e.g., Google Play, APKPure, etc.). You can download APK files for research purposes after getting access.

**Step 1: Request Access**

Visit the AndroZoo access page.

Fill in the request form with:

Your name and institutional affiliation.

Research purpose (must be academic/research use only).

Once approved, you will receive an API key via email.

**Step 2: Get the APK List**

AndroZoo provides a metadata file (androzoo.csv) that contains information about all available apps:

SHA256 hash, Package name, App markets (e.g., Google Play), Version, size, and more

**Step 3: Download APKs**

Use your API key and the app’s SHA256 hash to download APKs by following the procedure given in  "https://androzoo.uni.lu/api_doc", and save them in a folder.

**Step 4: Creating feature vector from .apk files**

Use the ** Feature Extraction.ipynb **to create a CSV file containing feature vectors of all apps.

## **Module 2: Feature Selection and Model Building**

In this module, we trained a LightGBM classifier using K-Fold cross-validation to ensure robust evaluation across different data splits.  In addition, we analysed and identified significant permission pairs that contribute to app behaviour, which are used as important features for classification. The best-performing model (highest accuracy) was then saved for future use. LightGBM offers a better trade-off between accuracy and model complexity on the combined dataset, making it a suitable choice for this task.

Use the **permpair_cross_validation.ipynb** to check model performance with other models, and **permpair_cross_validation.ipynb** for significant feature selection.

## **Module 3: Risk Score Evaluation**

In this module, SHAP values are used to assign weights to the selected features. Based on these weights, risk scores are calculated for each permission pair, and the results are stored in a risk score database for later use.

Use **significant feature selection_ risk score calculation.ipynb** to find the risk scores for significant permission pairs.

## **Module 4: App Recommendation**

Step 1: Collect the IDs and names of apps from the **Google Play Store** for a particular category of apps

Step 2: Collect .apk files of the app from APKPure (https://apkpure.com/), a well-established third-party app marketplace that provides verified .apk files for both the latest and older versions of Android applications.

Step 3: Use **Feature Extraction.ipynb** to create a CSV file containing feature vectors of all apps.

Step 4: For a given app category, the trained LGBM classifier labels apps as benign or malware.

For benign apps:

Computes a total risk score using the Module 3 database.

Ranks apps based on risk score.

Recommends the top r safest apps in the same category.


