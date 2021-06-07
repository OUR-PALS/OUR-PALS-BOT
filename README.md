# OUR-PALS-BOT
This repo contains the code for the 4WD bot and the ODOM code [to do] that will be offloaded to RPI 4b.

### Topics that are subscribed by the robot:
1. cmd_vel

### Topics that are published by the robot [these are the individual encoder ticks of each motor]:
1. lfwheel
2. lbwheel
3. rfwheel
4. rbwheel


# Pin binding:
### Encoders:
1. Encoder_fl = 9,8
2. Encoder_bl = 11,10
3. Encoder_fr = 4,5
4. Encoder_br = 6,7

### Motors:
1. Motor_fl = 20,21
2. Motor_bl = 22,23
3. Motor_fr = 15,14
4. Motor_br = 17,16

### Motor PWM:
1. PWM_FL = 2
2. PWM_BL = 3
3. PWM_FR = 0
4. PWM_BR = 1

### IMU [MPU6050]:
1. SDA = 18
2. SCL = 19

# Setting Up Raspberry Pi and Teensy

We used RPi 4- 4GB, This project is built on ROS Melodic, use Ubuntu 18 (32 bit, using 64 bit won't support Pi Cam). For a RPi camera server, you may follow [this](https://ubuntu.com/blog/how-to-stream-video-with-raspberry-pi-hq-camera-on-ubuntu-core) guide (note: In the tutorial, /boot/uboot/config.txt may not be availabe instead it will be available /boot/firmware/config.txt). It should be noted that [raspi-config](https://ubuntu.com/blog/how-to-stream-video-with-raspberry-pi-hq-camera-on-ubuntu-core) must be installed to activate Pi Camera.







# Steps to Start the bot
1. In both, RPi and desktop setup ROS network name resolution. refer section 2 of [this link](http://wiki.ros.org/ROS/NetworkSetup). In our case SSH in  RPi:  `export ROS_IP=192.168.0.52`  and in desktop: `export ROS_IP=192.168.0.70` 
2. As we are running ROS Core in RPi, in both desktop and RPi: `export ROS_MASTER_URI=http://192.168.0.52:11311` (refer [this link](http://wiki.ros.org/ROS/Tutorials/MultipleMachines)).
3. It should be noted that it is recommended to perform step 1 & 2 to every terminal that you open.
4. In RPi: `roscore` and `rosrun rosserial_python serial_node.py /dev/ttyACM0` 
5. In desktop, you may use [teleop_twist_keyboard](http://wiki.ros.org/teleop_twist_keyboard): `rosrun teleop_twist_keyboard teleop_twist_keyboard.py`