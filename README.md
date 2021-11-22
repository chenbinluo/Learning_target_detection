# 学习目标检测过程中的一些progress report及笔记


# YOLO v5 with FLIR dataset
step 1. 搭建相关环境，需要安装python, torch, torchversion,注意yolov5各个version对torch版本的要求；\
step 2. 下载数据，将15个压缩文件合并为一个，方法为在压缩文件下载的目录下打开CMD并输入“copy \B ” \
step 3. 然后使用[转json.ipynp](https://github.com/chenbinluo/Learning_target_detection/blob/main/json_to_yolo.ipynb)将train\val\vedio中的json文件转换成yolo要求的txt格式，并放入label问价夹中\
step 4. 整理数据框架，将train/val中的Annotated_ thermal_ 8_ Bit放入images文件夹内，将刚刚得到的txt问价放入labels文件夹内\
step 5. 下载yolo v5代码，并解压[下载点击](https://github.com/ultralytics/yolov5).\
step 6. 在文件夹yolov5-master下打开cmd, 并activate环境,然后pip install -r requirements.txt\
step 7. 修改models/yolov5s.yaml，将nc = 80修改为nc = 4（类别数）\
step 8. 在data文件夹下面新建一个[FLIR.yaml文件](https://github.com/chenbinluo/Learning_target_detection/blob/main/FLIR.yaml)\
step 9. 从零开始训练：python train.py --img 640 --epochs 300 --data data/FLIR.yaml --cfg models/yolov5s.yaml --weight " "\
step 10. 从预训练模型进行微调：python train.py --img 640 --epochs 300 --data data/FLIR.yaml --cfg models/yolov5s.yaml --weight weights/yolov5s.pt\

# YOLO v5 with 我自己下载的demo数据
1. 去google下载相应的图片 or 自己写一个简单的图片[爬虫](https://github.com/chenbinluo/Learning_target_detection/blob/main/%E7%88%AC%E5%8F%96%E5%9B%BE%E7%89%87.ipynb)\
2. 在文件夹yolov5-master下打开cmd, 并activate环境,然后pip install -r requirements.txt\
3. 然后pip install labelimg\
4. 在cmd输入labelimg打开该软件，按步骤open dir> 爬取图片的文件夹> create box> save的步骤手动给图片加标签并保存为xml格式文件\
5. 将xml文件分为训练测试并转为yolo标签数据，[相关代码点击1](https://github.com/chenbinluo/Learning_target_detection/blob/main/split.py) [点击2](https://github.com/chenbinluo/Learning_target_detection/blob/main/txt2yolo_label.py)\
6. 在data下增加新数据的yaml文件，做好图片和label路径的描述和类别数目的说明\
7. 在训练模型之前在yolov5-master下新建weights文件夹，并去[网页下载pt文件](https://github.com/ultralytics/yolov5/releases)将相应模型的weight放到该文件下\
8. 记得将model下对应模型的.yaml文件中nc改为刚刚用labelimg标记的类别数；
9. 然后在cmd输入python train.py --img 640 --batch 4 --epoch 300 --data ./data/myvoc.yaml --cfg ./models/yolov5m.yaml --weights weights/yolov5m.pt --workers 0即可开始训练
