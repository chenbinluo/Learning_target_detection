# Learning_target_detection
step 1. 搭建相关环境，需要安装python, torch, torchversion,注意yolov5各个version对torch版本的要求；\
step 2. 下载数据，将15个压缩文件合并为一个，方法为在压缩文件下载的目录下打开CMD并输入“copy \B ” \
step 3. 然后使用转json.ipynp将train\val\vedio中的json文件转换成yolo要求的txt格式，并放入label问价夹中\
step 4. 整理数据框架，将train/val中的Annotated_ thermal_ 8_ Bit放入images文件夹内，将刚刚得到的txt问价放入labels文件夹内\
step 5. 下载yolo v5代码，并解压[下载点击](https://github.com/ultralytics/yolov5).\
step 6. 在文件夹yolov5-master下打开cmd, 并activate环境,然后pip install -r requirements.txt\
step 7. 修改models/yolov5s.yaml，将nc = 80修改为nc = 4（类别数）\
step 8. 在data文件夹下面新建一个[FLIR.yaml文件](https://github.com/chenbinluo/Learning_target_detection)\
step 9. 从零开始训练：python train.py --img 640 --epochs 300 --data data/FLIR.yaml --cfg models/yolov5s.yaml --weight " "\
step 10. 从预训练模型进行微调：python train.py --img 640 --epochs 300 --data data/FLIR.yaml --cfg models/yolov5s.yaml --weight weights/yolov5s.pt\

# 使用自己构造的数据集
1. 去google下载相应的图片 or 自己写一个简单的图片[爬虫](https://github.com/chenbinluo/Learning_target_detection)\
2. 在文件夹yolov5-master下打开cmd, 并activate环境,然后pip install -r requirements.txt\
3. 然后pip install labelimg\
4. 在cmd输入labelimg打开该软件，按步骤open dir> 爬取图片的文件夹> create box> save的步骤手动给图片加标签并保存为xml格式文件\
5. 将xml文件分为训练测试并转为yolo标签数据，[相关代码点击](https://github.com/chenbinluo/Learning_target_detection)\
6. 
