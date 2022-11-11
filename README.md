# Tensorflow-Object-Detection-Project
# Garbage classification (recyclable, other, kitchen waste, hazardous waste)

1. This portfolio test runs on Windows 10Pro for Workstations (19045.2193), IDE is Pycharm, and a dataset uses ssd_mobilenet_v1_coco and faster_rcnn_inception_v2 for training. Finally select faster_rcnn_inception_v2 as the recognition model
2. Python environment collocation (using Python 3.6.5, TensorFlow 1.14.0 CPU Version)
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/image.png">
</div>
3. Open detect.py in Tensorflow-Object-Detection-Project\models-master\research\object_detection  

4. Change D:\\spec in "PATH_TO_CKPT" on line 16 to the directory where the test computer is placed for the Tensorflow Object Detection Project (select the model location)  

5. Change D:\\spec in "PATH_TO_LABELS" on line 17 to the directory where the test computer is placed for the Tensorflow Object Detection Project (select the label location)  

6. Change D:\\spec in detection on line 93 to the directory where Tensorflow Object Detection Project places the test computer (select the location of the test image set) 
 
7. The last step is to use Pycharm to execute detect.py to output the result  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/image.png">
</div>

8. Real-time recognition as test.py in Tensorflow-Object-Detection-Project\models-master\research\object_detection, open pycharm to execute
9. Due to the limited computer performance, the training time is not long, and the processor is used for training, so the accuracy is not high. The accuracy is about 70%.(Intel Core I5-5200U With 8GBRAM Single Channel 1600MHz DDR3)  

# Issues
1. Q: If ModuleNotFoundError: No module named 'object_detection' occurs  

A: Copy the "setup.py" in the "models\research\object_detection\packages\tf2" folder to the "models\research" directory, and then execute:  
python setup.py build  

`python setup.py install`

2. Q: If No module named 'tf_slim' appears  

A: Execute in the /research/slim folder  

`python setup.py install`  

Because github restricts the uploading single file to no more than 100mb, the events.out.tfevents of some training models and the model documents of ssd_mobilenet_v1_coco_11_06_2017 used for migration learning. It needs to be uploaded to Baidu network disk.  

Link: https://pan.baidu.com/s/1qBXpHb-EGXb5F7oNsQDprA?pwd=x4fl  

Download and unzip it and overwrite it with Tensorflow-Object-Detection-Project downloaded from github.
