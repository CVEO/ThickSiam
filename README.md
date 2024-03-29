# High-resolution Satellite Video Object Tracking Based on ThickSiam Framework

## Introduction

High-resolution satellite videos are playing an increasingly important role as a means of monitoring dynamic ground targets. Currently, objects in satellite videos are confronted with small size, partial occlusion, residual shadow, poor target-background discriminability, shape deformation, and poor general field illumination challenges. To solve the above problems, we design a ThickSiam framework in this paper, which consists of a Thickened Residual Block Siamese Network (TRBS-Net) and a Remoulded Kalman Filter (RKF) module. The TRBS-Net is stacked by well-designed thickened residual blocks and thickened maxpooling residual block, while the RKF module is designed to simultaneously correct the trajectory and size of the target. In this framework, we propose an N-frame-convergence mechanism to deal with the burn-in period problem existed in RKF module and combine the results of TRBS-Net and RKF modules by frames. We also construct a testing dataset suitable for satellite video single object tracking (SOT) task. We conducted ablation experiments on this dataset and compared the proposed ThickSiam framework with other 19 state-of-the-art trackers. The comparison results show that our ThickSiam tracker obtains a precision value of 0.991 and a success value of 0.755 while running at 56.849 frames per second (FPS) implemented on a single NVIDIA GTX1070Ti GPU.

### Challenges

<div align=center>
<img src = "demo/issue-h.png" />
</div>

&nbsp;

### Tracking results

<div align=center>
<img src = "demo/airplane-1.gif" />
</div>

<div align=center>
The tracking results of airplane-1 target
</div>

&nbsp;

<div align=center>
<img src = "demo/train-1.gif" />
</div>

<div align=center>
The tracking results of train-1 target
</div>

&nbsp;

<div align=center>
<img src = "demo/train-2.gif" />
</div>

<div align=center>
The tracking results of train-2 target
</div>

&nbsp;

<div align=center>
<img src = "demo/legend.png" />
</div>

## Main Results

### Validation of The ThickSiam

We modularly verified the effectiveness of the overall framework based on three training schemes: training with individual COCO dataset, training with individual DIOR dataset, and training with joint COCO and DIOR datasets. We stacked the original residual block and down-sampling residual block to assemble the baseline network and compared it with TRBS-Net. We compared the RKF module with the standard Kalman Filter (KF for short), which only predicts the center point coordinates of the tracked object. The precision plots and success plots about the comparison results of different methods with three training schemes are shown in the figure below.

<img src="demo/plot-E1.png" />

### Comparisons with State-of-the-Art Trackers on Our Constructed Testing Dataset

We compared the ThickSiam Framework with other 19 state-of-the-art trackers including CF-based and DL-based methods with different features and backbones on our constructed testing dataset. They are MOSSE, CSK, KCF, CN, DSST, Staple, SiamFC, DCFNet, ECO, STRCF, ATOM, DiMP, SiamFC+, SiamRPN+, SiamRPN++, SiamFC++ and ID-DSN. The comparison results are shown in the following Table.

|             Trackers           |  Methods |       Features       |            Backbones            | CUDA | Precision | Success |   FPS   |
|:------------------------------:|:--------:|:--------------------:|:-------------------------------:|:----:|:---------:|:-------:|:-------:|
| MOSSE(2010)                    | CF-based |  Grayscale Intensity | -                               | - | 0.745     | 0.48    | 4.964   |
| CSK(2012)                      | CF-based |  Grayscale Intensity | -                               | - | 0.755     | 0.512   | 5.478   |
| KCF(2014)                      | CF-based | HOG                  | -                               | - | 0.851     | 0.634   | 18.21   |
| CN(2014)                       | CF-based | Color Table          | -                               | - | 0.859     | 0.609   | 8.763   |
| DSST(2014)                     | CF-based | HOG                  | -                               | - | 0.782     | 0.596   | 9.72    |
| Staple(2016)                   | CF-based | HOG+Color Histogram  | -                               | - | 0.776     | 0.58    | 10.887  |
| SiamFC                         | DL-based | CNN Features         | AlexNet                         | √ | 0.902     | 0.663   | 127.174 |
| DCFNet(2017)                   | CF-based | CNN Features         | conv1 from VGG                  | √ | 0.833     | 0.644   | 12.4    |
| ECO(2017)                      | CF-based | CNN Features         | ResNet18 with vgg-m conv1 layer | - | 0.856     | 0.645   | 3.998   |
| STRCF(2018)                    | CF-based | HOG+Color Table      | -                               | - | 0.795     | 0.557   | 7.498   |
| ATOM(2019)                     | DL-based | CNN Features         | ResNet18                        | √ | 0.852     | 0.622   | 10.771  |
| DiMP(2019)                     | DL-based | CNN Features         | ResNet18                        | √ | 0.717     | 0.545   | 12.697  |
| DiMP(2019)                     | DL-based | CNN Features         | ResNet50                        | √ | 0.747     | 0.597   | 11.239  |
| SiamFC+(2019)                  | DL-based | CNN Features         | ResNet22                        | √ | 0.839     | 0.652   | 59.333  |
| SIamRPN+(2019)                 | DL-based | CNN Features         | ResNet22                        | √ | 0.878     | 0.618   | 114.867 |
| SiamRPN++(2019)                | DL-based | CNN Features         | AlexNet                         | √ | 0.883     | 0.656   | **144.783** |
| SiamRPN++(2019)                | DL-based | CNN Features         | ResNet50                        | √ | 0.828     | 0.655   | 31.617  |
| SiamFC++(2020)                 | DL-based | CNN Features         | AlexNet                         | √ | 0.925 | 0.699   | 139.828 |
| ID-DSN（2021）                  | DL-based | CNN Features         | ResNet50                        | √ | 0.933 | 0.718   | 31.167  |
| ThickSiam (ours, TRBS-Net)     | DL-based | CNN Features         | TRB+TMRB                        | √ | 0.959 | 0.721   | 57.315  |
| ThickSiam (ours, TRBS-Net+RKF) | DL-based | CNN Features         | TRB+TMRB                        | √ | **0.991**  | **0.755**    | 56.849  |

The precision plots and success plots of the ablation experiments with the state-of-the-art trackers are shown in the figure below.

<img src="demo/plot-E3.png" />

## Download Links

[*Google Drive*](https://drive.google.com/file/d/17s0Pc5jGJfVUd-_sP9xyXm9nIFRpRJdf/view?usp=sharing) | [*BaiduYun 百度云*](https://pan.baidu.com/share/init?surl=7B8QPrtnYUbD-DXcBK8bXQ&pwd=285e)

## Screenshots of the Dataset 
<img src="dataset/dataset.png" />

## Citation
If you like to use our work, please consider citing us:
```
@article{zhang2023high,
  title={High-resolution satellite video single object tracking based on thicksiam framework},
  author={Zhang, Xiaodong and Zhu, Kun and Chen, Guanzhou and Liao, Puyun and Tan, Xiaoliang and Wang, Tong and Li, Xianwei},
  journal={GIScience \& Remote Sensing},
  volume={60},
  number={1},
  pages={2163063},
  year={2023},
  publisher={Taylor \& Francis}
}
```

## License
Licensed under an MIT license.
