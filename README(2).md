# Re-implement the work in paper: Residual Attention Networks for Image Classification
Xin Huang (UNI: xh2510), Qimeng Tao (UNI: qt2139), Kangrui Li (UNI: kl3350)

##  Introduce

##  Dataset
In our project, we used CIFAR-10 and CIFAR-100 to train and test our model. The CIFAR-10 dataset consists of 60000 32x32 color images in 10 classes, with 6000 images per class. There are 50000 training images and 10000 test images. The dataset is divided into five training batches and one test batch, each with 10000 images. The test batch contains exactly 1000 randomly-selected images from each class. 

CIFAR-100 dataset is just like the CIFAR-10, except it has 100 classes containing 600 images each. There are 500 training images and 100 testing images per class. The 100 classes in the CIFAR-100 are grouped into 20 superclasses. Each image comes with a "fine" label (the class to which it belongs) and a "coarse" label (the superclass to which it belongs)

##  Results
Our network structure of Attention 56 and Attention 92
<img width="634" alt="table1" src="https://user-images.githubusercontent.com/90971979/146977436-0e3f3a8e-2d0c-43a0-a813-08e621ee2745.png">

First of all, we use the data set on CIFAR-10, first train the model on the network of Attention 56. The results are shown in the table below.
| Network Structure | Error | Reference Error | Traning Times |
| ----------------- | ----- | --------------- | ------------- |
| With Shortcut     | 6.71% | 5.52% | 107s / epochs(bath size = 64) |
| Without Shortcut  | 6.68% | 5.52% | 98s  / epochs(bath size = 64) |

Then we use the data set on CIFAR-10, train the model on the network of Attention 92. The results are shown in the table below.
| Network Structure | Error | Reference Error | Traning Times |
| ----------------- | ----- | --------------- | ------------- |
| With Shortcut     | 5.91% | 4.99% | 109s / epochs(bath size = 64) |
| Without Shortcut  | 6.12% | 4.99% | 99s  / epochs(bath size = 64) |

We also implemented the training of Attention56 and Attention92 on CIFAR-100. The results are shown in the table below.
Attention 56 on CIFAR-100
| Network Structure | Error | Reference Error | Traning Times |
| ----------------- | ----- | --------------- | ------------- |
| With Shortcut     | 32.24% | Not provided | 172s / epochs(bath size = 64) |
| Without Shortcut  | 37.98% | Not provided | 172s / epochs(bath size = 64) |

Attention 92 on CIFAR-100
| Network Structure | Error | Reference Error | Traning Times |
| ----------------- | ----- | --------------- | ------------- |
| With Shortcut     | 25.8% | 20.71% | 424s / epochs(bath size = 64) |
| Without Shortcut  | 30.3% | 20.71% | 424  / epochs(bath size = 64) |

Finally, we discussed the impact of noise on accuracy, and the results are shown in the following table.
| Noise | ResNet 164 | Attention 56 | Attention 92 |
| ----- | ---------- | ------------ | ------------ |
| 10%   | 5.93% | 9.46%  | 7.35% |
| 30%   | 6.61% | 10.43% | 8.21% |
| 50%   | 8.35% | 13.10% | 10.31%|
| 70%   | 17.21%| 21.3%  | 18.3% |

##  Environment
```
Python 3.8
Tensorflow-gpu 2.5
Google Cloud (NVIDIA Tesla P100)
```

##  Team Member and Contribution
| Name | UNI | Details 1 | Details 2 | Details 3 | Fraction of total contribution |
| ---- | --- | --------- | --------- | --------- | ------------------------------ |
| Xin Huang   | xh2510   | Building Model Structure | Training Model | Writing Paper | 1/3 |
| Qimeng Tao  | qt2139   | Building Model Structure | Training Model | Writing Paper | 1/3 |
| Kangrui Li  | kl3350   | Building Model Structure | Training Model | Writing Paper | 1/3 |

## Saved Models
The (saved) Models can be accessed through Google Drive:

## File Organization
```
├── /utils/
│  ├── modules.py
│  └── noise_level.py
├── /figures/
│  ├── Attention 56 acc.png
│  ├── Attention 56 loss.png
│  ├── Attention Module Architecture.png
│  ├── Example Architecture.png
│  ├── Shortcut Connection.png
│  ├── Structure of two branches.png
│  ├── System Architecture.png
│  └── soft mask.png
├── ECBM_4040_Final_Project.ipynb
├── Project Report.pdf
└── README.md
```