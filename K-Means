k = 10
# tolerance = 10e-3
# max_iterations = 30

class K_Means:
    
    def __init__(self, k = k, tolerance =  0.0001, max_iterations = 500):
        self.k = k
        self.tolerance= tolerance
        self.max_iterations = max_iterations
        
    
    def fit(self, data):
        
        self.centroids = {}
        
        # initialize the centroids, the first 'k' elements in the dataset will be our initial centroids
        for i in range(self.k):
            self.centroids[i] = data[i]
            
        # begin iterations
        for i in range(self.max_iterations):
            self.classes = {}
            for i in range(self.k):
                self.classes[i] = []
                
            # find the distance between the point and the cluster; choose the nearest centroid
            for features in data:
                distances = [np.linalg.norm(features - self.centroids[centroid]) for centroid in self.centroids]
                classification = distances.index(min(distances))
                self.classes[classification].append(features)
                
            ## re-calculate the cluster centroids
            # previous stores the value of centroids that the previous iteration returned.
            previous = dict(self.centroids)
            
            # average the cluster datapoints to re-calculate the centroids
            for classification in self.classes:
                self.centroids[classification] = np.average(self.classes[classification], axis = 0)
                
            
            # Check whether the algorithm has reached the optimal values of the centroids
            isOptimal = True
            
            for centroid in self.centroids:
                
                original_centroid = previous[centroid]
                curr = self.centroids[centroid]
                
                if np.sum((curr - original_centroid)/original_centroid * 100.0) > self.tolerance:
                    isOptimal = False
                    
            # break out of the loop if the results are optimal
            if isOptimal:
                break
                
    def pred(self, data):
        distances = [np.linalg.norm(data - self.centroids[centroid]) for centroid in self.centroids]
        classification = distances.index(min(distances))
        return classification
    


def main():
    
    k = 'specify k here'
    
    dataset = data.values
    km = K_Means(k)
    km.fit(dataset)
    
    # plotting starts here
#     colors = 10*["r", "g", "c", "b", "k"]
    
#     for centroid in km.centroids:
#         plt.scatter(km.centroids[centroid][0], km.centroids[centroid][1], s = 130, marker = "x")
        
#     for classification in km.classes:
#         color = color[classification]
#         for features in km.classes[classification]:
#             plt.scatter(features[0], features[1], color= color, s= 30)
            
#     plt.show()
    
    
                
if __name__ == "__main__":
    main()
