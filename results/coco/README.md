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

|Batch size | elapsed time | Train Accuracy | Validation Accuracy | Top Train Acc | Top Val Acc | Peak Memory |
|-----------|:-------------|:---------------|:--------------------|:--------------|:------------|:------------|
| 16       | 124 min      | 22             | 22                  |  64           | 64         | 2.6G |
| 32       | 184 min      | 25             | 24                  |  66           | 65         | 5.3G |
| 64       | 304 min      | 27             | 25                  |  70           | 69         | 11.1G |
| 128      | 570 min      | 28             | 25                  |  72           | 69         | 22.2G |

## Observations

During the training, the GPU was above 90% utilization. CPU usage was less than 50%, but I didn't keep a close watch. For batch sizes less than 128, memory usage was good and didn't need to use swap. If I ran additional training for a specific batch, it used more memory than the initial run. To fix that memory issue, I closed CreateML and restarted the app. There seems to be a garbage collection issue with running additional training without restarting the app. If I have time, I will investigate this a bit more to get a better understanding of why it happens.

For 32G MBP, the practical limit is 100-150K images and batch 128. If you have a 64G MBP, you should be able to go up to 200K images similar to COCO dataset. If you want the training to finish faster, use 32 or 64 batch size. The accuracy will be less than batch 128, but the difference shouldn't be significant. Training on macbook should be sufficient for small experiments. Once you're ready to validate your model on larger dataset, you'll want to train on the cloud with GPU or TPU and millions of records.
