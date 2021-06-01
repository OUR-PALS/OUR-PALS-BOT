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
4. Motor_br = 19,18

### IMU [MPU6050]:
1. SDA = 17
2. SCL = 16

   