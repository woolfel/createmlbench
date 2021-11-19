# Coco Dataset Results for M1 Max MBP

I ran the tests a few times and they are generally consistent. The results in the table aren't averages. Once I run them a few more times, I will update it with averages.

## Hardware Specs
* M1 Max
* 24 GPU
* 10 CPU
* 32G unified memory
* Monterey
* CreateML 3

## Coco Dataset

* training 115,406
* validation 4,952
* classes 80
* zipped file 6.5G

## Table of results

Screen shots of each run is in the folders.

* elapsed time is in minutes from the reported start and finish
* training accuracy is the final average accuracy across all classes
* validation accuracy is the final average accuracy across all classes
* top class Intersetion/Union reported from the training dataset
* top class Intersetion/Union reported from the validation dataset

|Batch size | elapsed time | Train Accuracy | Validation Accuracy | Top Train I/U | Top Val I/U | Peak Memory |
|-----------|:-------------|:---------------|:--------------------|:--------------|:------------|:------------|
| 16       | 124 min      | 22             | 22                  |  64           | 64         | 2.74G |
| 32       | 184 min      | 25             | 24                  |  66           | 65         | 5.3G |
| 64       | 304 min      | 27             | 25                  |  70           | 69         | 11.1G |
| 128      | 570 min      | 28             | 25                  |  72           | 69         | 22.2G |

[https://developer.apple.com/documentation/createml/mlobjectdetectormetrics] - Documentation on intersection/union and what Apple means in the context of object detection. If you're new to YOLO, read the paper to get a better understanding.

[https://pjreddie.com/darknet/yolov2/] - YOLOv2 website

[https://pjreddie.com/media/files/papers/YOLOv3.pdf] - YOLOV3 paper

## Observations

During the training, the GPU was above 90% utilization. CPU usage was around 50%, but I didn't keep a close watch. For batch sizes less than 128, memory usage was good and didn't need swap. If I ran additional training for a specific batch, it used more memory than the initial run. To fix that memory issue, I closed CreateML and restarted the app. There seems to be a garbage collection issue with running additional training without restarting the app. If I have time, I plan to investigate this a bit more to get a better understanding of why it happens.

For 32G MBP, the practical limit is 100-150K images and batch 128. If you have a 64G MBP, you should be able to go up to 200K images similar to COCO dataset. If you want the training to finish faster, use 32 or 64 batch size. The accuracy will be lower than larger batches, but the difference shouldn't be significant. Training on macbook should be sufficient for small experiments. Once you're ready to validate your model on larger dataset, you'll want to train on the cloud with GPU or TPU and millions of records.

The way activity monitor reports CPU usage is a little weird, since the graph shows the true overall system usage. The reported usage can be more than 100% for a given process. I don't know why Apple reports it this way in MacOS, but it's "a feature".
