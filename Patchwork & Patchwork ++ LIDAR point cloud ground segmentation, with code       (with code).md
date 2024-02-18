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
