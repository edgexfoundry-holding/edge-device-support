# 系统检验

[![README](https://img.shields.io/badge/English-brightgreen)](./System_Check.md)
[![README](https://img.shields.io/badge/目录-blue)](./README_CN.md)

打开EdgeX网页：<本机IP>:4000<br>
选取网关<br>

 ![image](./images/7.png)
 
点击左侧设备服务
 
 ![image](./images/8.png)
  
由于我们使用的是edgex-device-mqtt所以点击相对应的设备图标
  
 ![image](./images/9.png)
   
之后可以对机器人进行设置，角速度线速度以及获取机器人的电压<br>
对电压进行get指令后可以得到json文件进行解读后可以看到电压，如下图

 ![image](./images/10.png)

对线速度或角速度进行设定可以在log看到指令的发送如下图所示

 ![image](./images/11.png)
 
 机器人相应运动如下图所示
 
 ![image](./videos/run.gif)
 
 完整视频请点击按钮观看
 
 [![README](https://img.shields.io/badge/演示视频-orange)](./videos/Demo_Video_CN.mp4)