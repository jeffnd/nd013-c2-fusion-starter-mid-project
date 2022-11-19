# Writeup: Track 3D-Objects Over Time

Please use this starter template to answer the following questions:

### 1. Write a short recap of the four tracking steps and what you implemented there (filter, track management, association, camera fusion). Which results did you achieve? Which part of the project was most difficult for you to complete, and why?


### 2. Do you see any benefits in camera-lidar fusion compared to lidar-only tracking (in theory and in your concrete results)? 


### 3. Which challenges will a sensor fusion system face in real-life scenarios? Did you see any of these challenges in the project?


### 4. Can you think of ways to improve your tracking results in the future?

# Mid-Term Project: 3D Object Detection

### Section 1 : Compute Lidar Point-Cloud from Range Image

### Visualize range image channels (ID_S1_EX1)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-1005081002024129653_5313_150_5333_150_with_camera_labels.tfrecord

show_only_frames = [0, 1]

exec_data = []

exec_detection = []

exec_tracking = []

exec_visualization = ['show_range_image']

### The result look like:
