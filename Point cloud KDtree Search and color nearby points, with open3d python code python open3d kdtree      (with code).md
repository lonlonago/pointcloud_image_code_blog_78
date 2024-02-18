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
