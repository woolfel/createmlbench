# Hardware

## M1 Macbook Air
* 16G memory
* 512G SSD
* 4/4 CPU
* 8 GPU

## M1 Max Macbook Pro
* 32G memory
* 2T SSD
* 2/8 CPU
* 24 GPU

# Software
* CreateML version 3.0(78.6)
* XCode version 13.1(13A1030d) 


## Small Dataset
|Train	 | Validation | Test |
|--------|:----------:|:-----|
|144	   |16          |	8    |

## Test process

For each test, I cloned the repository, set the data sources, select the batch and timed the training run. At the end I used preview to test sample photos. Each run was for 1000 iterations. The setting used was "full network". Elapsed time is in minutes.


|batch	 | M1 ET | M1Max ET | peak mem G |
|--------|:------|:---------|:-----------|
|16	     | 16    | 11       |	1.5        |
|32      | 29    | 17       | 2.8        |
|64      | 56    | 30       | 5.4        |
|128     | 170   | 57       | 12         |

* Footnote: memory pressure for 128 batch size was light, but it didn't need swap

## bigger Dataset (larger-dataset-8)
|Train	 | Validation | Test |
|--------|:----------:|:-----|
|301	   |29          |	18   |

I also ran the same tests with a slightly bigger dataset. The purpose was to see at which point CreateML uses disk swap.

|batch	 | M1 ET | M1Max ET | peak mem G |
|--------|:------|:---------|:-----------|
|16	     | 21    | 10       |	1.5        |
|32      | 42    | 17       | 3.5        |
|64      | 85    | 30       | 8.4        |
|128     | 281   | 54       | 16.5       |

* Footnote: the swap for 128 had a max of 2.25G. There was noticeable memory pressure, which increased training time to over 4 hours

# Observations

During training I had activity monitor open. The GPU usage was oddly low 4-8%. This happens if you choose full network training. For some reason, full network training doesn't use GPU correctly. If you choose transfer learning, it uses GPU like I expect. As of 11/16/21, I don't know the reason for this behavior. I would expect full network to use GPU during training.
