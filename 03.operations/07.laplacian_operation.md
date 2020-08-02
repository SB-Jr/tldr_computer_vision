# Laplacian Operation

The Laplacian operation uses the laplacian filter. It tries to mimic the Laplacian operation which is the sum of second order derivative of the input function at a given point.

This operation is mainly used to find fine details in an image. An feature with sharp discontinuity will be enhanced

The commonly used filter to produce this effect are:

$$
\begin{bmatrix}
-1 & -1 & -1 \\
-1 & 8 & -1 \\
-1 & -1 & -1
\end{bmatrix} or \begin{bmatrix}
0 & -1 & 0 \\
-1 & 4 & -1 \\
0 & -1 & 0
\end{bmatrix}
$$

But Laplacian operation is very sensitive to noise, so a gaussian filter is first applied to the image and then the Laplacian filter is applied.

This can be done in 1 step by using the LoG filter or the Laplacian of Gaussian filter which clubs both the laplacian and gaussian filter into a single filter which can be then convoluted in 1 step with the input image.

$$
LoG(x,y) = - \frac{1}{\pi \sigma^4}[1 -  \frac{x^2 + y^2}{2\sigma^2}] e^{-\frac{x^2+y^2}{2\sigma^2}}
$$

<img title="" src="file:///home/sbjr/my_workspace/tldr_computer_vision/assets/log.gif" alt="">
