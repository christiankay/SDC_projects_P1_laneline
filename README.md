# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidYellowCurve2.jpg "Detected lanes merged with original image"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The processing pipeline mainly consists of six steps. First,  the images were converted to grayscale and gaussian blur was applied.
Blurring avoids the detection of unwanted edges during the processing of canny edge detection. 
After edge detection, a region of interest was selected to only process edges that may represent lane lines.
The gradient images were processed to finally detect small lines by using hough transformation.
In a final step, the found hough lines were averaged for each lane line (left&right) and extrapolated to a solid line.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by seperating the hough lines based
on the line gradient and averaged them to two new lines.
 

![alt text][image1]
### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the field of view of the camera changes. The pipeline ist sensitive 
to changes of the chosen region of interest. 

Another shortcoming could be curves on the track which lead to fitting problem regarding the hough lines extrapolation.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a dynamic region of interest based on the last found lane in previous images (video).

Another potential improvement could be to combine color based lane extraction and gradient based lane detection.
