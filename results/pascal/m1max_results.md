# Pascal Voc Dataset Results for M1 Max Macbook Pro

I ran the tests a few times and they are generally consistent. The results in the table aren't averages. Once I run them a few more times, I will update it with averages.

## Hardware Specs
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

* elapsed time is in minutes from the reported start and finish
* training accuracy is the final average accuracy across all classes
* validation accuracy is the final average accuracy across all classes
* top class Intersetion/Union reported from the training dataset
* top class Intersetion/Union reported from the validation dataset

|Batch size | elapsed time | Train Accuracy | Validation Accuracy | Top Train I/U | Top Val I/U | Peak Memory |
|-----------|:-------------|:---------------|:--------------------|:--------------|:------------|:------------|
| 16       | 7 min      | 38             | 37                  | 71            | 67         | 1.55G |
| 32       | 11 min     | 44             | 41                  | 74            | 70         | 2.9G |
| 64       | 17 min     | 48             | 44                  | 79            | 76         | 5.85G |
| 128      | 30 min     | 51             | 46                  | 83            | 77         | 11.0G |

[https://developer.apple.com/documentation/createml/mlobjectdetectormetrics] - Documentation on intersection/union and what Apple means in the context of object detection. If you're new to YOLO, read the paper to get a better understanding.

[https://pjreddie.com/darknet/yolov2/] - YOLOv2 website

[https://pjreddie.com/media/files/papers/YOLOv3.pdf] - YOLOV3 paper

## Observations

During the training, the GPU was above 90% utilization. CPU usage was around 50%. Performance was similar to COCO Dataset.

