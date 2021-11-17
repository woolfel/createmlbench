# Create ML Benchmark

I created this CreateML project to benchmark Apple's M1 Macbook Air and 2021 M1 Max Macbook Pro. The project uses the object detection model with a simple dataset I created on roboflow. This isn't meant to produce a useful model. The main purpose is to measure the performance of macbooks with different dataset and batch sizes. I have several NVidia video cards for doing ML training, but these days the cards are over priced due to supply shortage.

The cost of a high end RTX 3090 24G is around $3000.00 on newegg (Nov/2021). This makes the M1 Max macbook an interesting alternative for light weight experiments.

## Roboflow Project

The dataset is up on Roboflow.com. You can download the datasets with these links

[https://universe.roboflow.com/peter-lin/face-features-test] - a selection of images from coco dataset with eyes and nose bounding boxes

## Running the benchmark

1. clone the repository "git clone https://github.com/woolfel/createmlbench"
2. download the dataset and extract it to the desired location
3. open the CreateML project ![createml project](./images/createml-open-project.png)
4. The data sources need to be set before you can start training. Click Choose and open the train folder
5. Set validation data to the valid folder
6. Set testing data to the test folder
7. Use 1000 for the iterations
8. Change the batch size
9. Click Train button to start training

CreateML doesn't give you a summary of how long the train+test takes. What I do is create a spreadsheet or text file to record the start time and end time.



## Useful Links about hardware acceleration
[https://timdettmers.com/2020/09/07/which-gpu-for-deep-learning/] - a great write up on NVidia RTX video cards for ML training
