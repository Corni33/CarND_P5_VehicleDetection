# Vehicle Detection

The goal of this project was to identify vehicles in a video stream, by marking their position with a bounding box.
To achieve this, the following steps were performed:

* Camera calibration (distortion correction) 
* Perspective transformation to achieve a "birds-eye view" of the road
* Lane line pixel detection and polynomial fitting to find the lane boundary
* Determining the curvature of the lane and the lateral vehicle position with respect to the lane center
* Overlaying the detected lane onto the original camera image 

All of the code for completing this project is contained in [this jupyter notebook](https://github.com/Corni33/CarND_P4_AdvancedLaneLines/blob/master/advanced_lane_lines.ipynb).
