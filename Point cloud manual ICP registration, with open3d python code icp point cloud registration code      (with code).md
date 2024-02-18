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
