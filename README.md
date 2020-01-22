# **Finding Lane Lines on the Road**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project we will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  


[//]: # (Image References)

[image1]: ./examples/grayscale_image.jpg "Grayscale"
[image2]: ./examples/blurred.jpg "Gaussian"
[image3]: ./examples/Canny_transform.jpg "Canny Transform"
[image4]: ./examples/masking_with_region_of_interest.jpg "Region of Interest"
[image5]: ./examples/lane_lines_mask.jpg "Lane Lines on mask"
[image6]: ./examples/lane_lines_final.jpg "Lane Lines on Image"
[issue_1]: ./examples/Capture.JPG "imageio.ffmpeg.download() has been depreciated"

**Installing Dependencies**
---

- opencv -  `pip install opencv-python`
- imageio - `pip install imageio`
- ffmpeg - `pip install imageio-ffmpeg`
- moviepy - `pip install moviepy`

---

### Lane Line Detection Pipeline

To effectively detect lane lines using Computer Vision Techniques, I chose the following sequence

 * **Convert the Image to Grayscale**

    It is always easier to work on 2-channel images than 3-channel images
    ![image1]

* **Apply Gaussian Blur as Low pass filter**

    Gaussian Blur is used to remove noise in an Image and smooth the images.
    ![image2]

* **Apply Canny Edge Detection**

    Canny Edge Detection is used to detect edges. It detects parts of image where there is a abrupt shift in intensity.
    ![image3]

* **Selecting region of Interest**

    Now we select region of interest in which we want to find lane lines.
    I use a quadrilateral region
    ![image4]

* **Hough Transform**

    Hough Transform is used to detect lines and other polygons in the image.
    In this we used houghlines() functions to detect straight lines.
    Hough Transform uses hough space to detect common / intersecting points in sinusoidal curves which are the representation of straight lines in cartesian plane.
    ![image5]

* **Overlay the Original image with the lane lines**

    addweighted() function of opencv is used to multiply the original image with a smaller factor and then adding it to the lane lines in black image , so that lane lines have more intensity in the resultant image.
    ![image6]

**Common Issues**

![issue_1]

_Solution_ : make sure the moviepy package version is 1.0.0

_code_ : `pip install moviepy==1.0.0`
