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

7. Pull ultralytics docker container:
   ```bash
   sudo docker pull kambing74/yolov8-jetson:latest && sudo docker run -it --gpus all --ipc=host --runtime=nvidia --privileged kambing74/yolov8-jetson:latest

8. Go to ARBA workspace directory
   ```bash
   cd /ultralytics/simedarby_ws/src/weights

9. Run inference (without gui)
   ```bash
   yolo predict model=MeRBA-1n.pt source=0 show=False
