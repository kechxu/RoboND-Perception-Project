[predicted1]: ./images/predicted1.PNG
[predicted2]: ./images/predicted2.PNG
[predicted3]: ./images/predicted3.PNG

# Perception Pipeline
## Exercise 1
1. Point cloud ROS data was converted to PCL data
2. Point cloud was filtered with statistical outlier filter to remove noise from RGBD camera
    - Number of points and threshold scale factor was experimentally found
3. Point cloud was downsampled
4. A z -axis passthrough filter was made to filter out the bottom table particles
5. A y-axis passthrough filter was made to filter out the edges of the boxes that were present in the point cloud data
6. RANSAC Plane filtering to split objects from table
## Exercise 2
1. Experimentally found cluster sizes by determining the max/min point cloud cluster from testing
2. Set cluster tolerances and split point cloud data into different objects

## Exercise 3
1. Extracted 20 features for each object. The training set can be seen at `pr2_robot/scripts/training_set.sav`
2. Trained SVM with 20 extracted features. The model can be seen at `pr2_robot/scripts/model.sav`
3. Extracted features from object clusters using HSV color histograms
4. Predicted object using trained SVM
5. Added coresponding predicted label to object

# Pick and Place Setup
Using the data extracted from the perception pipeline, the clustered objects' centroid was found and then compiled into a ROS message. Although the pick place portion of the project was not complete due to computer limitations, the example output was outputted to appropriate YAML files. To speed up the process of switching between worlds, a rosparam was set in `pr2_robot/launch/pick_place_project.launch` launch file called `test_scene_num` which could be changed to determine the world number.

YAML outputs can be found at `pr2_robot/scripts/output_*.yaml`.

![alt text][predicted1]


`test1.world`
3/3 objects were predicted

![alt text][predicted2]


`test2.world`
4/5 objects were predicted
![alt text][predicted3]


`test3.world`
8/8 objects were predicted
