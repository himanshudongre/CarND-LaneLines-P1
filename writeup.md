# **Finding Lane Lines on the Road**

## By Himanshu Dongre
---

**Finding Lane Lines on the Road**

In this project we design a pipeline to detect lane lines on the road using OpenCV and Python.


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.

1. We read in an image and convert it to HSL color space and apply a mask to the image to extract white and yellow lines.This helps us see white and yellow lines properly in case of low light and shadow in the image.
2. We convert the above processed image to Grayscale and apply canny edge detection and Gaussian Blur.
3. We then create a polygon region of interest to mask the noise and provide a clear view of only lane lines.
4. We then apply Hough transform to the image to get the detected continuous and discrete line segments.
5. We then average and extrapolated the line segments and draw them back on the image to create continuous line segments.To achieve this we modify the draw_lines() function to calculate the slope and center co-ordinates of each line detected and then divide them into left and right lanes based on their slope.We then average all the slopes ,x and y centers and use the average to draw left and right lanes by calculating top and bottom co-ordinates for each line.

Below you can see the images processed through the above pipeline and their detected lane lines drawn on top of them:

[image1]: ./test_images_output/whiteCarLaneSwitch_lanes.jpg "whiteCarLaneSwitch"

[image2]: ./test_images_output/solidYellowLeft_lanes.jpg "solidYellowLeft"

[image3]: ./test_images_output/solidWhiteRight_lanes.jpg "solidWhiteRight"

[image4]: ./test_images_output/solidWhiteCurve_lanes.jpg "solidWhiteCurve"

[image5]: ./test_images_output/solidYellowCurve2_lanes.jpg "solidYellowCurve2"

[image6]: ./test_images_output/solidYellowCurve_lanes.jpg "solidYellowCurve"

We apply the above created pipeline on 3 videos showing lane lines and create annotated videos for the same.

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when we try to detect lanes at night or in extreme weather.

Another shortcoming is that the current pipeline is not able to detect curved line when there is a sharp turn.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make the system more robust to different lighting and weather conditions.

Another potential improvement could be to create a system that can detect curve lines too.
