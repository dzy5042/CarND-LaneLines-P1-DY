# **Finding Lane Lines on the Road** 

## Writeup

### By Dongao Yang, 05/31/2017
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/whiteCarLaneSwitch_output.jpg "One pipeline output"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
1. I converted the images to grayscale.
2. I applied gaussian blur and canny detection to find edges.
3. I created mask to mask region of interest.
4. I applied hough transform to get lines. (Also compute an averaged line stands for lane line)
5. I combine hough line image with original image to compute output. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by taking average of slope and bias on all line segments found by hough transformation. Filters also added.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be if the lane line recognition in the first catch is not a good one, the pipeline needs several more good catches to correct it.
Another shortcoming is the parameters for OpenCV are not fully optimized.
Also, although I tried to scale region of interest based on video size, but it still assume the lane lines will show up nicely in the bottom center. This pipeline will have huge problem if region-of-interest is not the "region of interest".


### 3. Suggest possible improvements to your pipeline

Further optimize the OpenCV parameters.
Change the region of interst mask shape to even more adapt to challenge video, but it will also cause more trouble if not that case.
Apply some pre editing on picture even before I do greyscale. Like paint any non white and yellow color to black at beginning. This will include less noise from road and ignore gradient change that we are not interested at. 
Doing better average on lane lines thant just taking mathmatical average from them.
