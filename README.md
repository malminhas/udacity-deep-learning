# udacity-deep-learning
Udacity Deep Learning course ipynb assignments.
Also contains HTML versions of ipynb for convenience.
These were developed on Python 2.7.6 setup on 64-bit Ubuntu 14.04.

## Installing tensorflow
Assume you are setting up a virtualenv:
```
$ mkvirtualenv tf
$ workon tf
(tf)$ pip wheel numpy
(tf)$ pip install numpy
(tf)$ pip wheel matplotlib
(tf)$ pip install matplotlib
(tf)$ pip wheel scipy
(tf)$ pip install scipy
(tf)$ pip wheel scikit-learn
(tf)$ pip install scikit-learn
(tf)$ pip wheel ipython[notebook]
(tf)$ pip install ipython[notebook]
# We want the 64-bit CPU only Python 2.7 version of tensorflow
(tf)$ pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.7.0-py2-none-linux_x86_64.whl
(tf)$ python
>> 
>> import tensorflow as tf
>> 
```
To get image support working:
```
$ sudo apt-get install python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
$ pip install Pillow
```

## Assignments
**1. notnmist.ipynb**:
 - notMNIST data is designed to look like the MNIST data but with lots of holes.
 - We use it to run through some basic data curation techniques.
 - Training set = 19k labelled 28x28 images in ten classes 'A' through to 'J'.  284Mb in size.
 - Extract from raw .tar.gz of .png files.  Convert png data into 3D ndarray and pickle it to 10 separate files depending on label. Takes well over 2 hours to do this on VM on my laptop!
 
**2. fullyconnected.ipynb**:
 - Same data as in previous assignment.  This time we use tensorflow (tf) with it.
 - With tf there are two stages: i) build computation graph, ii) run successive operations on it.
 - first example shown is BGD logistic.  Accuracy: 82.6
 - second example shown is SGD logistic.  Accuracy: 86.3%
 - worked example is SGD with a single hidden layer NN.  Apply RELU over hidden layer. Accuracy: 93.4%

**3. regularisation.ipynb**:
 - Regularisation is used to address overfitting. 
 - Try SGD logistic from assignment 2 with regularization.  Accuracy: 89.2%
 - Try SGD with a single hidden layer neural net. Accuracy: 93.6%
 - Try smaller range of samples
 - Try dropouts
 - Try SGD with a single hidden layer NN and 50% dropout.  Accuracy: 92.8%
 - Try SGD with three hidden layer NN, learning rate decay and 50% dropout and three times as many steps to run through. Accuracy: 94.8%.  Warning: this took over ~10 hours to run to completion on VM on my laptop.
