# Canny Edge Detection Algorithm

It consits for 4 parts:

- Noise reduction
- Finding gradient and its direction
- Non Maximum supression
- Hysteresis thresholding

## Noise Reduction

The algorithm starts with Gaussian blurring.

## Magnitude and Direction of Gradient

It then uses Sobel Kernel to find gradients and its direction. This is performed on all the pixels.

## Non Maximum Supression

Each and every pixel is checked to identify if it is a local maximum or not. It it is not then the point is suppressed to 0.

If the point is considered to be a local maximum, it goes to the next stage.

## Hysteresis Thresholding

Here we use 2 threshol values. These 2 values divides the spectrum in 3 different regions.

Now we check in whic region the gradient intensity lies:

- If it is **greater** than the **max** threshold: it is a **sure-edge**
- If it in the **middle** of both the threshold: We **check connectivity** to other sure-edges
- If it is **lower** than the **min** threshold: it is **discarded**

## OpenCV implementation

```python
# without bluring
egdes = cv2.Canny(img, threshold1=min_val, threshld2=max_val)

# with bluring
img_blur = cv2.blur(img, ksize=(5,5))
edges_blur = cv2.Canny(img_blur, threshold1=min_val, threshold2=max_val)
```
