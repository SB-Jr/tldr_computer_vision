# Sobel Operator

Sobel operator performs a 2-D spatial gradient operation on an image to enhance the edges.

Usually works as an **edge detector**.

The operator consists of a pair of 3-by-3 convolution kernels (two for the two perpendicular directions) that are separately applied to an image to produce the approximate gradients for each pixel for detecting edges in vertical and horizontal directions.

## Operation

The operator uses two 3×3 kernels which are convolved with the original image to calculate approximations of the derivatives – one for horizontal changes, and one for vertical. If we define A as the source image, and Gx and Gy are two images which at each point contain the vertical and horizontal derivative approximations respectively, the computations are as follows:

$$
G_x = 
\begin{bmatrix} 
+1 & 0 & -1 \\
+2 & 0 & -2 \\
+1 & 0 & -1
\end{bmatrix} * A
$$

and 

$$
G_y = 
\begin{bmatrix}
+1 & +2 & +1 \\
0 & 0 & 0 \\
-1 & -2 & -1
\end{bmatrix} *A
$$

Since the **Sobel kernels can be decomposed as the products of an averaging and a differentiation kernel**, they compute the gradient with smoothing. Thus G~x~ and G~y~ can be written as: 

$$
G_x = 
\begin{bmatrix}
1 \\
2 \\
1
\end{bmatrix} * 
(\begin{bmatrix}
+1 & 0 & -1
\end{bmatrix}
 * A) \space 
\text{and} \space  G_y = 
\begin{bmatrix}
+1 \\
0 \\
-1 
\end{bmatrix} *
(\begin{bmatrix}
1 & 2 & 1
\end{bmatrix}
 * A)
$$

## Explanation

This operation is based on the principle that the gradient change in case of an edge will be quite high and the change in case of a homogeneous region will be less. To calculate the edges in all direction, it uses 2 kernels, one for horizontal and one for the vertical edges.

To achieve this computation, the it requires to calculate the derivative on each pixel so as to find the sudden change in gradient.

But as the image is a descrete function of the RGB values, we can't define a proper differentiation operation. So as to get the derivatives, we will need to make some assumptions. 

Here the asssumption is that the descrete digital image is the result of quantization of an underlying continuous function and so we can define the differentiation operation on this function and calculate the derivative at each point to get the derivative of the whole image.

[**Sobel operation**](https://en.wikipedia.org/wiki/Sobel_operator) uses both Gaussian smoothing and differentiation.
