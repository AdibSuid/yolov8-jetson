# yolov8-jetson
Instruction to run yolov8 & yolov11 docker container on jetpack 6

## Quick Start

1. Clone JetsonHacks github repo to easily install docker:
   ```bash
   git clone https://github.com/jetsonhacks/install-docker.git

2. go to install-docker directory:
   ```bash
   cd install-docker

3. Install docker (version 27.5.1):
   ```bash
   bash ./install_nvidia_docker.sh

4. Configure docker (add ourselves to the docker group):
   ```bash
   bash ./configure_nvidia_docker.sh

5. Reboot jetson device for the changes to take effect:
   ```bash
   sudo reboot

6. Unhold & upgrade docker:
   ```bash
   base ./unhold_and_upgrade_docker.sh

7. Check docker version:
   ```bash
   docker --version

8. Downgrade docker(if nothing appeared after checked the docker version):
   ```bash
   base ./unhold_and_upgrade_docker.sh

9. Run these two commands to install x11 xserver on host machine:
   ```bash
   sudo apt-get install x11-xserver-utils

   xhost +local:docker

10. Pull ultralytics docker image:
   ```bash
   sudo docker pull kambing74/yolov8-jetson:latest

11. Run the docker container:
   ```bash
   sudo docker run -it --gpus all --ipc=host --runtime=nvidia --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix kambing74/yolov8-jetson:latest

12. Once you are inside the docker container, go to ARBA workspace directory
   ```bash
   cd /ultralytics/simedarby_ws/src/merba/src

13. Run python script to test the realtime video detection: 
   ```bash
   python3 test.py
