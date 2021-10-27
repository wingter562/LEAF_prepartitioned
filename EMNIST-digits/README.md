## EMNIST digits

**data source**: NIST (https://www.nist.gov/itl/products-and-services/emnist-dataset)

**file format**: pytorch .pt files. Data and labels are encapsulated in torch tensors and serialized.

**data size**: number of training samples = 341,873; number of test samples = 40,832

**how to load the data**:
```
  # load data
  import torch
  data_train = torch.load("training.pt")  # (torch.Size([341873, 28, 28]), torch.Size([341873]))
  data_test = torch.load("test.pt")  # (torch.Size([40832, 28, 28]), torch.Size([40832]))
```
Alternatively, Pytorch users can directly load the EMNIST data using torchvision's APIs:
```
  import torchvision
  transform = transforms.Compose([transforms.ToTensor(), transforms.Normalize((0.1307,), (0.3081,))])
  data_train = tv_datasets.EMNIST(task_cfg.path, split='digits', train=True, download=True,
                                           transform=transform)
  data_test = tv_datasets.EMNIST(task_cfg.path, split='digits', train=False, download=True,
                                          transform=transform)
```

**FL partitioning**: the EMNIST digits data are not pre-partitioned by users. 

For a by-user partitioned EMNIST, see the [pre-partitioned FEMNIST dataset](https://github.com/wingter562/LEAF_prepartitioned/tree/main/femnist_sf02). 

For a by-label partitioned EMNIST, one can use the same trick as in the [Dirichlet CIFAR dataset](https://github.com/wingter562/LEAF_prepartitioned/tree/main/CIFAR_Dirichlet).
