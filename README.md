# K-means-Clustering-from-Scratch-using-Python

K-Means Clustring aims to partition observations in dataset into clusters where each observation belongs to the cluster with the nearest mean. It is an unsupervised learning algorithm which requires no training data and performs computation on the actual dataset. 

### K-Means Algorithm:

1. Initialize random Centroids: Choose k centroids in random.
2. Calculate Distance: Distance between each of the datapoints with each of the centroids is calculated. This distance metric is used to find the which cluster the points belong to.
3. Calculate new centroids: Find the new values for centroid of newly formed clusters.
4. Stop the iteration: Stop the algorithm when the difference between the old and the new centroids is negligible or less than threshold.

### Canopy Method: This method is used to find the farthest centriods from each other based on their distance.
Step1: A random,initial centroid from the dataset 
Step2: Elucidean distance is calculated between initial centroid and all data points.
Step3: Find the maximum distance and the corresponding data point. This becomes the next centroid
Step4: A if loop is run to repeat step3 till the number of centroids determined equals the number of clusters,k. If the centroid gets repeated, the distance and the corresponding datapoint is deleted and the next maximum distance and its point is the new centroid. 

### Silhouette Method: This method is used to calculate optimum number od clusters k based on "Silhouette Coefficient" (SC). 
It can be calculated with any distance metric, such as the Euclidean distance or the Manhattan distance, This solution uses Euclidean distance.

Assume the data have been clustered, For data point {i} in C{i} 
ai = (1/|Ci| - 1) * Σ d(i,j)
where i ≠ j, j ∈ Ci
    Ci = cluster
    |Ci| = length of that cluster
    |Ci| - 1 is done as distance between i and i should not be included.

bi is the mean inter cluster distance of a point "i" to all points in its neignboring clusters. The minimum distance of these bi is the final bi for the point "i".

bi = min (1 / |Ck|) * Σ d(i,j)

where j ∈ Ck
       |Ck| = length of Ck cluster
    
si is the silhouette value for each point "i".

si = (bi - ai) / max(bi,ai)     if |Ci| > 1
    and
si = 0 if |Ci| = 1

s(k) is the mean of si over all the points for given number of clusters.
Silhouette Coeffecient is the max of sk for the given cluster.

    SC = max(sk)
   
For a predefined value of k clusters of dataset D, SC is calculated for each k. The optimum k is corresponding to Max of SC's.

### Anomaly Detection
1. The small clusters with less than a threshold: A dictionary of clusters as keys and number of points as values is created. A threshold of 1% of the data points in dataset is present in cluster then that cluster is considered as anomalies.
2. Isolated data points not belong to any cluster: Based on above created dictionary, the clusters with single data points are considered as outliers.
3. A data point belongs to a cluster with more than 2 standard deviations: Mean, SD and Mean ± 2*SD for each dimension is calculated at cluster level and points not in this range (95% confidence level) as detected as anomalies.
 
 ![K-Means](https://commons.wikimedia.org/wiki/File:K-means_convergence.gif#/media/File:K-means_convergence.gif)
 
 Souce: https://commons.wikimedia.org/
