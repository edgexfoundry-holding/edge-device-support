# Deploy and start the program Device on Rb3

[![README](https://img.shields.io/badge/%E4%B8%AD%E6%96%87-brightgreen)](./Run_Device_CN.md)
[![README](https://img.shields.io/badge/Contents-blue)](./README.md)

## Deployment of program device

First connect Rb3 to the power supply and link Rb3 to the same local area network as PC.<br>
Then link Rb3 to the computer.<br>
Access Rb3 through the adb instruction.<br>

```buildoutcfg
$ adb shell
```

Create a new folder called ros2.<br>

```buildoutcfg
$ mkdir ros2
```

Crtl+d quits Rb3 and copies the file edgex_mqtt_ros2.tar into the Rb3 ros2 directory.<br>

```buildoutcfg
$ adb push ~/edgex_mqtt_ros2.tar /ros2
```

Re-enter Rb3 through the adb instruction and uncompress the edgex_mqtt_ros2.tar file to the current directory.<br>

```buildoutcfg
$ adb shell
$ tar -xvf edgex_mqtt_ros2.tar
```

Create a docker under a configured ROS2 environment.<br>

```buildoutcfg
$ sudo docker run --rm -it  --name ros2_env --hostname ros2_env \ 
  --network host -v $(pwd):/root/workspace ros:dashing-ros-core-bionic bash

```

Install pip3 in docker after Docker starts.<br>

```buildoutcfg
<dokcker>$ apt-get update
<dokcker>$ apt-get install python3-pip
```

Install the python library of paho-mqtt in docker.<br>

```buildoutcfg
<dokcker>$ pip3 install paho-mqtt
```

## Modify and compile

If the code is updated, it needs to be recompiled.<br>
To add a new node, you need to modify setup.py.<br>
If you add a reference to the ros package, you need to modify package.xml.<br>

```buildoutcfg
<dokcker>$ cd /root/workspace/mqtt_device/
<dokcker>$ apt install python3-colcon-common-extensions
<dokcker>$ colcon build
```

## Start the program device

Go to directory mqtt_device.<br>
Execute setup.bash files with the source command.<br>
Set environment variables ROS_DOMAIN_ID and BROKER_IP.<br>
Execute the file ros2_dev in ROS file package edgex_mqtt_ros_dev.<br>

```buildoutcfg
<docker>$ cd /root/workspace/mqtt_device/
<docker>$ source ./install/setup.bash
<docker>$ export ROS_DOMAIN_ID=<ROBOT's DOMAIN ID（Between 0 and 232）>
<docker>$ export BROKER_IP=<Local IP address>
<docker>$ ros2 run edgex_mqtt_ros_dev ros2_dev
```
It will be shown as below after successful startup.<br>

![image](./images/4.png)

[![README](https://img.shields.io/badge/Deploy_and_start_control_programs_on_Rb3-yellow)](./Initiate_Robot.md)

 