# **Finding Lane Lines on the Road** 

## Description

---
### ** This is the first projext of self-driving cars engineer nanodegree. In this project, we will find lane lines of the road. This pipeline will be tested in different situations.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

## Pipeline


* First, the image is coverted to grey scale, gaussian blur is applied and using canny edge detector, edge is detected.
* Second, using region_of_interest function, the region where white lines may be of consideration is chosen.
* Third, using hough line detector, those white lines are detected and it's been colored with red color and overlapped over the original image.

I've also passed vertices in pipeline function as I tried to improve the lane detection considering different masked regions for every images.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by averaging all slopes, x co-ordinates and y co-ordiantes. Separate functions are defined for positive left lane and right lane as left lane has positive slope and right lane has negative slope. <br/>
For this function to draw a single line as it was not possible with the normal draw_lines function for middle line as its dotted-type. I've made use of averaging of slopes, x co-ordiante and y co-ordinate to calculate top x and bottom x co-ordinate to draw a straight line.

---
![./CarND-LaneLines-P1/test_images/solidWhiteCurve.jpg][original image]
![./CarND-LaneLines-P1/test_images_output/solidWhiteCurve.png][image after lane detection]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when we go through tight curves. Parameters might not be able to draw finer lines 
to gauge it.

Another shortcoming could be tracking lanes if they are of other shades or types. (quite possible in remote regions)


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to further tune parameters through vertices or line lengths/gaps to cover for curves. Upcoming lessons will probably cover this as I took a glimpse but I thought I should point it out.

Another potential improvement could be to cover a wider range of lane lines and types through better masking and transformations.
