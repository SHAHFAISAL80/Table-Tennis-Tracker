# Table-Tennis-Tracker
Tracking a table tennis ball in 3D using two cameras, and analyzing the result. Uses OpenCV and computer vision techniques to identify points, strokes, bounces, etc. 
Table Tennis Tracker
Tracking a table tennis ball in 3D using two cameras, and analyzing the result. Uses OpenCV and computer vision techniques to identify points, strokes, bounces, etc.

This project is not optimized for extended use, but rather showcases an idea for how OpenCV and computer vision can in a simple way be applied to analyze table tennis games. It has only been tested on videos captured at 720p, 30 fps on two iphones, and might need changes to work well for other onfigurations.

Overview
Demo
How to use
Further improvements
Overview
analysis_functions.py - Contains the Analyzer class, which computes 3D tracks, strokes, points etc. and visualization functions. Also contains functions for camera calibration, trilateration, interpolation, visualization, etc.

balltracker.py - Script that uses process_video.py to find ball positions in each frame of two videos, and storing these positions in the data-directory.

crop_video.py - Script for cropping and syncing two videos so that they are of the same length, and each two frames are approximately from the same point in time.

demo.py - Script demonstrating usage of Analyzer-class, and doing visualization.

process_video.py - Contains functions for detecting a table tennis ball in each frame of a video.

Demo
The data visualized below is the output from running the algorithm on two videos that are not uploaded here.

Uncomment a desired function furthest down in demo.py and run the script. This will create an "analyzer"-object. The following functions applied to this object are currently supported:

visualize_3d_strokes()
Plots the path of one detected stroke at a time in 3d, detected bounce positions, and the camera positions.

3dstroke

visualize_2d_strokes()
Plots the path of one detected stroke at a time in 2d and detected bounce positions.

2dstroke

animate_3d_path()
Creates an animation of the estimated 3d path taken in the whole video.

animation

bounce_heatmap()
Plots a heatmap of the detected bounces on the table.

bounce_heatmap

plot_3d_point()
Plots the estimated path of a whole point in 3d together with camera positions.

3dpoint

plot_trajectory()
Plots the estimated trajectory viewed from the perspective of one of the cameras.

allpointscam

Usage
Step 1: Clone repository
Clone repository to desired location.

Step 2: Capture and save
Capture two videos simultaneously using two cameras from either side of the table.

Create a new folder called "videos_original" in the working directory and store the two videos here.

Step 3: Crop (crop_video.py)
Create a new folder called "videos" in the working directory. Assign the variable video_name in crop_video.py a name of the instance that will be used to store the data later. Then run the script.

The function will open a window which shows the current frame from each camera. Press 1 or 2 to run a camera forward. When a synced position in the video has been reached, press esc. and the script will save the ramainder of the videos until one has no more frames into the "videos"-folder. This ensures equal length of the two videos.

Step 4: Process videos (balltracker.py)
Set video_name to the chosen instance name in balltracker.py and then run the script. This will prompt you to locate corners and net positions in both videos. In the window that appears, double-click on the corner points and net positions in the order they appear here: (i.e. clock-wise from the top left to the bottom left, and then the top of the net, from bottom to top)

camera1_corner

After doing this the videos will be processed, and the detected position in each frame will be saved in the "data"-folder under the name of the video, together with the corner positions, fps, etc. This will take some time, depending on the length, resolution, etc. of the videos.

Step 5: Analyze result (demo.py)
In demo.py set video_name to the name of your instance, and then choose to run the desired function
