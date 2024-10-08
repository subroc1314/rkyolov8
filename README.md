## 1.训练并导出ONNX模型  
克隆YOLOv8仓库  
```
git clone https://github.com/ultralytics/ultralytics.git
```  
由于YOLOv8的官方仓库主分支已变为YOLO11，这里切换v8分支  
```
cd ultralytics  
git checkout a05edfbc27d74e6dce9d0f169036282042aadb97  
```  
改写修改ONNX模型输出的代码，将onnx.patch放置ultralytics主目录下  
```
git apply onnx.patch  
```
代码修改完成后主目录多了一个export_onnx.py文件，再新建名weights的文件夹，将训练好模型***.pt文件放置weights文件夹下  
注意export_onnx.py中模型名称和尺寸（n s m l）yaml文件的与训练好的模型匹配  
```
python export_onnx.py
```
运行后在weights文件夹中生成onnx模型  

## 2.导出RKNN模型  
在toolkit环境下运行convert_rknn.py  
在convert_rknn.py中修改ONNX模型位置，生成RKNN模型名称，量化校准集位置，是否量化，模型标签名称，测试图片位置，建议同一目录下  
```
python convert_rknn.py
```
运行后生成rknn模型和测试图片推理结果  

## 3.板端推理
根据模型修改src/process/postprocess.cpp中第59行class_num=检测类别数量  
根据模型修改src/task/yolov8_custom.cpp中第8行模型检测标签，编译  
```
mkdir build && cd build
cmake ../ && make
```
build文件生成三个可执行文件，分别推理图片，视频，线程池推理
```
./yolov8_img [模型地址] [图像地址]  
 
./yolob8_video [模型地址] [视频地址] [写1或者不写，1表示将结果保存，默认不存结果]  
 
./yolov8_thread_pool [模型地址] [视频地址] [线程数]  
```
