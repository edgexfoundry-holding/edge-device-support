# Check whether the system is running successfully

[![README](https://img.shields.io/badge/%E4%B8%AD%E6%96%87-brightgreen)](./System_Check_CN.md)
[![README](https://img.shields.io/badge/Contents-blue)](./README.md)

Open the EdgeX page: (Local IP address):4000<br>
Choose a gateway.<br>

 ![image](./images/7.png)
 
Click the device service button on the left.<br>

 ![image](./images/8.png)
 
Because we use edgex-device-mqtt, click the corresponding device icon.<br>

 ![image](./images/9.png)
 
The robot can then be set, the angular velocity, linear speed and the voltage of the robot can be controled and obtained.<br>
After getting the voltage instruction, you can copy the json file to interpret website, and then you can see the voltage inside the json file, as shown in the figure below.<br>

 ![image](./images/10.png)<br>
 
Setting the linear speed or angular velocity can see the sending of instructions in logs as shown in the figure below.
 
  ![image](./images/11.png)
  
Corresponding movement of the robot as shown below.
  
  ![image](./videos/run.gif)
  
Please click the button to watch the full video.
 
 [![README](https://img.shields.io/badge/Demo_Video-orange)](./videos/Demo_Video.mp4)