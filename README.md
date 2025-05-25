## Development_of_an_Autonomous_Navigation_System_Based_on_Rolling_2D_Lidar_in_Modern_Apple_Orchards
We have developed an autonomous mobile robot for modern orchards. This robot is capable of scanning the orchard environment using a 2D lidar through rolling motion to obtain 3D point cloud data of the orchard. It then utilizes the 3D point cloud of the current tree row to extract and fit tree row lines and the navigation line. By employing trajectory tracking, the robot achieves autonomous navigation between rows. At the end of each row, it utilizes point cloud data to determine and locate the end of the row, and ultimately performs the U-turn. The robot is mainly composed of a 2D lidar, a servo motor (equipped with high-precision magnetic encoders), an IMU (Inertial Measurement Unit), and a four-wheel independently driven chassis (with wheel speed feedback). The robot and all sensors follow the right-hand Cartesian coordinate system

<p align="center">
  <img src="img/Hardware_Schematic.jpg" alt="Hardware Overview" width="90%"/>
</p>

### Construction of 3D Point Clouds
Synchronizing the 2D point cloud, servo motor angle feedback, wheeled odometry, and IMU data, and registering the 2D point cloud data into the O3d-xyz reference coordinate system for 3D point clouds, ultimately publishing the accumulated 3D point cloud data from every half rolling cycle for environmental perception processing. We have tested the system in a modern apple orchard, the process and results are as follows:

<p align="center">
  <img src="img/create_3d_pointcloud.gif" alt="3D pointcloud construction" width="80%"/>
</p>

<p align="center">
  <img src="img/3D_pointcloud.jpg" alt="3D pointcloud" width="80%"/>
</p>

### Tree Row 3D Point Cloud Segmentation
We used a point cloud segmentation strategy to extract the point cloud data of the fruit tree in the tree row where the robot is currently located, and the results are as follows:

<p align="center">
  <img src="img/tree_row_segmentation.gif" alt="tree row segmentation" width="80%"/>
</p>

<p align="center">
  <img src="img/treerow_extraction.jpg" alt="tree row extraction" width="80%"/>
</p>

### Trunk 3D Point Cloud extraction
Local geometrical features are utilized to extract the fruit tree trunk point cloud, the results are as follows:

<p align="center">
  <img src="img/trunk_point_extraction.png" alt="trunk point extraction" width="80%"/>
</p>

### Navigation Line Fitting
The extracted trunk point cloud is finally utilized to fit the navigation line for the robot autonomous guidance, the results are as follows (The white point cloud represents extracted tree trunk features. The blue and red arrows indicate the left and right tree row lines, respectively, while the white center line denotes the navigation path):

<p align="center">
  <img src="img/navigation_line_detection.gif" alt="Navigation line fitting" width="80%"/>
</p>

### Path tracking
The pure pursuit controller is implemented to guide the robot along the target path for autonomous navigation. Field test results are as follows:

<p align="center">
  <img src="img/autonomous_navigation.gif" width="80%"/>
</p>

## Detailed information can be seen in this paper：
Zhou, Y.; Wang, X.; Wang, Z.; Ye, Y.; Zhu, F.; Yu, K.; Zhao, Y. Rolling 2D Lidar-Based Navigation Line Extraction Method for Modern Orchard Automation. Agronomy 2025, 15, 816. https://doi.org/10.3390/agronomy15040816

## Author
Yibo Zhou

College of Mechanical and Electronic Engineering, Northwest A&F University
