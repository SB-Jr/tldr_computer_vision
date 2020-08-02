# Common Image Processing Kernels

## Edge Detection Kernels

## Prewitt Operator

Rather than only relying on four directly adjacent neighbors, the Prewitt operator utilizes eight surrounding pixels for smoother results.

$$
\mathbf{G}_x = \begin{bmatrix} -1 & 0 & +1 \\ -1 & 0 & +1 \\ -1 & 0 & +1 \end{bmatrix} \ast \mathbf{A} \text{ and } \mathbf{G}_y = \begin{bmatrix} +1 & +1 & +1 \\ 0 & 0 & 0 \\ -1 & -1 & -1 \end{bmatrix} \ast \mathbf{A} 
$$

## Sobel Operator

To emphasize the impact of directly adjacent pixels more, they get assigned with higher weights.

$$
\mathbf{G}_x = \begin{bmatrix}
-1 & 0 & +1 \\
-2 & 0 & +2 \\
-1 & 0 & +1
\end{bmatrix} \ast \mathbf{A} \text{ and }
\mathbf{G}_y = \begin{bmatrix}
+1 & +2 & +1 \\
0 & 0 & 0 \\
-1 & -2 & -1
\end{bmatrix} \ast \mathbf{A}
$$

### Kirsh

It is a non-linear edge detection kernel. This operation takes a mask as input and rotates it in 45$\degree$ for all 8 angles(N, NW, W, SW, S, SE, E, NE).

$$
\mathbf{G}^{(1)} = \begin{bmatrix}
+5 & +5 & +5 \\
-3 & 0 & -3 \\
-3 & -3 & -3
\end{bmatrix}, \mathbf{G}^{(2)} = \begin{bmatrix}
+5 & +5 & -3 \\
+5 & 0 & -3 \\
-3 & -3 & -3
\end{bmatrix}, \mathbf{G}^{(3)} = \begin{bmatrix}
+5 & -3 & -3 \\
+5 & 0 & -3 \\
+5 & -3 & -3
\end{bmatrix}, ....
$$

## Bluring Kernels

### Box Blur/Smooth Blur

It is a basic bluring kernel.

$$
k_{Box} = \frac{1}{9}\begin{bmatrix}
1 & 1 & 1 \\
1 & 1 & 1 \\
1 & 1 & 1
\end{bmatrix}
$$

### Gaussian Blur

Uses the no generated from a 2 variable gaussian distribution.

eg: $5 \times 5$ kernel:

$$
K_{Gaussian} = \begin{bmatrix}
0.003765 & 0.015019 & 0.023792 & 0.015019 & 0.003765 \\
0.015019 & 0.059912 & 0.094907 & 0.059912 & 0.015019 \\
0.023792 & 0.094907 & 0.150342 & 0.094907 & 0.023792 \\
0.015019 & 0.059912 & 0.094907 & 0.059912 & 0.015019 \\
0.003765 & 0.015019 & 0.023792 & 0.015019 & 0.003765
\end{bmatrix}

$$

## Sharpening Kernels

These kernels enhance the contrast of the image to bring out the details.

### Simple Sharpening

This is an extension to the edge detection kernel. In place of finding just the edge, it enhances it so as to increase the contrast.

$$
K_{shaprt} = \begin{bmatrix}
0 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 0
\end{bmatrix} + \begin{bmatrix}
0 & -1 & 0 \\
-1 & 4 & -1 \\
0 & -1 & 0
\end{bmatrix} \times \text{amount}
$$

eg:

$$
\begin{bmatrix}
0 & -1 & 0 \\
-1 & 5 & -1 \\
0 & -1 & 0
\end{bmatrix}
$$

### Unsharp Mask

Produces better results and has more arguments to customize the result. This combines both an edge detector and bluring kernel. Basic unsharp mask uses simple shartpening kernel and a gaussian blur kernel. In this case it will have the amount parameter and a radius parameter for gaussian blur.

eg:

$$

eg: \begin{bmatrix}
−0.00391 & −0.01563 & −0.02344 & −0.01563 & −0.00391 \\
−0.01563 & −0.06250 & −0.09375 & −0.06250 & −0.01563 \\
−0.02344 & −0.09375 & 1.85980 & −0.09375 & −0.02344 \\
−0.01563 & −0.06250 & −0.09375 & −0.06250 & −0.01563 \\
−0.00391 & −0.01563 & −0.02344 & −0.01563 & −0.00391
\end{bmatrix}
$$







# Reference

[1]:https://lilianweng.github.io/lil-log/2017/12/15/object-recognition-for-dummies-part-2.html

[2]:https://taylorpetrick.com/blog/post/convolution-part3