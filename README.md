# Security assessment of Android mobile applications based on Permission Pairs
This repo contains an official Python implementation of our paper: Recommender System for Secure Mobile Application based on Permission Pairs using Explainable Artificial Intelligence
 ![Image Alt](https://github.com/tejaswivij/Mobile-App-Security-with-Permission-Pairs/blob/main/framework.jpg?raw=true)
 
The figure above illustrates the overall workflow of our proposed system. In this system, permission pairs of apps are treated as features. The system comprises four modules: (i) feature extraction, (ii) feature selection and model building, (iii) evaluation of risk scores for permission pairs, and (iv) the recommendation module. The first three modules act as preliminary steps to obtain relevant inputs that influence the final recommendation.

## **Prerequisites: **

Before running this project, ensure you have the following:
    
OS: Ubuntu 20.04+ / Windows 10+ / macOS (Linux preferred for research workflows)

AndroZoo account for accessing APKs

Python 3.0+

Jupyter Notebook for .ipynb files

## **Module 1: Feature Extraction**

In this module, we collect .apk files from AndroZoo and extracts permissions from the AndroidManifest.xml file of each app.

Next, generate a feature vector representing app behaviour.

### **Collecting APK Files from AndroZoo**

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

Use your API key and the app’s SHA256 hash to download APKs by following the procedure given in  "https://androzoo.uni.lu/api_doc"
