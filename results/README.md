# Hardware
* M1 Macbook Air
* 16G memory
* 512G SSD
* 13" screen

# Software
* CreateML version 3.0(78.6)
* XCode version 13.1(13A1030d) 

# Test process

For each test, I cloned the repository, set the data sources, select the batch and timed the training run. At the end I used preview to test sample photos. Each run was for 1000 iterations.

|batch	 | elapsed time min | peak memory G | loss |
|--------|:----------------:|:-------------:|------|
|16	     |16                |	1.5           |1.493 |
|32      |29                | 2.8           |1.326 |
|64      |56                |5.4            |1.272 |
|128     |170               |12             |1.186 |

* Footnote: memory pressure for 128 batch size was light, but it didn't need swap
