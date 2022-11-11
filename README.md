# Tensorflow-Object-Detection-Project
# Garbage classification (recyclable, other and kitchen waste)

The repository includes:  

The whole projects form Google TensorFlow Object Detection  

Source code of Garbage classification built on TensorFlow Detection Project.  

Training code for ssd_mobilenet_v1  

Pre-trained weights for faster_rcnn_inception_v2 and ssd_mobilenet_v1  

the detection code are in the detect.py (One by one photo identification) and test.py (real time detection).  

Example of training on your own dataset

# Get Start
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

# Training on ssd_mobilenet_v1
I’m providing pre-trained weights for ssd_mobilenet_v1 to make it easier to start, but you need to download the complete model file in the provided Baidu network disk link. You can use those weights as a starting point to train your own variation on the network. Training code is in Tensorflow-Object-Detection-Project\models-master\research\object_detection\train.py. You can run it directly from Windows cmd as such:
`python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training ssd/ssd_mobilenet_v1_coco.config`  

Because github restricts the uploading single file to no more than 100mb, the events.out.tfevents of some training models and the model documents of ssd_mobilenet_v1_coco_11_06_2017 used for migration learning. It needs to be uploaded to Baidu network disk.  

Link: https://pan.baidu.com/s/1RuxKbtsS8ZLSRX3i97OdeA?pwd=rst1  

Download and unzip it and overwrite it with Tensorflow-Object-Detection-Project downloaded from github.  

# Train your own dataset (take this project as an example)
## Prepare training data and test data
1.D:\python3\models-master\research\object_detection Create a new folder named images  

Then create two folders under the mages file, one named train and the other named test. The file structure is as follows(Due to Github limitations, this repository ignores uploading the dataset of this project)  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/1.png">
</div>  

`There are 9 pictures of kitchen waste, 15 pictures of recyclable waste, and 11 pictures of other waste in the test.  
There are 34 pictures of kitchen waste, 76 pictures of recyclable waste, and 31 pictures of other waste in the train.`

The image naming format is number_flip/number, and the image type is jpg format, as shown in the figure  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/2.png">
</div>
2. Label each picture and generate an xml file containing the picture label and location information. This project uses a software LabelImg, which is convenient and quick to label.(link:https://github.com/tzutalin/labelImg/files/2638199/windows_v1.8.1.zip)  

Click on the link and download the latest version, then unzip it, as shown in the figure






# Issues
1. Q: If ModuleNotFoundError: No module named 'object_detection' occurs  

A: Copy the "setup.py" in the "models\research\object_detection\packages\tf2" folder to the "models\research" directory, and then execute:  
python setup.py build  

`python setup.py install`

2. Q: If No module named 'tf_slim' appears  

A: Execute in the /research/slim folder  

`python setup.py install`  


