# **Finding Lane Lines on the Road** 

## Writeup

[//]: # (Image References)

[image1]: ./test_images/grayscale.jpg "Grayscale"


### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied a Gaussian smoothing transformation, then I applied a Canny transformation to identify the edges, then I masked the images, and then finally defined and drew the Hough lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by finding the slope and center point of every Hough line. Slopes with values too high or too low were ignored, and the lines with a positive slope were concluded to be the right line, while lines with a negative slope were concluded to be the left line. 

Using all of the slope and center values, averages were calculated for both the left and right side. Then, using point slope form, I was able to determine the bottom and top points for each line. The bottom of each line is the bottom of the picture, and the top is slightly below the midpoint of the picture. Once I knew all of the points, I used the cv2.line function to connect them. 

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
