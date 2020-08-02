# Basic Definitions in Computer Vision

## CV Tasks

- **Object Recognition**
  
  This activity relates to the classification of an image whether it has a certain object or not. This activity has not other tasks to accomplish like at what location the object is or how many objects are present etc.

- **Object Detection**
  
  This tasks not only tells which objects are present in an image but also specifies the location of the objects. In most cases a bounding boxes are used to specify the location of the objects.

## Mathematics

- **Derivative**
  
  The derivative of a function $f(x_1,x_2,x_3,...)$ at a point $(a_1,a_2,a_3,...)$ is the rate of change of the function at that point. In other terms we can say that the derivative of a function at a specific point is the slope of the tangent line at that point drawn on the function.
  
  *It is a scalar quantity.*

- **Directional Derivative**
  
  The instantaneous rate of change of a function $f(x_1,x_2,x_3,...)$ in the direction of an unit vector $\vec{u}$.
  
  *It is a scalar quantity.*

- **Gradient**
  
  It points in the direction of the greatest rate of increase of a function , containing all the partial derivative information of a multi-variable function.
  
  *It is a vector quantity.*

## Image Processing

- **Image Gradient Vector**
  
  Metric for every individual pixel, containing the pixel color changes in both x-axis and y-axis.
  
  $$
  \Large
\begin{equation}
\triangledown f(x,y) =
\begin{bmatrix}
g_x \\
g_y
\end{bmatrix}
= 
\begin{bmatrix}
\frac{\partial f}{\partial x} \\
\frac{\partial f}{\partial y}
\end{bmatrix}
= 
\begin{bmatrix}
f(x+1,y) - f(x-1,y) \\
f(x,y+1) - f(x,y-1)
\end{bmatrix}
\end{equation}
  $$

Here $f(x,y)$ is the pixel value at location $(x,y)$

It is aligned with the gradient of a continuous multi-variable function, which is a vector of partial derivatives of all the variables.

Here the partial derivative is calculated as the color difference between the adjacent pixels.

Attributes of image gradient:

- **Magnitude**: is the L2 norm of the vector $g = \sqrt{g_x^2 + g_y^2}$
- **Direction**: is the arc-tangent of the ratio between the partial derivatives on 2 directions, $\large \theta = artan(\frac{g_y}{g_x})$

But doing this process pixel wise is too slow and thus can be speed up by using the convolution operator on the entire image matrix using a convolution kernel.

so lets say the kernel is **G** and the image matrix is **A** then, the convolution operator is:

$ G*A$

## Image Segmentation Definitions

- **Internal Difference**
  
  $Int(C) = max_{e \in MST(C,E)} w(e)$ 
  
  Where $MST$ is the minimum spanning tree of the components. A component C can still remain connected even when we have removed all the edges with weight < $Int(C)$

- **Difference between 2 components**
  
  $\large Dif(C_1,C_2) = min_{v_i \in C_1, v_j \in C_2, (v_i,v_j) \in E}w(v_i, v_j)$
  
  $\large Dif(C_1,C_2) = \infin$   if there is no edge in between

- **Minimum Internal Difference**
  
  $M\ Int(C_1,C_2) = min(Int(C_1) + \tau(C_1), Int(C_2) + \tau(C_2))$ where $\tau(C) = \frac{k}{|C|}$

# Reference

[1]:https://lilianweng.github.io/lil-log/2017/12/15/object-recognition-for-dummies-part-2.html