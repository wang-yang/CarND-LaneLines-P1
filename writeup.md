# **Finding Lane Lines on the Road**

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/grayscale.png "Grayscale"
[image2]: ./test_images_output/blur.png "Blur"
[image3]: ./test_images_output/canny.png "Canny"
[image4]: ./test_images_output/mask.png "Mask"
[image5]: ./test_images_output/hough.png "Hough"
[image6]: ./test_images_output/pipeline1.png "Pipeline1"
[image7]: ./test_images_output/pipeline2.png "Pipeline2"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

#### The initial draw_line(), which draw several line on the image

My pipeline consisted of 5 steps.

1) I converted the images to grayscale

![Grayscale][image1]

2) I used gaussian filter to the grayscale image into blur image, which can suppress noise and can improve the effect when we do edges detection.

![Blur][image2]


3) I used Canny Edge Detection to get the raw line

![Canny][image3]

4) Then, I created a polygon mask region which is only covered the road to filter out the lines outside road.

![Mask][image4]

5) Use Hough algorithm to get solid lines

![Hough][image5]

After that, I draw the line on the image, as following

![Pipeline1][image6]

#### The improved version of draw_line2(), which draw only single line on the image

In order to draw a single on on each side, I grouped the lines into the left group and right group, then fit them into the left line and right line. Then draw them on the image. The code cell of this `draw_line2()` in `#3`. And the final result as follow:

![Pipeline2][image7]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are only few strips are visible, the slope of the lane is identified in an incorrect way.

Another shortcoming could be the region of interested is very sensible to position of the camera, many parameters have to be fine tuned when the position of camera changed.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to solve the above shortcoming.

And my implementation failed to handle the challenge video. When the lane line is not a straight line, may need some method to generate curve line.
