# Vehicle Detection

The goal of this project was to identify vehicles in a video stream, by marking their position with a bounding box.
To achieve this, the following steps were performed:

* Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images
* Color feature extraction (histogram based and via spatial binning)
* Training of a binary classifier
* Implementation of a sliding-window technique to search for vehicles in images
* Design and implementation of a heat map technique to suppress outliers and make the detection of vehicles more robust
* Estimation of a bounding box for detected vehicles

All of the code for completing this project is contained in [this jupyter notebook](https://github.com/Corni33/CarND_P5_VehicleDetection/blob/master/vehicle_detection.ipynb).

## Feature Extraction

The labeled data set consist of ...# vehicle and ...# non-vehicle images, each with a size of 64 by 64 pixels and 3 color channels.

In order to train a classifier to distinguish vehicles from other objects (e.g. road markings, trees, ...), characteristik featurs of the images have to be extracted.  

### Color Features

An example of a vehicle image and a non vehicle image looks like this:
.. example images RGB ... 

In this case it's easy to see that one possible criterion for classifying images might be color information.
To use this information a histogram over the whole image for each color channel is calculated and unraveled into a feature vector:
... hist plot RGB ....
 .. feature vec plot ...

It turns out that using a different color space can help to 

...

### HOG Features
...





