# Signature_detectuin_custom_yolo5

# Objective 

We wanna detect the signature from different documents by tunning yoloy v5 

# Dataset 
You can find it [here](https://drive.google.com/file/d/1gew1zSfSZKiUKGPGc3bpGXbO03HvE9-_/view) 
This dataset consists of four folders:
- ‘TrainImages’ folder : contains the training images (660 images) 
for the detection task

- ‘TrainGroundTruth’ folder: contains the corresponding detection 
labels (660 files) for training detection task

• Each image in ‘TrainImages’ folder has a corresponding 
text file in this folder with the same name as the image

• The text file has (1 or more) rows. Each row represents the 
bounding box of a single signature.

• Each row has 4 values: x1,y1,x2,y2

- ‘TestImages’ folder : contains the training images (115 images) for 
the detection task

- ‘TestGroundTruth’ folder: contains the corresponding detection 
labels (115 files) for testing the detection task

# Steps 

## 1: data preparation 

we have to make txt files in yolo txt file format as :
 
- 1:  IN OUR DATASET WE HAVE DIM OF TWO POINTS  INSTEAD OF center  POINT , WIDTH AND HEIGHT SO WE HAVE TO CONVERT IT and **normalize the dim**  

- 2: txt files should be in the same folder of images but in our data they aren't 

I handeled them using two fuctions (convert_xy_to_xywh , data_preparing)

## 2: Tuning the model 

- change the yaml file to contain your specific data :

      train :  /content/dataset/TrainImages

      val :  /content/dataset/TestImages

      nc : 1

      names : ["sinature"]
- run this line 
!python /content/yolov5/train.py --img-size 640 --batch-size 16 --epochs 5 --data dataset.yaml --cfg /content/yolov5/models/yolov5s.yaml --weights yolov5s.pt

## FINALLY _Evaluation  

- After getting your  CUSTOMIZED YOLO, you can find it in this path ( yolov5/runs/train/exp/weights/last.pt)

- test it at any image 
- 
![image](https://user-images.githubusercontent.com/84232181/229382086-2b30e002-9443-4b26-a712-154c1e46be35.png)
