# Tensorflow-Object-Detection-Project
* This project is modified from the Google TensorFlow Object Detection open source project 
# Garbage classification (recyclable, other and kitchen waste)
* The repository was published by Wenhao Li  
The repository includes:  
* The whole projects form Google TensorFlow Object Detection  
* Source code of Garbage classification built on TensorFlow Detection Project.  
* Training code for ssd_mobilenet_v1  
* Pre-trained weights for faster_rcnn_inception_v2 and ssd_mobilenet_v1  
* the detection code are in the detect.py (One by one photo identification) and test.py (real time detection).  
* Example of training on your own dataset
* In the "training" folder is the checkpoint file of faster_rcnn_inception_v2, and the checkpoint file of ssd_mobilenet_v1 is stored in Baidu network disk.
* The demo of "Get Start" is based on the model trained by faster_rcnn_inception_v2

# Get Start
1. This portfolio test runs on Windows 10Pro for Workstations (19045.2193), IDE is Pycharm, and a dataset uses ssd_mobilenet_v1_coco and faster_rcnn_inception_v2 for training. Finally select faster_rcnn_inception_v2 as the recognition model
2. Python environment collocation (using Python 3.6.5, TensorFlow 1.14.0 CPU Version)
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/image.png">
</div>
3. Open detect.py in "Tensorflow-Object-Detection-Project\models-master\research\object_detection"  

4. Change "D:\\spec" in "PATH_TO_CKPT" on line 16 to the directory where the test computer is placed for the "Tensorflow Object Detection Project" (select the model location)  

5. Change "D:\\spec" in "PATH_TO_LABELS" on line 17 to the directory where the test computer is placed for the "Tensorflow Object Detection Project" (select the label location)  

6. Change "D:\\spec" in detection on line 93 to the directory where "Tensorflow Object Detection Project" places the test computer (select the location of the test image set) 
 
7. The last step is to use Pycharm to execute detect.py to output the result  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/image.png">
</div>

8. Real-time recognition as test.py in "Tensorflow-Object-Detection-Project\models-master\research\object_detection", open pycharm to execute
9. Due to the limited computer performance, the training time is not long, and the processor is used for training, so the accuracy is not high. The accuracy is about 70%.(Intel Core I5-5200U With 8GBRAM Single Channel 1600MHz DDR3)  

# Training on ssd_mobilenet_v1
I’m providing pre-trained weights for ssd_mobilenet_v1 to make it easier to start, but you need to download the complete model file in the provided Baidu network disk link. You can use those weights as a starting point to train your own variation on the network. Training code is in "Tensorflow-Object-Detection-Project\models-master\research\object_detection\train.py". You can run it directly from Windows cmd as such:
`python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training ssd/ssd_mobilenet_v1_coco.config`  

Because github restricts the uploading single file to no more than 100mb, the events.out.tfevents of some training models and the model documents of ssd_mobilenet_v1_coco_11_06_2017 used for migration learning. It needs to be uploaded to Baidu network disk.  

Links: https://pan.baidu.com/s/1RuxKbtsS8ZLSRX3i97OdeA?pwd=rst1  

Download and unzip it and overwrite it with Tensorflow-Object-Detection-Project downloaded from github.  

# Train your own dataset (take this project as an example)
## Prepare training data and test data
1."D:\spec\Tensorflow-Object-Detection-Project\models-master\research\object_detection" Create a new folder named images  

Then create two folders under the mages file, one named train and the other named test. The file structure is as follows(Due to Github limitations, this repository ignores uploading the dataset of this project)  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/1.png">
</div>  

 * There are 9 pictures of kitchen waste, 15 pictures of recyclable waste, and 11 pictures of other waste in the test.  
 * There are 34 pictures of kitchen waste, 76 pictures of recyclable waste, and 31 pictures of other waste in the train.

The image naming format is number_flip/number, and the image type is jpg format, as shown in the figure  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/2.png">
</div>  
2. Label each picture and generate an xml file containing the picture label and location information. This project uses a software LabelImg, which is convenient and quick to label.(links:https://github.com/tzutalin/labelImg/files/2638199/windows_v1.8.1.zip)  
 
* (1) Click on the link and download the latest version, then unzip it, as shown in the figure  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/3.png">
</div>  

* (2) After opening labelimg, the first step is to click Open Dir, then find "D:\spec\Tensorflow-Object-Detection-Project\models-master\research\object_detection\images\train" and click to select the folder"
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/4.png">
</div>  

* (3)Press the W key of the keyboard to start marking, as shown in the figure, select the marked object (soda can), and a dialog box will pop up, enter the label, and what I type here is ke_hui_shou (Chinese Pinyin, meaning recyclable), If it is kitchen waste, enter chu_yu, the effect is as shown in the figure
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/5.png">
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/6.png">
</div>  

* (4) The final effect is shown in the figure
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/7.png">
</div>  

* (5) Then collect all the xml into a csv file, you need to use Python code to achieve, in the "Tensorflow-Object-Detection-Project" directory, run "transfer from xml to csv.py"  
PS:The path needs to be modified before running "transfer from xml to csv.py". Change "D:\\spec" in the path on lines 13 and 14 to the directory where Tensorflow Object Detection Project places the test computer.  
* (6) Run the above code to generate the csv file as shown below
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/8.png">
</div>

* (7) Similarly, the pictures in the test are also marked and converted according to steps (2)-(6). Attention:
    * The path of step (2) needs to be changed to "Project directory\Tensorflow-Object-Detection-Project\models-master\research\object_detection\images\test"
    * The path of step (5) needs to change the path of "D:\spec" to the location directory of the computer where the Tensorflow Object Detection Project is located, and change the trash_train.csv on line 40 to trash_test.csv

* (8) Because the input data format of the Tensorflow object detection API is in TFRcords Format, we need to convert the csv file into a record file, first copy and paste the trash_train.csv and trash_test.csv generated above to "D:\spec\Tensorflow-Object-Detection-Project\models-master\research\object_detection\data" and "D:/spec" is changed to the directory where TensorFlow Object Detection is located, as shown in the figure
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/9.png">
</div>  

* (9) Then you need to use Python code to convert csv to record. The code is as follows, copy and paste the following code into a file named generate_TFR.py under "D:\python3\models-master\research\object_detection"  
* (10) Then you need to use Python code to convert csv to record. The code is in the file named "generate_tfr.py" under "TensorFlow-Object-Detection\models-master\research\object_detection"  
Conversion steps：  
    * Two changes are required
        * In line 12, you need to change "D:\\spec" in the path "D:\\spec\\Tensorflow-Object-Detection-Project\\models-master\\research\\object_detection" to the computer to store Tensorflow-Object-Detection-Project location
        * Lines 22 to 35 need to be changed to the categories marked in labelImg as shown in the figure. Write as many categories as there are. Here, this project is divided into 5 categories
        * In line 87, if train.record is generated, it should be changed to "Tensorflow-Object-Detection-Project\\models-master\\research\\object_detection\\images\\train": (training set image path)  
Then execute `python generate_TFR.py --csv_input=data/trash_train.csv --output_path=data/train.record`
        * In line 87, if test.record is generated, it should be changed to "Tensorflow-Object-Detection-Project\\models-master\\research\\object_detection\\images\\test": (training set image path)  
Then execute `python generate_TFR.py --csv_input=data/trash_test.csv --output_path=data/test.record`  
The following picture appears, the conversion is successful
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/10.png">
</div> 
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/11.png">
</div>  

3. Profiles and Models  
This project selects ssd_mobilenet_v1_coco.config, copy ssd_mobilenet_v1_coco.config in the "object_detection\ssd_mobilenet_v1_coco_11_06_2017" file, and create a new folder named training ssd in the "\object_detection directory", and put ssd_mobilenet_v1_coco.config in the training ssd folder ,As shown below
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/12.png">
</div>  

* (1) Use pycharm to open ssd_mobilenet_v1_coco.config for modification  
* (2) Modify "input_path:" on line 175, and change the path to "D:\\spec\\Tensorflow-Object-Detection-Project\\models-master\\research\\object_detection\\data\\train.record". Where "D:\\spec" should be changed to the project where the project is located.  
* (3) Modify "input_path:" on line 177, and change the path to "D:\\spec\\Tensorflow-Object-Detection-Project\\models-master\\research\\object_detection\\data\\trash.pbtxt". Where "D:\\spec" should be changed to the project where the project is located.  
* This input_path is the path of the test data, change it to the corresponding path  

* (4) Modify "input_path:" on line 189, and change the path to "D:\\spec\\Tensorflow-Object-Detection-Project\\models-master\\research\\object_detection\\data\\test.record". Where "D:\\spec" should be changed to the project where the project is located.  
* (5) Modify "input_path:" on line 191, and change the path to "D:\\spec\\Tensorflow-Object-Detection-Project\\models-master\\research\\object_detection\\data\\trash.pbtxt". Where "D:\\spec" should be changed to the project where the project is located
* This input_path is the path of the training data, change to the corresponding path  
* (6) Modify "num_classes: " in line 9, this project is divided into 6 categories, so it is 6  
* The trash.pbtxt file at (3) and (5) modified above needs to be created by yourself, you can copy a file and then change the file name, as shown in the figure
    * The trash.pbtxt file at (3) and (5) modified above needs to be created by yourself, and then write as many categories as there are in this format.
    </div>  
    <div align=center>
    <img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/13.png">
    </div>  
* The configuration is now complete, start training  

4. Train the model
Just execute `python train.py --logtostderr --train_dir=training ssd/ --pipeline_config_path=training ssd/ssd_mobilenet_v1_coco.config`in cmd openning in "Tensorflow-Object-Detection-Project\models-master\research\object_detection"
* Attention:  
    * If you download the training ssd provided by the Baidu network disk file for coverage in this project, you need to delete the pre-training file of this project before training, and then put the ssd_mobilenet_v1_coco.config file configured in (1)-(6) into the training ssd and then execute the training instructions in this step  
* When you see the content shown in the figure below, it proves that the training is in progress:
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/14.png">
</div>  

* You can see the optimization situation through the visual page
    * Open the cmd window in the "models-master\research\object_detection" directory  
Execute `tensorboard --logdir=training ssd` and the following figure appears  
    </div>  
    <div align=center>
    <img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/15.png">
    </div>  
    
    * Copy the address of the white box in the above picture to a web browser to open it, and the interface shown in the figure below will appear.  
    </div>  
    <div align=center>
    <img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/16.png">
    </div>   

5. Test the trained model  
* When the number of training steps is enough, you can try to close the cmd window that runs the training model, and use the export_inference_graph.py that comes with the Object Detection API to export the model to check the detection effect. Before running it, you need to pass in config and other related information, parameters, and create a test folder in the "object_detection\" directory (take the garbage classification of this project as an example)
Open cmd in the "models-master\research\object_detection" directory and execute this command(xxxx is the trained checkpoint）    
`python export_inference_graph.py \ --input_type image_tensor \ --pipeline_config_path training ssd/ssd_mobilenet_v1_coco.config \ --trained_checkpoint_prefix training ssd/model.ckpt-xxxx \ --output_directory testing`  
    * Attention:
        * "--output_directory" is the folder name of the output model, "trained_checkpoint_prefix" is the prefix we want to convert the model checkpoint to, and "pipeline_config_path" is the location of the training configuration file "ssd_mobilenet_v1_coco.config".  
 * After running the above command, the "testing" folder will be generated under the object_detection folder, as shown in the figure below.
</div>  
<div align=center>
<img src="https://github.com/leo770/Tensorflow-Object-Detection-Project/blob/main/img-folder/17.png">
</div>   

6. Finally, our model has been constructed.

# Test your own model
* As with the model trained by the previous Get Start call in this project, change the path in step 4 of "Get Start" to the path location of the model "testing" just exported.
* "Get Start" step 5 is changed to the "pbtxt" document path created in step 6 in "Profiles and Models" in "Train your own dataset".
* Store the test image you are looking for in step 6 of "Get Start", and then run "detect.py" in pycharm to see the recognition effect


    
    




# Issues
1. Q: If ModuleNotFoundError: No module named 'object_detection' occurs  

A: Copy the "setup.py" in the "models\research\object_detection\packages\tf2" folder to the "models\research" directory, and then execute:  
python setup.py build  

`python setup.py install`

2. Q: If No module named 'tf_slim' appears  

A: Execute in the /research/slim folder  

`python setup.py install`  


