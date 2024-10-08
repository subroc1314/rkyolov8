## 1.训练并导出ONNX模型  
克隆YOLOv8仓库  
```git clone https://github.com/ultralytics/ultralytics.git
由于YOLOv8的官方仓库主分支已变为YOLO11，这里切换v8分支
```cd ultralytics
```git checkout a05edfbc27d74e6dce9d0f169036282042aadb97
改写ONNX模型输出的代码，将onnx.patch放置ultralytics主目录下
```git apply onnx.patch
