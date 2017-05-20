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

Another way of utilizing color information while also retaining some spatial information, is to just take the raw image pixel values and unravel them into a feature vector.
Doing so for the whole 64 by 64 pixel image will create a very big feature vector (4096 elements!) while not necessarily / and also ... , as not every pixel contains relevant information about the class of the image.
To cope with this problem the image gets scaled down to a more reasonable resolution that produces a smaller feature vector while still containing information about the spatial structure of the image.
After some experimentation I chose a resolution of 24 by 24 pixels:
...image 24 by 24 ...

### HOG Features

A very important feature for detecting vehicles is their characteristic shape. 
Even without color information, a human can easily identify a car in many different situations.
In my classification pipeline I used "histogram of oriented gradients" (HOG) features on all channels of the YCbCr image to extract shape information (code cell ...).

Applied to example images, the visualization of the HOG features looks like this:
... HOG vis of example images ...

As parameters for the HOG feature extraction I chose `orientations=8`, `pixels_per_cell=(8, 8)` and `cells_per_block=(2,2)`. 
I tried to increase `pixels_per_cell` to 16 (with `orientations` set to 11) to reduce the number of features and speed up the classifier, but this decreased the accuracy of bounding boxes, i.e. they fit less tight around the vehicles.

## Classifier Training

The classifier takes a single vector of features (containing color and HOG features) and produces a prediction whether or not an image contains a vehicle.

At first I started training a Support Vector Machine (SVM) and tried out different kernels (`rbf`, `linear`) and different combinations of parameter values (`C`, `gamma`).
While a well tuned `rbf` kernel showed good testing accuracy (>98%), it was slow in the prediction and generalization was only average (i.e. there were quite a few false positives / false negatives while testing it on the project video). ---> TODO: testen!!!!!
A well tuned (i.e. a well chosen value for `C`) linear SVM kernel seemed to generally provide better protection against overfitting.
In the end I settled for a Random Forest Classifier (an ensemble of decision trees) as it could be trained very fast (testing accuracy of about 99%) and gave me the least amount of false positives/negatives of all classification approaches I experimented with.










...





