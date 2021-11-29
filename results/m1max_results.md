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
|16	     | 11     |         |       |        |            |            |           | 1.5       |  |
|32	     |      |         |       |        |            |            |           |        | 1.32 |
|64	     |      |         |       |        |            |            |           |        | 1.27 |
|128     |      |         |       |        |            |            |           |         | 1.18 |

* Footnote: the swap for 128 had a max of 2.25G. There was noticeable memory pressure, which increased training time to over 4 hours

# Observations

During training I had activity monitor open. The GPU usage was oddly low 4-8%. This happens if you choose full network training. For some reason, full network training doesn't use GPU correctly. If you choose transfer learning, it uses GPU like I expect. As of 11/16/21, I don't know the reason for this behavior. I would expect full network to use GPU during training.
