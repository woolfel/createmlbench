# Create ML Benchmark

I wanted to benchmark Apple's M1 Macbook Air to the new 2021 M1 Max Macbook Pro. This Create ML benchmark uses a simple project to measure the training time with different dataset and batch size settings.

## Roboflow Project

The dataset is up on Roboflow.com. You can download the datasets with these links

[https://app.roboflow.com/peter-lin/face-features-test/overview] - a selection of images from coco dataset with eyes and nose bounding boxes

## Running the benchmark

1. clone the repository
2. download the dataset and extract it to the desired location
3. open the CreateML project
4. Click Train button to start training

CreateML doesn't give you a summary of how long the train+test takes. What I do is create a spreadsheet or text file to record the start time and end time.

## Useful Links about hardware acceleration
[https://timdettmers.com/2020/09/07/which-gpu-for-deep-learning/] - a great write up on NVidia RTX video cards for ML training
