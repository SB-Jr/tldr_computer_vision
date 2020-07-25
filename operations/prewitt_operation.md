# Prewitt Operation

It is mainly used for edge detection.

It mainly tries to calculate the differential or the approximate gradient at each point.

Mainly used **within an edge deetection algorithm**.

It depends on 2 kernel, one for horizontal and one for vertical gradient calculation. It is thus relatively **more expensize compared to sobel operator**.

## Kernel

It basically uses 3 $\times$ 3 kernels which are convolved with the original image to calculate approximations of the derivatives.

$$
\mathbf{G_x} = \begin{bmatrix}
+1 & 0 & -1 \\
+1 & 0 & -1 \\
+1 & 0 & -1 \\
\end{bmatrix} * \mathbf{A}\ and \ 
\mathbf{G_y} = \begin{bmatrix}
+1 & 0 & -1 \\
+1 & 0 & -1 \\
+1 & 0 & -1 \\
\end{bmatrix} * \mathbf{A}
$$

## Explanation

In simple terms, the operator calculates the *[gradient](https://en.wikipedia.org/wiki/Image_gradient "Image gradient")* of the image intensity at each point, giving the direction of the largest possible increase from light to dark and the rate of change in that direction. The result therefore shows how "abruptly" or "smoothly" the image changes at that point, and therefore how likely it is that part of the image represents an *edge*, as well as how that edge is likely to be oriented.
