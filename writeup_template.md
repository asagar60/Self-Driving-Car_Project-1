# **Finding Lane Lines on the Road**
---
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale_image.jpg "Grayscale"
[image2]: ./examples/blurred.jpg "Gaussian"
[image3]: ./examples/Canny_transform.jpg "Canny Transform"
[image4]: ./examples/masking_with_region_of_interest.jpg "Region of Interest"
[image5]: ./examples/lane_lines_mask.jpg "Lane Lines on mask"
[image6]: ./examples/lane_lines_final.jpg "Lane Lines on Image"
---

### Reflection

### 1. Lane Line Detection Pipeline

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


### 2. Potential Shortcomings in this approach


*  This Approach doesnt handle cases of curved lane lines


### 3. Possible improvements to the pipeline

* Polylines() function of opencv might overcome this shortcoming
