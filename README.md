# yolov8-jetson
Instruction to run yolov8 & yolov11 docker container on jetpack 6

## Quick Start (Docker Container)

1. Clone jetson-container repository:
   ```bash
   git clone https://github.com/dusty-nv/jetson-containers.git

2. go to jetson-container directory:
   ```bash
   cd jetson-containers

3. Install the packages:
   ```bash
   bash install.sh

3. Install x11 xserver on host machine:
   ```bash
   sudo apt-get install x11-xserver-utils

   xhost +local:docker

7. Pull ultralytics docker container:
   ```bash
   sudo docker pull kambing74/yolov8-jetson:latest

3. Run the docker container:
   ```bash
   sudo docker run -it --gpus all --ipc=host --runtime=nvidia --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix kambing74/yolov8-jetson:latest

8. Once you are inside the docker container, go to ARBA workspace directory
   ```bash
   cd /ultralytics/simedarby_ws/src/merba/src

9. Run python script to test the realtime video detection: 
   ```bash
   python3 test.py
