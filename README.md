# OUR-PALS-BOT
**Please drop a star ⭐ if you like the project.**

  *It should be noted that though most commits are from [suryachereddy](https://github.com/OUR-PALS/OUR-PALS-BOT), 3 others ([darshan1215](https://github.com/darshan1215), [Amulya Ganti](https://github.com/ganti0907) and [Sriya027](https://github.com/Sriya027)) have also contributed for the project (including parts of the code). We thank [Dr. Chakravarthula Kiran](https://github.com/kirandotc) (our faculty guide) and [Srujan Panuganti](https://github.com/srujanpanuganti) for their valuable inputs to the project.*
This repo contains the Arduino firmware for the 4WD bot, we used Teensy 4.1 for this project.

### Topics that are subscribed by the robot:
1. /cmd_vel

### Topics that are published by the robot [these are the individual encoder ticks of each motor]:
1. /lfwheel
2. /lbwheel
3. /rfwheel
4. /rbwheel


# Pin binding for Teensy 4.1:
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
*We have not used it for this project now, but our future plan is to develop better localisation by fusing IMU data with motor ticks. You're free to implement this and submit a pull request to our repository(-ies).*
1. SDA = 18
2. SCL = 19

# Setting Up Camera Stream on Raspberry Pi
It should also be noted that we didn't integrate video stream with ROS. Instead we used used a WLAN based RPi camera stream server. For a RPi camera server, you may follow [this](https://ubuntu.com/blog/how-to-stream-video-with-raspberry-pi-hq-camera-on-ubuntu-core) guide (note: In the tutorial, /boot/uboot/config.txt may not be availabe instead it will be available /boot/firmware/config.txt). It should be noted that [raspi-config](https://ubuntu.com/blog/how-to-stream-video-with-raspberry-pi-hq-camera-on-ubuntu-core) must be installed to activate Pi Camera. 
We've used RPi 4- 4GB. **use Ubuntu 18 32 bit, using 64 bit won't support Pi Cam.**


# Steps to Start the bot
*Please clone and build the [ourpals_iris](https://github.com/OUR-PALS/ourpals_iris) package on your desktop/laptop before you proceed.*
1. In both, RPi and desktop setup ROS network name resolution. refer section 2 of [this link](http://wiki.ros.org/ROS/NetworkSetup). In our case SSH in  RPi:  `export ROS_IP=<RPi-IP-Address>`  and in desktop: `export ROS_IP=<desktop-IP-Address>`. *(you can find the IP address of both using a simple IP scanning app on your mobile or desktop connected to the same WLAN)*
2. As we are running ROS Core in RPi, in both desktop and RPi: `export ROS_MASTER_URI=<RPi-IP-Address>` (refer [this link](http://wiki.ros.org/ROS/Tutorials/MultipleMachines)).
3. It should be noted that it is recommended to perform step 1 & 2 to every terminal that you open.
4. In RPi: `roscore`, `rosrun rosserial_python serial_node.py /dev/ttyACM0 __name:=serial1` and `rosrun rosserial_python serial_node.py /dev/ttyACM1 __name:=serial2`  
5. In desktop, you may use [teleop_twist_keyboard](http://wiki.ros.org/teleop_twist_keyboard) (for testing): `rosrun teleop_twist_keyboard teleop_twist_keyboard.py`
6. Build the [OURPALS IRIS](https://github.com/OUR-PALS/ourpals_iris.git) package using a Catkin workspace. To run the script: `rosrun ourpals_iris iris_realtime.py`


*For any doubts regarding the project feel free to ask in "issues".*

