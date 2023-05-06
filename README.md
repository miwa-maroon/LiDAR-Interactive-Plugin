# LiDAR-Interactive-Plugin

# dev

# Features
- Projection Mode
- Selecting the type of LiDAR
- Multiple LiDARs
- Easy Calibration (clicking base, not adjusting camera)
- Blob Tracking
- lightweight program(preferably with c++)

# Process of calibration
1. Correts the projection
2. Determines the area
3. Calibrates for blob tracking

# Technical Background
## Projection Area

## Tracking Blobs
Clustering
method *1
- MeanShift (band width) 
- Ward (number of clusters or distance threshold)
- Gaussian Mixture (the distance of the test point from the center of mass divided by the width of the ellipsoid in the direction of the test point 1)


## Calibration
Matching placed items and cursors


### references
*1. https://scikit-learn.org/stable/modules/clustering.html


