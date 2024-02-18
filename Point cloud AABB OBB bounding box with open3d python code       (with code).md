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
