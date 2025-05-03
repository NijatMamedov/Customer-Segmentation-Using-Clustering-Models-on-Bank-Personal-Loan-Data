# Customer Segmentation Using Clustering Models on Bank Personal Loan Data

🔧 Data Preprocessing Steps
Look at the basics Check descriptive stats to understand the data 📊

Drop what's not needed Remove unnecessary columns 🗑️

Label the categories Convert categorical columns to numbers using Label Encoder 🔢

Find the blanks Check for missing values and handle them accordingly ❓

Outlier check Use the IQR method to cap outliers — but only for columns with more than 2 unique values 🚫📈

Visual check Plot a scatter plot between Income and CCAvg to spot patterns or weirdness 🎯

Standardize it Apply standardization to scale the data ⚖️



🤖 Modeling with K-Means
Start simple Train a KMeans model using default settings 🎯

Find the best number of clusters

Calculate WCSS (within-cluster sum of squares) for 1 to 7 clusters

Calculate Silhouette score to measure quality 🧠

Use KneeLocator to find the "elbow" = best number of clusters (that sweet spot) 💡

Build the final model Use your chosen number of clusters to fit a new KMeans model ✅

Predict clusters Add a new column Segment_KM with the cluster predictions 🔢

Explore the clusters Use groupby('Segment_KM') to analyze the characteristics of each group 🔍

Visualize it! Plot a scatter between Income and CCAvg, color-coded by Segment_KM 🎨


  
🎯 K-Means with PCA – Step-by-Step
Apply PCA on the scaled data Fit a PCA() model and get the explained variance ratio for each principal component 📊

Pick number of components Plot the cumulative explained variance — choose components that together explain at least 80% of the variance (best practice!) ✅

Rebuild PCA Fit PCA(n_components=chosen_number) on the scaled data again to reduce the dimensionality 💡

Understand what each component means Create a dataframe with PCA components (rows) × original variables (columns) to see which component relates to what 🧠

Calculate PCA scores Get the transformed data (let’s call it scores_pca) ➡️ This is the data in the new PCA space

Wrap it up in a new dataframe Create pca_df and rename new PCA features as Variable_1, Variable_2, etc 🧾

Run K-Means again

Calculate WCSS and Silhouette Score for clusters from 1 to 7

Use KneeLocator to find the elbow (best number of clusters) 🎯

Build final KMeans model using that cluster number

Predict clusters Add a new column Segment_KM_PCA with predicted cluster labels 🔢

Merge original and PCA data Combine data and pca_df into one final dataframe 📎

Visualize in 2D Plot a scatter between Variable_1 and Variable_2, colored by Segment_KM_PCA 🎨


🌿 Hierarchical Clustering (Agglomerative)
Draw the dendrogram Use linkage and dendrogram to visualize clusters — it’ll help you decide the number of clusters (centroids) 🌳✨

Fit the model Build the AgglomerativeClustering model using the number of clusters you picked 👌

Predict clusters Add a new column named segment_HC with the predicted cluster labels 🧩

Visualize it Plot a scatter between Income and CCAvg, colored by segment_HC 🎨💼


🧬 Agglomerative Clustering (PCA Version)
Draw the dendrogram Use the pca_df (your PCA-transformed data) to build a dendrogram — this helps you decide how many clusters to use 🌳

Build the model Create the AgglomerativeClustering model using the number of clusters you chose ✅

Predict the clusters Add a new column named segment_HC_PCA with the predicted cluster labels 🧩

Visualize the result Plot a scatter plot between Variable_1 and Variable_2, coloring the points by segment_HC_PCA 🎨
