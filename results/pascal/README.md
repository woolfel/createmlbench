# Pascal Voc Dataset Results 

I ran transfer learning with Pascal Dataset on both 2020 M1 Macbook Air and 2021 M1 Max Macbook Pro. Both systems have the same release of XCode, CreateML and Monterey.

## Hardware Specs

### M1 Macbook Air
* M1
* 8 GPU
* 4/4 CPU
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

|Batch size | M1 ET  | M1Max ET | M1 Train Acc | M1Max Train Acc |
|-----------|:-------|:---------|:-------------|:----------------|
| 16        | 14 min | 7 min    | 37           | 38              |
| 32        | 21 min | 11 min   | 45           | 44              |
| 64        | 35 min | 17 min   | 47           | 48              |
| 128       | 64 min | 30 min   | 51           | 51              |


## References

[https://github.com/woolfel/createmlbench/blob/main/results/pascal/m1air.md] - Full M1 Air results

[https://github.com/woolfel/createmlbench/blob/main/results/pascal/m1max_results.md] - Full M1 Max MBP results

[https://developer.apple.com/documentation/createml/mlobjectdetectormetrics] - Documentation on intersection/union and what Apple means in the context of object detection. If you're new to YOLO, read the paper to get a better understanding.

[https://pjreddie.com/darknet/yolov2/] - YOLOv2 website

[https://pjreddie.com/media/files/papers/YOLOv3.pdf] - YOLOV3 paper

## Observations

In terms of training accuracy, the differences were not significant. I ran the test several times and observed the final training and validation accuracy varied 1-2%. Some runs on M1Max were better than M1, but then other runs M1 was better. Using M1Max, the training times were generally faster by 2x. The extra memory means you can easily run batch sizes larger than 64 with zero memory pressure. As of November 28, there's reports of memory leak with MacOS Monterey. Apple appears to have a fix in the pipeline, so hopefully in a few weeks it will be released. To get around the Monterey memory leak, I made sure to restart if I noticed the memory usage was above 5G. 

