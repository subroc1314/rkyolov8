## 1.训练并导出ONNX模型  
克隆YOLOv8仓库  <br>
```git clone https://github.com/ultralytics/ultralytics.git<br>
由于YOLOv8的官方仓库主分支已变为YOLO11，这里切换v8分支<br>
```cd ultralytics<br>
```git checkout a05edfbc27d74e6dce9d0f169036282042aadb97<br>
改写ONNX模型输出的代码，将onnx.patch放置ultralytics主目录下<br>
```git apply onnx.patch<br>
