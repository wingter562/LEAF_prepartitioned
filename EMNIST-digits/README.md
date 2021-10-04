## EMNIST digits

**data source**: NIST (https://www.nist.gov/itl/products-and-services/emnist-dataset)

**file format**: pytorch .pt files. Data and labels are encapsulated in torch tensors and serialized.

**data size**: number of training samples = 341873; number of test samples = 40832

**how to load the data**:
```
  # load data
  import torch
  import torchvision as tv
  data_train = torch.load("training.pt")  # (torch.Size([341873, 28, 28]), torch.Size([341873]))
  data_test = torch.load("test.pt")  # (torch.Size([40832, 28, 28]), torch.Size([40832]))
```

**FL partitioning**: the EMNIST digits data are not pre-partitioned by users. See the code (.ipynb) in this repo for a class-imbalanced partitioning example.
