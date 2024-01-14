# Articubot Customized Fork

This repository is a fork of Josh Newans' Articubot, with customizations to enhance compactness and includes a personalized URDF file. The modifications are designed to offer improved performance and aesthetics based on individual preferences.
The following is the 3D model for this particular design:
https://www.thingiverse.com/thing:6423686

## Dependencies

Before proceeding, ensure that you have the following dependencies installed:

- **ROS 2 Foxy Fitzroy Packages:**
  ```bash
  sudo apt install ros-foxy-rviz2
  sudo apt install ros-foxy-gazebo-ros-pkgs
  sudo apt install ros-foxy-gazebo-ros2-control
  ```

- **Raspberry Pi Support for lidar:**
  ```bash
  sudo apt install ros-foxy-rplidar-ros
  ```

- **Joystick and Control Packages:**
  ```bash
  sudo apt install joystick jstest-gtk evtest
  sudo apt install ros-foxy-twist-mux
  ```

- **SLAM Toolbox and Navigation2:**
  ```bash
  sudo apt install ros-foxy-slam-toolbox
  sudo apt install ros-foxy-navigation2 ros-foxy-nav2-bringup
  ```

- **Serial Communication Packages:**
  ```bash
  sudo apt install python3-serial
  ```

- **Additional Packages:**
  ```bash
  sudo apt install ros-foxy-image-transport-plugins
  sudo apt install ros-foxy-rqt-image-view
  ```

- **Development Machine Dependency:**
  ```bash
  git clone https://github.com/joshnewans/serial_motor_demo.git
  ```

## Usage (These are just the generally confusing commands)
### Main commands
To launch the robot, use the following command on the robot:
```bash
cd robot_ws/
source install/setup.bash 
ros2 launch articubot_one launch_robot.launch.py
```
To launch the lidar, use the following command:
```bash
cd robot_ws/
source install/setup.bash 
ros2 launch articubot_one rplidar.launch.py
```
To launch the camera, use the following command:
```bash
cd robot_ws/
source install/setup.bash 
ros2 launch articubot_one camera.launch.py
```

### Mapping

To perform mapping, use the following command on the dev machine:
```bash
ros2 launch slam_toolbox online_async_launch.py params_file:=./src/articubot_one/config/mapper_params_online_async.yaml use_sim_time:=false
```

### Navigation

For navigation, execute the following command on the dev machine:
```bash
ros2 launch nav2_bringup navigation_launch.py use_sim_time:=false
```

### Teleoperation (Keyboard)

To use the teleop keyboard, run the following command on the dev machine:
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped
```
### Joystick

To launch the joystick program, run on the dev machine:
```bash
ros2 launch articubot_one joystick.launch.py
```

### Rviz2

To open Rviz2 with a specific configuration, run on the dev machine:
```bash
rviz2 -d src/articubot_one/config/main.rviz
```

## Custom URDF

This program's URDF file is eddited according to my design, It is designed to be compact and easy to print and assemble, the whole print is just one piece and has place holders for all the components.
