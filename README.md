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
0. Color Calibration
1. Correts the projection(Geometry Calibration)
2. Determines the area
3. Calibrates for blob tracking(Sensor Calibration)

# Technical Background
## Color Calibration
- display gamma[](http://compojigoku.blog.fc2.com/blog-entry-23.html)
- XYZ color space (needs to measure projected color by spectroradiometer) -> can alternate by camera?
- measure some samples and estimate parameter(Xr = Arx * R^g(display gamma) + Brx(environment light and black offset) <- scipy)
- Add X + Y + Z -> $$XYZ_{R,G,B} = 
\begin{pmatrix} 
X_{R} + X_{G} + X_{B} \\
Y_{R} + Y_{G} + Y_{B} \\
Z_{R} + Z_{G} + Z_{B} 
\end{pmatrix} =
\begin{pmatrix} 
a_{RX} & a_{GX} & a_{BX} \\
a_{RY} & a_{GY} & a_{BY} \\
a_{RZ} & a_{GZ} & a_{BZ} 
\end{pmatrix}
\begin{pmatrix} 
R^g \\
G^g \\
B^g
\end{pmatrix} +
\begin{pmatrix} 
b_{RX} + b_{GX} + b_{BX} \\
b_{RY} + b_{GY} + b_{BY} \\
b_{RZ} + b_{GZ} + b_{BZ}
\end{pmatrix}$$

- RGB to XYZ $$ XYZ_{R,G,B} = 
A
\begin{pmatrix} 
R^g \
G^g \
B^g
\end{pmatrix} +
\begin{pmatrix} 
b_{RX} + b_{GX} + b_{BX} \
b_{RY} + b_{GY} + b_{BY} \
b_{RZ} + b_{GZ} + b_{BZ}
\end{pmatrix}

- XYZ to RGB $$\begin{pmatrix} 
R^g \
G^g \
B^g
\end{pmatrix} = 
A^-1
\begin{pmatrix} 
X -(b_{RX} + b_{GX} + b_{BX}) \
Y - (b_{RY} + b_{GY} + b_{BY}) \
Z - (b_{RZ} + b_{GZ} + b_{BZ})
\end{pmatrix}

- Uniformity Correction(plus alpha)


## Geometry Calibration
- auto correction(Open CV) ^3
- - calibrate image of cameara with desired TOP
- save transformation matrix or UV Map


## Blob Tracking
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

### parameters
- Presets like a finger, a hand, a leg, a ball
- Custom mode(mm)

## Sensor Calibration
Matching placed items and cursors
Find best parameters


## Output
- OSC
- Json


## Collaboration
- external tox based(git for TD!!)

# references
^1. https://scikit-learn.org/stable/modules/clustering.html
^2. https://github.com/cdalitz/hclust-cpp
^3. https://vimeo.com/336365649
^4. https://medium.com/@shunichi.kasahara/fragment-shadow-touchdesigner-online-interactive-workshop-report-71a84bb0ae97

### Other LiDAR System
https://github.com/STARRYWORKS-inc/HokuyoUtil
- doesn't consider projection

https://github.com/FifthChat/LidarTracker
- doesn't consider projection
