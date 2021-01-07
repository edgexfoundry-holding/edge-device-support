# Deploy and start control programs on Rb3

[![README](https://img.shields.io/badge/%E4%B8%AD%E6%96%87-brightgreen)](./Initiate_Robot_CN.md)
[![README](https://img.shields.io/badge/Contents-blue)](./README.md)

Create docker to start the robot and publish the robot parameters.<br>

```buildoutcfg
$ sudo docker run --rm -it --name robot --network host aarch64universal/turtlebot3ros2:0.1.1 bash 
```

Set the environment variables ROS_DOMAIN_ID, BROKER_IP and TURTLEBOT3_MODEL<br>

```buildoutcfg
<docker>$ export ROS_DOMAIN_ID=<ROBOT's DOMAIN ID（Between 0 and 232）>
<docker>$ export BROKER_IP=<Local IP address>
<docker>$ export TURTLEBOT3_MODEL=burger
```

Execute setup.bash files with the source command<br>

```buildoutcfg
<docker>$ source /root/turtlebot3_ws/install/setup.bash
```

Execute the file robot_launch.launch.py in the ROS package launch cpp_vel_report.<br>

 ```buildoutcfg
<docker>$ ros2 launch cpp_vel_report robot_launch.launch.py
```

 ![image](./images/6.png)<br>
 
 
 
 [![README](https://img.shields.io/badge/Check_whether_the_system_is_running_successfully-yellow)](./System_Check.md)