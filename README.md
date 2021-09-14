# Learning_target_detection
step 1. 搭建相关环境，需要安装python, torch, torchversion,注意yolov5各个version对torch版本的要求；\
step 2. 下载数据，将15个压缩文件合并为一个，方法为在压缩文件下载的目录下打开CMD并输入“copy \B ” \
step 3. 然后使用转json.ipynp将train\val\vedio中的json文件转换成yolo要求的txt格式，并放入label问价夹中\
step 4. 整理数据框架，将train/val中的Annotated_ thermal_ 8_ Bit放入images文件夹内，将刚刚得到的txt问价放入labels文件夹内\
step 5. 下载yolo v5代码，并解压[下载点击](https://github.com/ultralytics/yolov5).\
step 6. 在文件夹yolov5-master下打开cmd, 并activate环境,然后pip install -r requirements.txt\
step 7. 修改models/yolov5s.yaml，将nc = 80修改为nc = 4（类别数）\
step 8. 在data文件夹下面新建一个FLIR.yaml文件\
step 9. 从零开始训练：python train.py --img 640 --epochs 300 --data data/FLIR.yaml --cfg models/yolov5s.yaml --weight " "\
step 10. 从预训练模型进行微调：python train.py --img 640 --epochs 300 --data data/FLIR.yaml --cfg models/yolov5s.yaml --weight weights/yolov5s.pt\
