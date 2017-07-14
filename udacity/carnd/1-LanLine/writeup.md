# **Finding Lane Lines on the Road** 




---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

1, I converted the images to grayscale because I just need the edge of the image and one channel is enough and simple.
2, I use gaussian_blur function to suppressing noise and Canny edge detect algorithm  to find the edge (the fast changing of derivatives may be edge).
3, I draw an mask region (it's quadrilateral  polygon ) on the image to get my interest region and  to  reduce  noise.
4, I tune the paramters of hough_lines to get lines in the image(Not very skilled).
5, I use weighted_img the apply result to origin image which is a copy of image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by judge the slop of each line segments.
As slop of left line is negative (x axis increase y axis decrease), I get the all left line by judge the slop. 
Then I loop all the left line and get the minimum x1 y1  and maximun x2 y2 to draw left line.the same to right line.

here is my result:
![alt text][test_images_output/solidWhiteCurve.jpg]


### 2. Identify potential shortcomings with your current pipeline

the significant  shortcomings is that there is some unexpected frames in the movie  where the right line I drawed is ran out of the mask region,and I can't find why.

One potential shortcoming is when the image size change and the land lines is not in the mask region , I will get error.

Another shortcoming could be if some line-like block between land lines area,then may get errors.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to refact my draw_lines function to get more readable .

Another potential improvement could be to overcome the challage project.
