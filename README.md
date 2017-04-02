Updates
----------

**Update 22/03/2017** Fixed a bug in mask_analysis.py and almost completed a more robust version of the CNN head pose estimator.

**Update 21/11/2016**
New package [color_classification.py](./deepgaze/color_classification.py). The package contains an implementation of the histogram intersection algorithm for colour classification [[example]](./examples/ex_color_classification_images/ex_color_classification_image.py). Read more on [my blog post](https://mpatacchiola.github.io/blog/2016/11/12/the-simplest-classifier-histogram-intersection.html).

**Update 04/11/2016**
New package [motion_tracking.py](./deepgaze/motion_tracking.py). The package contains an implementation of [Particle Filter](https://en.wikipedia.org/wiki/Particle_filter), which can be used to follow a target in presence of noisy measurements [[example]](./examples/ex_particle_filter_object_tracking_video/ex_particle_filter_object_tracking_video.py) [[video]](https://www.youtube.com/watch?v=KTxVBN5-KpE)

**Update 01/11/2016**
Comparison of three different motion detection algorithms [[example]](./examples/ex_motion_detectors_comparison_video/ex_motion_detectors_comparison_video.py) [[video]](https://www.youtube.com/watch?v=XmI2kE2hUgE)

**Update 28/10/2016**
New package [motion_detection.py](./deepgaze/motion_detection.py). Using the classes in this package it is possible to track moving objects through [background subtraction](https://en.wikipedia.org/wiki/Background_subtraction). Possible applications of this algorithm are people detection, vehicle detection and tracking [[example]](./examples/ex_diff_motion_detection_video/ex_diff_motion_detection.py)

**Update 21/10/2016**:
New package [color_detection.py](./deepgaze/color_detection.py) added. Using the classes inside this package it is possible to detect colors [[example]](./examples/ex_color_detection_image/ex_color_detection_image.py), skin [[example]](./examples/ex_skin_detection_images/ex_skin_detection_images.py) and faces [[example]](./examples/ex_face_center_color_detection/ex_face_center_color_detection.py)

**Update 19/10/2016**:
Working example on how to use CNNs for the pitch estimation [[code]](./examples/ex_cnn_headp_pose_estimation_images/ex_cnn_head_pose_estimation_images_pitch.py)
Working example on how to use CNNs for both yaw and pitch estimation [[code]](./examples/ex_cnn_headp_pose_estimation_images/ex_cnn_head_pose_estimation_images_pitch_yaw.py)

**Update 5/10/2016**:
Working example on how to use CNNs for head pose estimation (for the moment only yaw angle) [[code]](./examples/ex_cnn_headp_pose_estimation_images/ex_cnn_head_pose_estimation_images.py)

**Update 20/09/2016**:
Work in progress. The code provided at the moment does not still implement gaze detection. There is a beta version of the class which implements the CNN head pose estimator of the yaw angle [[code]](https://github.com/mpatacchiola/deepgaze/blob/master/deepgaze/head_pose_estimation.py). You can use it loading the variables stored in this [[file]](https://github.com/mpatacchiola/deepgaze/blob/master/etc/tensorflow/head_pose/yaw/cnn_cccdd_30k).


What is deepgaze?
----------
Deepgaze is a library for people detection and tracking which uses **Convolutional Neural Networks** (CNNs) to estimate the Focus of Attention (FOA) of users. The FOA can be approximately estimated finding the **head orientation**. This is particularly useful when the eyes are covered, or when the user is too far from the camera to grab the eye region with a good resolution. When the eye region is visible it is possible to estimate the **gaze direction**, which is much more informative and can give a good indication of the FOA. Deepgaze contains useful packages for:

- Head pose estimation (Perspective-n-Point, Convolutional Neural Networks)
- Face detection (Haar Cascade)
- Skin and color detection (Range detection, Backprojection)
- Motion detection (Frame differencing, MOG, MOG2)
- Motion tracking (Particle filter)

Deepgaze is based on OpenCV and Tensorflow, some of the best libraries in computer vision and machine learning. Deepgaze is an **open source** project and any contribution is appreciated, feel free to fork the repository and propose integrations. 

This library is the result of my recent work which is under revision:
*Head Pose Estimation in the Wild using Convolutional Neural Networks and Adaptive Gradient Methods*

What is a Convolutional Neural Network?
------------------------------
A convolutional neural network (CNN, or ConvNet) is a type of feed-forward artificial neural network in which the connectivity pattern between its neurons is inspired by the organization of the animal visual cortex, whose individual neurons are arranged in such a way that they respond to overlapping regions tiling the visual field. Convolutional networks were inspired by biological processes and are variations of multilayer perceptrons designed to use minimal amounts of preprocessing. They have wide applications in image and video recognition, recommender systems and natural language processing [[wiki]](https://en.wikipedia.org/wiki/Convolutional_neural_network)

<p align="center">
<img src="doc/images/figure_cnn.png" width="750">
</p>


Prerequisites
------------
To use the libray you have to install:

- Numpy [[link]](http://www.numpy.org/)

```shell
sudo pip install numpy
```

- OpenCV [[link]](http://opencv.org/)

```shell
sudo apt-get install libopencv-dev python-opencv
```

- Tensorflow [[link]](https://www.tensorflow.org/)

```shell
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.10.0rc0-cp27-none-linux_x86_64.whl
sudo pip install --upgrade $TF_BINARY_URL
```

Some examples may require additional libraries:

- dlib [[link]](http://dlib.net/)

Installation
--------

Download the repository from [[here]](https://github.com/mpatacchiola/deepgaze/archive/master.zip) or clone it using git:

```shell
git clone https://github.com/mpatacchiola/deepgaze.git
```

To install the package you have to run the setup.py script (it may require root privileges):

```shell
sudo python setup.py install
```

If you want to track all the installed files you can record the installation process in a text file:

```shell
sudo python setup.py install --record record.txt
```

Done! Now give a look to the examples below.

Examples
--------

- Head Pose Estimation using the Perspective-n-Point algorithm in OpenCV [[code]](./examples/ex_pnp_head_pose_estimation_webcam.py) [[video]](https://www.youtube.com/watch?v=OSnI18XmAg4)

- Head Pose Estimation in-the-wild using Perspective-n-Point and dlib face detector [[code]](./examples/ex_dlib_pnp_head_pose_estimation_video.py) [[video]](https://www.youtube.com/watch?v=xurEs0G9ARs)

- Head Pose Estimation in images using Convolutional Neural Networks [[code]](./examples/ex_cnn_headp_pose_estimation_images/ex_cnn_head_pose_estimation_images.py)

<p align="center">
<img src="doc/images/ex_cnn_head_pose_estimation_images.png" width="750">
</p>

- Color detection using the Histogram Backprojection algorithm [[blog]](https://mpatacchiola.github.io/blog/2016/12/01/playing-the-google-chrome-dinosaur-game-with-your-hand.html) [[code]](./examples/ex_color_detection_image/ex_color_detection_image.py)

<p align="center">
<img src="doc/images/ex_color_detection_image.png" width="750">
</p>

- Skin detection using the HSV range color detector [[code]](./examples/ex_skin_detection_images/ex_skin_detection_images.py)

<p align="center">
<img src="doc/images/ex_skin_detection_images.png" width="750">
</p>

- Face detection using the HSV range color detector [[code]](./examples/ex_face_center_color_detection/ex_face_center_color_detection.py)

<p align="center">
<img src="doc/images/ex_face_center_color_detection.png" width="750">
</p>

- Motion detection and tracking using frame differencing on a video streaming [[code]](./examples/ex_diff_motion_detection_video/ex_diff_motion_detection.py)

<p align="center">
<img src="doc/images/ex_diff_motion_detection_video.png" width="750">
</p>

- Motion detection and tracking comparison of three algorithms on a video streaming [[code]](./examples/ex_motion_detectors_comparison_video/ex_motion_detectors_comparison_video.py) [[video]](https://www.youtube.com/watch?v=XmI2kE2hUgE)

<p align="center">
<img src="doc/images/ex_motion_detectors_comparison_video.png" width="750">
</p>

- Motion tracking with unstable measurements using Particle Filter [[code]](./examples/ex_particle_filter_object_tracking_video/ex_particle_filter_object_tracking_video.py) [[video]](https://www.youtube.com/watch?v=KTxVBN5-KpE)
<p align="center">
<img src="doc/images/ex_particle_filtering_object_tracking_video.png" width="750">
</p>

- Motion tracking with multiple backprojection for playing chrome's dinosaur game [[blog]](https://mpatacchiola.github.io/blog/2016/12/01/playing-the-google-chrome-dinosaur-game-with-your-hand.html) [[code]](./examples/ex_multi_backprojection_hand_tracking_gaming/ex_multi_backprojection_hand_tracking_gaming.py) [[video]](https://www.youtube.com/watch?v=eoUOkV5vVpU&feature=youtu.be)
<p align="center">
<img src="doc/images/ex_multi_backprojection_hand_tracking_gaming.gif" width="550">
</p>

- Classify object using their colour fingerprint (histogram intersection) [[blog]](https://mpatacchiola.github.io/blog/2016/11/12/the-simplest-classifier-histogram-intersection.html) [[code]](./examples/ex_color_classification_images/ex_color_classification_image.py)
<p align="center">
<img src="doc/images/ex_color_classification_images.png" width="750">
</p>

Acknowledgments
---------------

- The example "head pose estimation using Perspective-n-Point" is partially based on the C++ version you can find [here](https://github.com/severin-lemaignan/gazr), and on the workshop "Developing an attention system for a social robot" which was part of the 2nd International Summer School on Social Human-Robot Interaction.

- To implement the Bayes and Particle Filters I followed the great repository of [rlabbe](https://github.com/rlabbe) which you can find [here](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python)









