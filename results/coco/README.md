# Coco Dataset Results for M1 Max MBP

I ran the tests a few times and they are generally consistent. The results in the table aren't averages. Once I run them a few more times, I will update it with averages.

## Hardware Specs
* M1 Max
* 24 GPU
* 10 CPU
* 32G unified memory
* Monterey
* CreateML 3

## Table of results

Screen shots of each run is in the folders.

* elapsed time is in minutes from the reported start and finish
* training accuracy is the final average accuracy across all classes
* validation accuracy is the final average accuracy across all classes
* top train accuracy is the class I/U reported from the training dataset
* top validation accuracy is the class I/U reported from the validation dataset

|Batch size | elapsed time | Train Accuracy | Validation Accuracy | Top Train Acc | Top Val Acc |
|-----------|:-------------|:---------------|:--------------------|:--------------|:-----------|
| 16       | 124 min      | 22             | 22                  |  64           | 64         |
| 32       | 184 min      | 25             | 24                  |  66           | 65         |
| 64       | 304 min      | 27             | 25                  |  70           | 69         |
| 128      | 570 min      | 28             | 25                  |  72           | 69         |
