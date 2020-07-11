# Selective Search

This is similar to the image segmentation algorithm but in place of working on pixels it works on the segments given by the segmentation algorithm.

This is mainly used for region proposal, which contain objects.

## Hierarchical Selective Search Algorithm

1. Apply graph based segmentation algorithm to create regions to start with.
2. Use greedy algorithm to iteratively group regions together:
   - Calculate similarities between neighbouring regions
   - Group 2 similar regions and calculate a new similarity of the resulting region
3. Repeat the grouping process until the whole image becomes a single region



## Similarity Comparison

For 2 regions $(r_i, r_j)$ we can have 4 kinds of similarity measure:

- **Color** similarity
- **Texture**: A different algorithm to calculate the texture similarity
- **Size**: Small regions are encouraged to merge early
- **Shape**: Ideally 1 region can fill the gap of the other



## Parameter Tuning

We have the following parameter to tune to get different results

- threshold $k$ of Felzenswalb and Huttenlocher’s algorithm
- Changing color space of the image
- Similarity measure operation

