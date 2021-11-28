# Pascal Voc Dataset Results 

I ran the tests a few times and they are generally consistent. The results in the table aren't averages. Once I run them a few more times, I will update it with averages.

## Hardware Specs

### M1 Macbook Air
* M1
* 8 GPU
* 8 CPU
* 16G unified memory
* Monterey
* CreateML 3

### M1 Max Macbook Pro
* M1 Max
* 24 GPU
* 2/8 CPU
* 32G unified memory
* Monterey
* CreateML 3

## Pascal Dataset

* training 13,299 
* validation 3,302 
* classes 20
* zipped file 

## Table of results

Screen shots of each run is in the folders.

* ET - elapsed time is in minutes from the reported start and finish
* training accuracy is the final average accuracy across all classes
* validation accuracy is the final average accuracy across all classes
* top class Intersetion/Union reported from the training dataset
* top class Intersetion/Union reported from the validation dataset

|Batch size | M1 ET | M1Max ET | M1 Train Acc | M1Max Train Acc |
|-----------|:------|:---------|:-------------|:----------------|
| 16       | 14 min | 7 min    | 37           | 38              |
| 32       | 21 min | 11 min   | 45           | 44              |
| 64       | 35 min | 17 min   | 47           | 48              |
| 128      | 64 min | 30 min   | 51           | 51              |


## References

[https://developer.apple.com/documentation/createml/mlobjectdetectormetrics] - Documentation on intersection/union and what Apple means in the context of object detection. If you're new to YOLO, read the paper to get a better understanding.

[https://pjreddie.com/darknet/yolov2/] - YOLOv2 website

[https://pjreddie.com/media/files/papers/YOLOv3.pdf] - YOLOV3 paper

## Observations

During the training, the GPU was above 90% utilization. CPU usage was around 50%. Performance was similar to COCO Dataset.

