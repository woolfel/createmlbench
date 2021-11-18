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

Batch size | elapsed time | Train Accuracy | Validation Accuracy | Top Train Acc | Tp Val Acc |
-----------------------------------------------------------------------------------------------
| 16       | 124 min      | 22             | 22                  |  64           | 64         |
| 32       | 184 min      | 25             | 24                  |  66           | 65         |
| 64       | 304 min      | 27             | 25                  |  70           | 69         |
| 128      | 570 min      | 28             | 25                  |  72           | 69         |
