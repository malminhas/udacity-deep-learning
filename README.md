# udacity-deep-learning
Udacity Deep Learning course ipynb assignments.
Also contains HTML versions of ipynb for convenience.

## Setup
These notebooks were developed in a Python 2.7.6 virtualenv setup running on a 64-bit Ubuntu 14.04 running in a VirtualBox VM on a standard issue 16GB Dell Latitude laptop. It should all work with a Python3 scipy+tensorflow stack.

IMPORTANT: You will need to assign **at least 8GB RAM to the VirtualBox VM** or the convnet examples will not run.

## Installing tensorflow
The following assumes you have Python virtualenv support in place:
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
(tf)$ pip install https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.7.0-py2-none-linux_x86_64.whl
(tf)$ python
Python 2.7.6 (default, Nov 10 2013, 19:24:18) [MSC v.1500 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>> import tensorflow as tf
>> 
(tf)$ ipython notebook
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
 - The data generated is as follows: i) Training set = 200k 28 x 28 images, ii) Validation set = 10k images, iii) Test set = 10k images.  All loaded into notMNIST.pickle file. On loading images reformatted to unravelled 784 len vector (28x28)
 
**2. fullyconnected.ipynb**:
 - Use same data generated in previous assignment.  
 - This time we apply tensorflow (tf) to it.
 - With tf there are two stages: i) build computation graph, ii) run successive operations on it.
 - first example shown is BGD logistic.  Test Accuracy: 82.6%
 - second example shown is SGD logistic.  Test Accuracy: 86.3%
 - worked example is SGD with a single hidden layer NN.  Apply RELU over hidden layer. Test Accuracy: 93.4%

**3. regularisation.ipynb**:
 - Same data as 2.
 - Regularisation is used to address overfitting. 
 - SGD logistic from assignment 2 with regularization.  Test Accuracy: 89.2%
 - SGD with a single hidden layer neural net.  Test Accuracy: 93.6%
 - Trying with smaller range of samples and dropouts
 - SGD with a single hidden layer NN and 50% dropout.  Test Accuracy: 92.8%
 - Try SGD with three hidden layer NN, learning rate decay and 50% dropout and three times as many steps to run through. Test Accuracy: 94.8%.  Warning: this took over ~10 hours to run to completion on VM on my laptop.
 
**4. convolutions.ipynb**:
 - Same data as 3.
 - Starting point: 2 conv layers, 1 fully connected layer.  This seems to run ok in terms of time on my VM.  Test Accuracy: 89.8%
 - Replace strides with max pooling in the conv layers.  Test Accuracy: 90.1%
 - Added 50% dropout to both conv layers and fully connected layer.  Also added learning rate decay.  Test Accuracy: 48.5%
 - Limited dropout to 30% on fully connected layer only.  Left learning rate decay in there.  Test Accuracy: 77%
 - IMPORTANT: Solutions involving max pooling only run in a VM with 8GB RAM + processors set to 2.

**5. word2vec.ipynb**:
 - Data is text8 100MB text data file
 - Starting point: implementation of word2vec, tf computation graph, execute 100k steps
 - Average loss at step 100000: 3.357733
 - Problem: implementation of CBOW (continuous bag of words), tf computation graph, execute 100k steps
 - Involves swapping between target and label so instead of word->context we have context->word:
 - Average loss at step 100000: 3.357481

