 Three normal vector estimation methods (K-nearest neighbor estimation, radius nearest neighbor estimation, mixed search estimation) 

 The difference is only that the method of searching for the nearest neighbor points is slightly different, but in fact the difference is not big; 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574630998
  ```  


--------------------------------------------------------------------------------

This is really too simple, I will directly on the code, including X, Y, Z three directions of through filtering, and can be filtered according to the yaw angle range; 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574647022
  ```  


--------------------------------------------------------------------------------

These two filters are very useful and must be used well. 

 Radius filtering: 

 The radius filter is relatively simple and crude. Draw a circle with a point as the center to calculate the number of points that fall in the circle. When the number is greater than a given value, the point is retained, and if the number is less than a given value, the point is rejected. This algorithm runs fast, and the points left by sequential iterations must be the densest, but the radius of the circle and the number of points in the circle need to be manually specified; 

 Statistical filtering: 

 First Scan: For each point, we calculate the average distance from it to all N points in its vicinity. Calculate the mean and standard deviation of these distances 

 Second scan: Points with an average distance outside the M standard deviations range (defined by the global distance mean and variance) can be defined as outliers and removed from the dataset. 

 The code is very simple, just two lines: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957468851
  ```  


--------------------------------------------------------------------------------

 The patchwork is divided into three parts, CZM, R-GPF, and GLE. 

 CZM (concentric region model): can be understood as a model of region segmentation with non-uniform or multi-resolution; most multiplanar-based methods are based on the assumption that the observable world may not be flat. Therefore, the ground plane estimate should be pushed back by assuming that the possible non-flat world has small patches or bins and that the ground can indeed be flat within that region. 

  R-GPF (Regional Ground Plane Fitting): Each bin is ground estimated by R-GPF and then ground merged. In this article, Principal Component Analysis (PCA) is used instead of RANSAC. 

  GLE (ground likelihood estimation): A regional probability test for binary classification to determine whether it is the actual ground. 

 ![avatar]( 8439090989674906989da04cbbe14fd1.png) 

 The CZM shown in the following figure is actually a polar coordinate grid: 

 ![avatar]( e50d9d6330ca4e319d60ab6ecbd3781f.png) 

 Patchwork ++: An extension of Patchwork. 

 Some ground segmentation methods require fine-tuning the parameters according to the environment, which is very time-consuming and labor-intensive. In addition, even if the parameters are properly adjusted, there may still be a partial segmentation problem, which means that the ground segmentation in some areas fails. Patchwork ++ adaptively calculates the appropriate parameters using adaptive ground likelihood estimation (A-GLE). Partial undersegmentation problems are alleviated by using temporal ground recovery (TGR). 

 Two new outlier suppression modules, Reflected Noise Removal (RNR) and Regional Vertical Plane Fitting (R-VPF), are proposed to prevent the hypothesis from failing due to noise suppression or non-grounding 

 ![avatar]( fe59d185695744ee8f3d41951d674d80.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574631961
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574631961
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574631961
  ```  


--------------------------------------------------------------------------------

Today, I spent some time looking at the relevant algorithms and took a simple note. 

 The specific implementation method of the Euclidean algorithm is roughly as follows: 

 1 Find a point p10 in space, there is kdTree to find the n points closest to him, and judge the distance from these n points to p. Put points p12, p13, p14.... with distances less than the threshold r in class Q 

 2 Find a bit of p12 in Q (p10), repeat 1 

 3 Find a point in Q (p10, p12), repeat 1, find p22, p23, p24.... all put in Q 

 4. When Q can no longer add new points, the search is completed. 

 Looking at the PCL code, the process is very simple, and you can also see the process. The clustering code is as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574696284
  ```  


--------------------------------------------------------------------------------

![avatar]( 8593d61fe6214a479872d5abff3bbe17.png) 

 AABB bounding box: AABB bounding box is a bounding box aligned with the coordinate axis, with good simplicity. 

 Poor compactness (especially for thin and elongated objects placed diagonally, AABB is used. 

 This will leave a large corner gap, resulting in a large number of unnecessary bounding box intersecting tests.

OBB Bounding Box: Oriented Bounding Box;

The compactness of OBB collision detection method is better. 

It can greatly reduce the number of bounding boxes participating in the intersection test. 

Therefore, the overall performance is better than that of AABB and enclosing ball, and the degree of real-time performance is higher.

After the object rotates, it is sufficient to perform the same rotation on the OBB.

Therefore, for collision detection between rigid bodies, OBB is a better choice.

OBB is closer to objects than AABB, which can significantly reduce the number of enclosures

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574679043
  ```  


--------------------------------------------------------------------------------

 The existing ICP registration algorithm is centrally encapsulated.

And it integrates common operations before and after registration.

Adapts numpy arrays. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574671073
  ```  


--------------------------------------------------------------------------------

 Add up the xyz of each point and divide by the number of points to get the centroid of the point cloud.

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957469410
  ```  


--------------------------------------------------------------------------------

 Realized non-blocking point cloud visualization operation 

 ![avatar]( 5861a0c3d7b1453981be71d6839ae009.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574651580
  ```  


--------------------------------------------------------------------------------

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574629785
  ```  


--------------------------------------------------------------------------------

Find the edge point by computing the layer of each point, similar to the method of finding the outline of the image in the image 

 Useful for simplifying subsequent computational steps or extracting point cloud features 

 The results are as follows; 

 ![avatar]( 3d793efdf9a34ce3a28fc531cad177fc.png) 

 The code is as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957465970
  ```  


--------------------------------------------------------------------------------

 Fix a color for the point cloud through the code. 

 ![avatar]( caa6afd3d8d6467896b81aa9bf0bbb73.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574657627
  ```  


--------------------------------------------------------------------------------

 Ground removal by ground fitting

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574653123
  ```  


--------------------------------------------------------------------------------

 The point cloud is projected onto the ground.

According to the points within each region

Elevation changes, and point count

Determine classified ground points and obstacle points

The height of the ground area changes little,

The height of the obstacle area varies greatly.

Mainly based on this feature 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574644061
  ```  


--------------------------------------------------------------------------------

Open3D uses FLANN to build KDTrees for fast nearest neighbor retrieval.

Function search_knn_vector_3d returns the indices of the k nearest neighbors of the anchor

List and color these adjacent points blue. Please note that for batch access to point colors

We convert pcd.colors to a numpy array and broadcast all selected points in blue. 

We skip the first index because it is the anchor itself.

Similarly, we can use search_radius_vector_3d query for small distance from anchor

Go to all points of the given radius and color them green. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574649703
  ```  


--------------------------------------------------------------------------------

 ![avatar]( 7f9333dff82545ca97a4883962f9d3af.png) 

 If the angle of rotation between the point clouds is very large, or the translation distance is very large,

Regular registration will be invalid. At this time, you can consider manually giving the registration algorithm an initial value.

The specific method is to manually select at least three points on two point clouds.

These three points have the same position on the two point clouds,

It is equivalent to manually informing the registration algorithm of the mapping relationship between the two point clouds.

It should be noted that the selection of three points should not be on a line.

As far away as possible,

It is best to form a large triangle.

The selected locations should be as consistent as possible on the two point clouds. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957463088
  ```  


--------------------------------------------------------------------------------

 By surface triangulation mesh reconstruction of the point cloud, the point cloud map can be made lighter, and the amount of map data can be further reduced by using triangular patch vertices with different sampling rates for ground (red) and non-ground (blue). 

 ![avatar]( a4e1575737fe4a3398770aa9cd858ee7.png) 



--------------------------------------------------------------------------------

![avatar]( f2aa5aa7d67341778d243593e6147110.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574661497
  ```  


--------------------------------------------------------------------------------

Three normal vector estimation methods (K-nearest neighbor estimation, radius nearest neighbor estimation, mixed search estimation)

The difference is only that the method of searching for the nearest neighbor points is slightly different, but in fact the difference is not big;

The actual impact is whether the setting of parameters is reasonable

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574614736
  ```  


--------------------------------------------------------------------------------

 ![avatar]( 70eeb434786e4947893e44ba0267215a.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574657910
  ```  


--------------------------------------------------------------------------------

