# uav mavros simulation (author @antonikaras)

## Dependencies

* ROS, tested on ros-melodic
* catkin workspace: `catkin_ws/src`
* the mavros package v1.11.0 (source build), https://dev.px4.io/master/en/ros/mavros_installation.html
* QGroundControl, http://qgroundcontrol.com/
* the simple_pid python package, ```pip install simple-pid```
* PX4 firmware, tested on version v1.11.0-beta1, ``` git clone https://github.com/PX4/Firmware.git ```

## Instructions

* catkin_ws/src: ``` git clone https://github.com/congtranv/uav_mavros_simulation.git ```
* catkin_ws/src/uav_mavros_simulation: ```./installAshets.sh /path/to/PX4/Firmware```
* Add `/path/to/PX4/Firmware` to the file `uav_mavros_simulation/launch/uav_launch.launch` at `firm_dir`
* ```catkin build```
* ```source catkin_ws/devel/setup.bash```
* ``` roslaunch uav_mavros_simulation uav_launch.launch world:=aruco vehicle:=iris_fpv_cam sdf:=iris_fpv_down_cam ```
* /path/to/QGroundControl: ```chmod +x QGroundControl.AppImage && ./QGroundControl.AppImage```
* ``` rosrun rqt_image_view rqt_image_view ```
* ``` rosrun uav_mavros_simulation simpleDrone.py ```

## UAV commander

* at terminal run *rosrun uav_mavros_simulation simpleDrone.py* 

* `goto x y z yaw` examples : ```goto 2 2 15 1.5``` or ```goto aruco```
    *   uav 'll go to the  specified location x, y, z, yaw, or the aruco marker position
* `land [x y z yaw]` examples : ```land ```, ```land 1 5 5 1.2 ```, ```land aruco```
    *  uav 'll land at its current position or at the optional x, y, z, yaw, or at the aruco marker position
* `return`, uav will return to its home position and land
* `exit`, to close the swarm commander
