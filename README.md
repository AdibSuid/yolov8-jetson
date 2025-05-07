# yolov8-jetson
Run yolov8 & yolov11 docker container on jetpack5 & jetpack 6

For Jetpack 5, the docker container consist of:
ultralytics yolov8n
ultralytics yolov11n
ROS Noetic(Bare Bones)
ROS Foxy(Bare Bones)
ARBA oil palm tree detection weights (yolo v8)

For Jetpack 6, the docker container consist of:
ultralytics yolov8n
ultralytics yolov11n
ARBA weights (yolo v8)

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

10. Pull ultralytics docker image(if the jetson board host running jetpack 5, run this command):
    ```bash
    sudo docker pull kambing74/yolov8-jetson:latest

If the jetson board host running jetpack 6, run this command:
    ```bash
    sudo docker pull kambing74/yolov8-jetson:jetpack6
    ```

11. Run the docker container (for jetpack 5):
    ```bash
    sudo docker run -it --gpus all --ipc=host --runtime=nvidia --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix kambing74/yolov8-jetson:jetpack5
    ```
If the jetson board running jetpack 6, run this command:
    ```bash
    sudo docker run -it --gpus all --ipc=host --runtime=nvidia --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix kambing74/yolov8-jetson:latest
    ```

12. Once you are inside the docker container, go to ARBA workspace directory:
    ```bash
    cd /ultralytics/simedarby_ws/src/merba/src
    ```

13. Run python script to test the realtime video detection: 
    ```bash
    python3 test.py
