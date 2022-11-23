# Mid-Term Project Writeup: 3D Object Detection

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

### The result looks like:

![221119](https://user-images.githubusercontent.com/94186015/202856176-73d9c92c-3bdb-4541-83a4-a543229deb1c.PNG)

### Visualize lidar point-cloud (ID_S1_EX2)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-10963653239323173269_1924_000_1944_000_with_camera_labels.tfrecord'

show_only_frames = [0, 200]

exec_data = []

exec_detection = []

exec_tracking = []

exec_visualization = ['show_pcl']

### The results look like:

![1120A](https://user-images.githubusercontent.com/94186015/202886781-954166de-c9ce-4db7-8d6a-6344e8577359.PNG)

![1120B](https://user-images.githubusercontent.com/94186015/202886800-92662a58-1715-4075-b489-a19f562c525f.PNG)

![1120C](https://user-images.githubusercontent.com/94186015/202886808-4faba2cb-a60d-4366-bc21-f39b07360edf.PNG)

### Section 2 : Create Birds-Eye View from Lidar PCL

### Convert sensor coordinates to BEV-map coordinates (ID_S2_EX1)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-1005081002024129653_5313_150_5333_150_with_camera_labels.tfrecord

show_only_frames = [0, 1]

exec_data = ['pcl_from_rangeimage']

exec_detection = ['bev_from_pcl']

exec_tracking = []

exec_visualization = []

### The result looks like:

![221120g](https://user-images.githubusercontent.com/94186015/202888609-b518820e-fd67-4a7a-8621-10e478384100.PNG)

### Compute intensity layer of the BEV map (ID_S2_EX2)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-1005081002024129653_5313_150_5333_150_with_camera_labels.tfrecord

show_only_frames = [0, 1]

exec_data = ['pcl_from_rangeimage']

exec_detection = ['bev_from_pcl']

exec_tracking = []

exec_visualization = []

### The result looks like:

![221120g1](https://user-images.githubusercontent.com/94186015/202888678-4c91532e-ea01-4066-a61c-639b0879dd74.PNG)

### Compute height layer of the BEV map (ID_S2_EX3)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-1005081002024129653_5313_150_5333_150_with_camera_labels.tfrecord

show_only_frames = [0, 1]

exec_data = ['pcl_from_rangeimage']

exec_detection = ['bev_from_pcl']

exec_tracking = []

exec_visualization = []

### The result looks like:

![221120g2](https://user-images.githubusercontent.com/94186015/202888731-855c3447-ed8d-48c5-9be9-8594f53ad2c7.PNG)

### Section 3 : Model-based Object Detection in BEV Image

### Add a second model from a GitHub repo (ID_S3_EX1)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-1005081002024129653_5313_150_5333_150_with_camera_labels.tfrecord

show_only_frames = [50, 51]

exec_data = ['pcl_from_rangeimage', 'load_image']

exec_detection = ['bev_from_pcl', 'detect_objects']

exec_tracking = []

exec_visualization = ['show_objects_in_bev_labels_in_camera']

configs_det = det.load_configs(model_name="fpn_resnet")

### Where to find this task?
This task involves writing code within the functions detect_objects, load_configs_model and create_model located in the file student/objdet_detect.py.

### What this task is about?
The model-based detection of objects in lidar point-clouds using deep-learning is a heavily researched area with new approaches appearing in the literature and on GitHub every few weeks. On the website Papers With Code and on GitHub, several repositories with code for object detection can be found, such as Complex-YOLO: Real-time 3D Object Detection on Point Clouds and Super Fast and Accurate 3D Object Detection based on 3D LiDAR Point Clouds.

The goal of this task is to illustrate how a new model can be integrated into an existing framework. The task consists of the following steps:

Clone the repo Super Fast and Accurate 3D Object Detection based on 3D LiDAR Point Clouds
Familiarize yourself with the code in SFA3D->test.py with the goal of understanding the steps involved for performing inference with a pre-trained model
Extract the relevant parameters from SFA3D->test.py->parse_test_configs() and add them to the configs structure in load_configs_model.
Instantiate the model for fpn_resnet in create_model.
After model inference has been performed, decode the output and perform post-processing in detect_objects-
Visualize the results by setting the flag show_objects_in_bev_labels_in_camera
Note that the pre-trained model from SFA3D as well as the model classes and some helper functions have already been integrated into the mid-term project. You can find all related files in the folder tools/objdet_models/resnet.

Also note that in this project, we are only focussing on the detection of vehicles, even though the Waymo Open dataset contains labels for other road users as well.

### Extract 3D bounding boxes from model response (ID_S3_EX2)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-1005081002024129653_5313_150_5333_150_with_camera_labels.tfrecord

show_only_frames = [50, 51]

exec_data = ['pcl_from_rangeimage', 'load_image']

exec_detection = ['bev_from_pcl', 'detect_objects']

exec_tracking = []

exec_visualization = ['show_objects_in_bev_labels_in_camera']

configs_det = det.load_configs(model_name="fpn_resnet")

### The result looks like:

![221120g3](https://user-images.githubusercontent.com/94186015/202889643-aa6a4497-8dc6-4d8e-ab8e-72a3ab1135b9.PNG)

### Section 4 : Performance Evaluation for Object Detection

### Compute intersection-over-union between labels and detections (ID_S4_EX1)
### Task preparations
In file loop_over_dataset.py, set the attributes for code execution in the following way:

data_filename = 'training_segment-1005081002024129653_5313_150_5333_150_with_camera_labels.tfrecord

show_only_frames = [50, 51]

exec_data = ['pcl_from_rangeimage']

exec_detection = ['bev_from_pcl', 'detect_objects', 'validate_object_labels', 'measure_detection_performance']

exec_tracking = []

exec_visualization = ['show_detection_performance']

configs_det = det.load_configs(model_name="darknet")

### compute intersection over union (iou) and distance between centers

            ####### ID_S4_EX1 START #######     
            #######
            print("student task ID_S4_EX1 ")

            ## step 1 : extract the four corners of the current label bounding-box
            box = label.box
            box_1 = tools.compute_box_corners(box.center_x, box.center_y, box.width, box.length, box.heading)

            ## step 2 : loop over all detected objects
            for detection in detections:

                ## step 3 : extract the four corners of the current detection
                _id, x, y,z, _h, w, l, yaw = detection
                box_2 = tools.compute_box_corners(x, y, w, l, yaw)

                ## step 4 : computer the center distance between label and detection bounding-box in x, y, and z
                dist_x = np.array(box.center_x - x).item()
                dist_y = np.array(box.center_y - y).item()
                dist_z = np.array(box.center_z - z).item()
                # dist_x = box.center_x - x
                # dist_y = box.center_y - y
                # dist_Z = box.center_z - z

                ## step 5 : compute the intersection over union (IOU) between label and detection bounding-box
                try:
                    poly_1 = Polygon(box_1)
                    poly_2 = Polygon(box_2)
                    intersection = poly_1.intersection(poly_2).area 
                    union = poly_1.union(poly_2).area
                    iou = intersection / union
                except Exception as err:
                    print("Error in computation",err)
                ## step 6 : if IOU exceeds min_iou threshold, store [iou,dist_x, dist_y, dist_z] in matches_lab_det and increase the TP count
                if iou > min_iou:
                    matches_lab_det.append([iou,dist_x, dist_y, dist_z ])
                    true_positives = true_positives + 1

            #######
            ####### ID_S4_EX1 END #######   
            
            
            ####### ID_S4_EX2 START #######     
    #######
    print("student task ID_S4_EX2")
    
    # compute positives and negatives for precision/recall
    
    ## step 1 : compute the total number of positives present in the scene
    all_positives = labels_valid.sum()


    ## step 2 : compute the number of false negatives
    false_negatives = all_positives - true_positives


    ## step 3 : compute the number of false positives
    false_positives = len(detections) - true_positives

    
    #######
    ####### ID_S4_EX2 END #######     
    
    
    ####### ID_S4_EX3 START #######     
    #######    
    print('student task ID_S4_EX3')

    ## step 1 : extract the total number of positives, true positives, false negatives and false positives
    TP = sum([data[1] for data in pos_negs])
    FN = sum([data[2] for data in pos_negs])
    FP = sum([data[3] for data in pos_negs])

    ## step 2 : compute precision
    precision = TP / (TP + FP)


    ## step 3 : compute recall 
    recall = TP / (TP + FN)


    #######    
    ####### ID_S4_EX3 END #######     
    print('precision = ' + str(precision) + ", recall = " + str(recall))   

### The result is:

precision = 0.9508196721311475, recall = 0.9477124183006536

![221120g6](https://user-images.githubusercontent.com/94186015/202906937-b7969927-37a8-4623-8bc2-5e2f0a9b2040.PNG)

