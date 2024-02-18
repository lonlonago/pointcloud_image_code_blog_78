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
