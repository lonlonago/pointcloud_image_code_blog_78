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
