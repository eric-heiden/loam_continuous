## loam_continuous

Lidar Odometry and Mapping (Loam) is a realtime method for state estimation and mapping using a 3D lidar, and optionally an IMU. The program contains four nodes. The “scanRegistration” node stacks laser scans within a sweep and publishes them as point cloud. The “laserOdometry” node estimates motion of the lidar between two sweeps, at a higher frame rate. The node corrects distortion in the point cloud from motion of the lidar. The “laserMapping” node takes the output of “laser_odometry” and incrementally builds a map. It also computes pose of the lidar on the map, at a lower frame rate. The state estimation of the lidar is combination of the outputs from “laserOdometry” and “laserMapping”, integrated in the “transformMaintenance” node. 

The program is tested on ROS Fuerte, on a laptop computer with 2.5 GHz quad cores and 6 Gib memory (the program consumes two cores). This version uses a lidar that spins continuously.

Wiki Webpage: http://wiki.ros.org/loam_continuous

Another version of the program that uses back and forth spin is available at

Wiki Webpage: http://wiki.ros.org/loam_back_and_forth

GitHub Code: https://github.com/jizhang-cmu/loam_back_and_forth.git

### How to use:

1) Clone this repository to your `catkin_ws/src` folder and run `catkin_make`.

2) Download datasets from the following website. Make sure the data files are for continuous spin (not back and forth spin). Play the data files with “rosbag play data_file_name.bag”. Note that if a slow computer is used, users can try to play the data files at a lower speed, e.g. “rosbag play data_file_name.bag -r 0.5” plays the data file at half speed.

Datasets can be downloaded at: http://www.frc.ri.cmu.edu/~jizhang03/projects.htm
