# **Finding Lane Lines on the Road** 

## Writeup

[//]: # (Image References)

[image1]: ./test_images/grayscale.jpg "Grayscale"


### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied a Gaussian smoothing transformation, then I applied a Canny transformation to identify the edges, then I masked the images, and then finally, I defined and drew the Hough lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by finding the slope and center point of every Hough line. Slopes with values too high or too low were ignored, and the lines with a positive slope were concluded to be the right line, while lines with a negative slope were concluded to be the left line. 

Using all of the slope and center values, averages were calculated for both the left and right side. Then, using point slope form, I was able to determine the bottom and top points for each line. The bottom of each line is the bottom of the picture, and the top is slightly below the midpoint of the picture. Once I knew all of the points, I used the cv2.line function to connect them. 

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when lane markings were dirty or worn down. If the markings were brown, for example, the threshold in the Canny function would not be able to detect the line. 

Another shortcoming could be if the car were approaching the top of a hill, so that the cameras are unable to see more than a few feet in front of them. The pipeline would assume that the lines continue with the visible slope, but that could be wrong if the road turned at the top of the hill.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to identify the lanes adjacent to the lane that the car is currently in. This would be helpful in merging into the other lanes as well as seeing cars merge into this lane.

Another potential improvement could be to detect how high up the image the car can see the lines. Currently, the top of the lines are at a set point below the midpoint. This appears correct in normal driving circumstances, but there are instances where the lines are higher/lower than this point. 
