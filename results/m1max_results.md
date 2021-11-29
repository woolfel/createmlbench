# Hardware
* M1 Max Macbook Pro
* 2/8 CPU
* 24 GPU
* 32G memory
* 2T SSD

# Software
* CreateML version 3.0(78.6)
* XCode version 13.1(13A1030d) 


## Small Dataset
|Train	 | Validation | Test |
|--------|:----------:|:-----|
|144	   |16          |	8    |

## Test process

For each test, I cloned the repository, set the data sources, select the batch and timed the training run. At the end I used preview to test sample photos. Each run was for 1000 iterations. The setting used was "full network".


|batch	 | ET min | Train Acc | Val Acc | Test Acc | Top IU Train | Top IU Valid | Top IU Test | Peak mem G | loss |
|--------|:-------|:----------|:--------|:---------|:-------------|:-------------|:------------|:-----------|:-----|
|16	     | 11     | 52        | 24      | 10       | 60           | 42           | 17          |	1.5       | 1.49 |
|32	     | 17     | 59        | 31      | 18       | 63           | 48           | 32          |	2.8       | 1.32 |
|64	     | 30     | 64        | 30      | 15       | 69           | 45           | 26          |	5.4       | 1.27 |
|128     | 57     | 69        | 26      | 22       | 72           | 39           | 38          |	12        | 1.18 |

* Footnote: memory pressure for 128 batch size was light, but it didn't need swap

## bigger Dataset (larger-dataset-8)
|Train	 | Validation | Test |
|--------|:----------:|:-----|
|301	   |29          |	18   |

I also ran the same tests with a slightly bigger dataset. The purpose was to see at which point CreateML uses disk swap.

|batch	 | ET min | Train Acc | Val Acc | Test Acc | Top IU Train | Top IU Valid | Top IU Test | Peak mem G | loss |
|--------|:-------|:----------|:--------|:---------|:-------------|:-------------|:------------|:-----------|:-----|
|16	     | 10     | 46        | 26      | 22       | 49           | 42           | 29          | 1.5        | 1.64 |
|32	     | 17     | 54        | 28      | 14       | 55           | 46           | 17          | 2.76       | 1.53 |
|64	     | 30     | 57        | 25      | 28       | 58           | 41           | 35          | 5.3        | 1.36 |
|128     | 54     | 66        | 28      | 17       | 68           | 46           | 24          | 11.8       | 1.30 |

* Footnote: the swap for 128 had a max of 2.25G. There was noticeable memory pressure, which increased training time to over 4 hours

# Accuracy differences between datasets

Note the accuracy between the small and larger dataset is quite different. Even though the larger dataset contains the same images as the small dataset, you can't expect the same accuracy. The larger dataset has more variety, which means it will have lower accuracy. You can see the impact on training accuracy with batch size. What you can't do is directly compare the results of different datasets.

# Transfer Learning

The accuracy with transfer learning is better than full network.

|batch	 | ET min | Train Acc | Val Acc | Test Acc | Top IU Train | Top IU Valid | Top IU Test | Peak mem G | loss |
|--------|:-------|:----------|:--------|:---------|:-------------|:-------------|:------------|:-----------|:-----|
|16	     | 4      | 75        | 19      | 12       | 78           | 23           | 13          | 1.5        | 0.41 |
|32	     | 8      | 75        | 21      | 10       | 78           | 26           | 11          | 2.76       | 0.02 |
|64	     | 13     | 75        | 23      | 8        | 78           | 24           | 9           | 5.3        | 0.017 |
|128     | 25     | 75        | 22      | 13       | 78           | 25           | 14          | 8.4        | 0.012 |
