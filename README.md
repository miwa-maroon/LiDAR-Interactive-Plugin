# LiDAR-Interactive-Plugin

# dev

# Goal
- easy setup including projection, color correction, calibration and adjustimg(preset style)
- collaborate to work
- optimize a performance
- GUI base(need design)

# Features
- Projection Mode
- Selecting the type of LiDAR
- Multiple LiDARs
- Easy Calibration (clicking base, not adjusting camera)
- Blob Tracking
- lightweight program(preferably with c++)

# Process 
1. Correts the projection
2. Determines the area
3. Calibrates for blob tracking

# Technical Background
## Projection Area
- auto correction(Open CV) ^3
- save transformation matrix or UV Map

## Color Calibration


## Tracking Blobs
Clustering
method ^1
#### python
##### sk-learn
- MeanShift (band width) 
- Ward (number of clusters or distance threshold)
- Gaussian Mixture (the distance of the test point from the center of mass divided by the width of the ellipsoid in the direction of the test point 1)

#### C++
- hierarchical clustering[](https://github.com/cdalitz/hclust-cpp) ^2
- MeanShift

### implementation
- python and engine comp
- using python library with C++
- implemeting the method in C++


## Calibration
Matching placed items and cursors
Find best parameters


## Output
- OSC
- Json


## Collaboration
- external tox based(git for TD!!)

### references
^1. https://scikit-learn.org/stable/modules/clustering.html
^2. https://github.com/cdalitz/hclust-cpp
^3. https://vimeo.com/336365649
^4. https://medium.com/@shunichi.kasahara/fragment-shadow-touchdesigner-online-interactive-workshop-report-71a84bb0ae97

##### Other LiDAR System
https://github.com/STARRYWORKS-inc/HokuyoUtil
- doesn't consider projection

https://github.com/FifthChat/LidarTracker
- 
