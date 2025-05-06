# yolov8-jetson
Instruction to run yolov8 docker container on jetpack 6

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
   t=ultralytics/ultralytics:latest-jetson-jetpack6
   sudo docker pull $t && sudo docker run -it --ipc=host --runtime=nvidia $t

8. Convert model to TensorRT & run inference
   ```bash
   # Export a YOLOv8n PyTorch model to TensorRT format
   yolo export model=yolov8n.pt format=engine  # creates 'yolov8n.engine'

   # Run inference with the exported model
   yolo predict model=yolov8n.engine source='https://ultralytics.com/images/bus.jpg'
