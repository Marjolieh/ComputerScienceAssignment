# ComputerScienceAssignment

# Overview
This project addresses the challenge of detecting duplicate products across different web shops. Using scalable techniques such as Locality Sensitive Hashing (LSH) and hierarchical clustering methods. The goal is to reduce the computational cost of product comparisons while maintaining high-quality duplicate detection.

The provided code performs the following key tasks:
* Data cleaning and preprocessing.
* Feature extraction using model words.
* Candidate pair generation using LSH.
* Hierarchical clustering (Single, Average, and Complete Linkage).
* Evaluation of clustering results using metrics like F1-score, Pair Quality, and Pair Completeness.
* Hyperparameter tuning and performance benchmarking.

# Dataset
The dataset used contains 1,624 television product descriptions from four different web shops:
1. Amazon
2. Newegg
3. Best Buy
4. The Nerds

The dataset originally contains 1,624 products. For 12 ModelIDs (26LV2500, 55LW5600, 40E210U, 65LW6500, LEDTV2326, KDL40EX500, PN64D8000F, PN64D7000F, 47LW5600, TC-P60ST30, 42LV3500), the same Web shop appears twice. One of those two observations is removed.

# Each product entry includes:
* Title: product title.
* FeaturesMap: key-value attributes (e.g., "brand: Samsung").
* Shop: source web shop.
* Url: link to the Web page of the product

# File Structure
* Main.py: the main script that runs the entire pipeline.
* README.md: documentation file.
* TVs-all-merged.json: dataset file.

# Code Explanation
Key Functions
1. upload_data(bestandspad):
    * Loads and restructures the dataset from JSON format.
    * Outputs cleaned data with their product number.
2. clean_data(data):
    * Cleans and normalizes product titles and features.
    * Combines titles and features for further processing.
3. lsh_duplicate_detection(cleaned_data, bands):
    * Generates candidate pairs using LSH to minimize comparisons.
    * Uses hash signatures and banding for approximate matching.
4. calculate_dissimilarity_matrix(...):
    * Computes dissimilarities between product pairs based on features, model words, and titles.
5. linkage_clustering(...):
    * Clusters products using hierarchical clustering (Single, Average, Complete Linkage).
6. bootstrapping(...):
    * Evaluates the performance of the clustering pipeline with metrics like F1 measure, F1* measure, Pair Quality, and Pair Completeness.
7. hyperparameter_tuning(...):
    * Finds the best parameters (alpha, beta, epsilon) for optimal clustering performance.

# Metrics and Evaluation
* F1 measure: harmonic mean of Precision and Recall.
* F1* measure: harmonic mean of Pair Quality and Pair Completeness.
* Pair Quality: duplicates found / total comparisons.
* Pair Completeness: duplicates found / total duplicates.

# How to Run
1. Prepare Dataset
    * Download the dataset.
    * Place the TVs-all-merged.json file in the project directory.
2. Run the Pipeline Execute the main script to process the dataset and evaluate performance: python main.py
3. Results
    * Results will be printed to the console.
    * Metrics and visualizations for Single, Average, and Complete Linkage methods will be provided for all band widths provided.


