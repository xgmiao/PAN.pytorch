# Efficient and Accurate Arbitrary-Shaped Text Detection with Pixel Aggregation Network

![](imgs/paper/PAN.jpg)

## Requirements
* pytorch 1.1+
* torchvision 0.3+
* pyclipper
* opencv3
* gcc 4.9+


## Data Preparation

train: prepare a text in the following format, use '\t' as a separator
```bash
/path/to/img.jpg path/to/label.txt
...
```
val:
use a folder
```bash
img/ store img
gt/ store gt file
```

## Train
1. config the `train_data_path`,`val_data_path`in [config.json](config.json)
2. use following script to run
```sh
python3 train.py
```

## Test

[eval.py](eval.py) is used to test model on test dataset

1. config `model_path`, `img_path`, `gt_path`, `save_path` in [eval.py](eval.py)
2. use following script to test
```sh
python3 eval.py
```

## Predict 
[predict.py](predict.py) is used to inference on single image

1. config `model_path`, `img_path`, in [predict.py](predict.py)
2. use following script to predict
```sh
python3 predict.py
```

The project is still under development.

<h2 id="Performance">Performance</h2>

### [ICDAR 2015](http://rrc.cvc.uab.es/?ch=4)
only train on ICDAR2015 dataset

| Method                   | image size (short size) |learning rate | Precision (%) | Recall (%) | F-measure (%) | FPS |
|--------------------------|-------|--------|--------|------------|---------------|-----|
| paper(resnet18)  | 736 |x | x | x | 80.4 | 26.1 |
| my (resnet18+FPEM_FFM+pse扩张)  |736 |1e-3| 84.24 | 74.14 | 78.87 | 21.31 (P100)|
| my (resnet50+FPEM_FFM+pse扩张)  |736 |1e-3| 69.04 | 66.66 | 67.83 | 14.22 (P100)|
| my (resnet18+FPEM_FFM+pse扩张)  |736 |1e-4| 62.93 | 62.41 | 62.61 | 21.31 (P100)|
| my (resnet50+FPEM_FFM+pse扩张)  |736 |1e-4| 61.19 | 69.18 | 64.94 | 14.22 (P100)|
| my (resnet18+FPN+pse扩张)  | 736 |1e-3|  76.50 | 74.70 | 75.59 | 14.47 (P100)|
| my (resnet50+FPN+pse扩张)  | 736 |1e-3|  71.82 | 75.73 | 73.72 | 10.67 (P100)|
| my (resnet18+FPN+pse扩张)  | 736 |1e-4|  74.19 | 72.34 | 73.25 | 14.47 (P100)|
| my (resnet50+FPN+pse扩张)  | 736 |1e-4|  78.96 | 76.27 | 77.59 | 10.67 (P100)|

### examples
TBD

### reference
1. https://arxiv.org/pdf/1908.05900.pdf
2. https://github.com/WenmuZhou/PSENet.pytorch

**If this repository helps you，please star it. Thanks.**