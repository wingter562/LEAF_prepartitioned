## Pre-partitioned FEMNIST dataset

**Source data:** FEMNIST (which is basically EMNIST with writer tags).

**Task**: Image classification.

**Sampling and partitioning script**: ./preprocess.sh -s niid --sf 0.2 -t sample (see [LEAF's repo](https://github.com/TalwalkarLab/leaf/tree/master/data/femnist) for details).

**Meta data**: 
- Sampling source: 20% data (--sf 0.2)
- User filter: none
- Statistically distribution: non-IID as each writer is a unique domain (-s niid)
- Sampling results: number of users = 737, training data size = 146,870, test data size = 16,686

**Data format**: each .json file contains a hierarchical dictionary
- "users": the list of user ids, e.g., \["f3388_36", "f3285_15", ...\]
- "num_samples": the list of number of samples for each user, e.g., \[155, 162, 164, ...\]
- "user_data": the value is a dictionary with user ids as the keys
	- "user id" (e.g., "f3388_36"): 
		- "x": the users' flattened images as an 2D array, x.shape = (N, 784=28x28)
		- "y": the labels as a list, length = N

**Data loading demo**: see the [FEMNIST_loader_demo notebook](https://github.com/wingter562/LEAF_prepartitioned/blob/main/femnist_sf02/FEMNIST_loader_demo.ipynb) for details.