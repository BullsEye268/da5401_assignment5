# DA5401 Assignment 5: Visualizing Data Veracity Challenges in Multi-Label Classification

**Author Name:** Achyutha Munimakula PH21B004

## Assignment Overview

This assignment focuses on utilizing non-linear dimensionality reduction techniques, specifically t-SNE and Isomap, to analyze and visualize data veracity challenges in a multi-label classification context. The dataset used is the Yeast dataset, which involves gene expression levels and their association with multiple functional categories.

The primary objectives are:

- To preprocess the Yeast dataset for visualization.
- To apply t-SNE and Isomap to reduce the dimensionality of the feature space.
- To visually inspect the data for issues like noisy labels, outliers, and hard-to-learn samples.
- To understand the theoretical differences between t-SNE and Isomap and their impact on visualizing data structure.

## Part A: Preprocessing and Initial Setup

1.  **Data Loading:** The Yeast dataset was loaded from an ARFF file into a pandas DataFrame.
2.  **Dimensionality Check:** The dataset contains **2417 data points** and **103 features**.
3.  **Label Selection for Visualization:** To simplify visualization, a new target variable was created by selecting the most frequent single-label class, and the two most frequent multi-label combinations. All other data points were grouped into an "Other" category.
4.  **Scaling:** The feature matrix (X) was standardized using `StandardScaler` to ensure all features contribute equally to the distance-based dimensionality reduction algorithms.

## Part B: t-SNE and Veracity Inspection

- **t-SNE Implementation:** t-SNE was applied to the scaled data with various perplexity values (5, 15, 22, 35, 55, 70) to find the optimal representation. A perplexity of **22** was chosen as it provided the best balance between capturing local and global structures.
- **Visualization:** A 2D scatter plot of the t-SNE embedding was generated, with points colored according to the simplified labels created in Part A.

## Part C: Isomap and Manifold Learning

- **Isomap Implementation:** Isomap was applied to the scaled feature matrix to reduce its dimensionality to 2. The fundamental difference between Isomap and t-SNE is that Isomap aims to preserve global geodesic distances, while t-SNE focuses on preserving local similarities.
- **Visualization:** A 2D scatter plot of the Isomap embedding was created using the same coloring scheme as the t-SNE plot.
- **Comparison and Curvature:** The Isomap visualization revealed a more global, "unrolled" structure of the data manifold compared to the tight, localized clusters of t-SNE. The arching patterns in the Isomap plot suggest a curved and complex data manifold, which can pose challenges for linear classifiers.

## Key Findings

- **t-SNE** was effective at identifying local neighborhood structures and potential clusters, highlighting the separation between the selected prominent classes.
- **Isomap** provided a better representation of the global structure of the data, revealing the underlying manifold's shape.
- The visualizations from both techniques successfully exposed data veracity challenges, such as the mixing of different classes, which would be difficult for simple classifiers to model accurately.
