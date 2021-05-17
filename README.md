# High-resolution Satellite Video Object Tracking Based on ThickSiam Framework

## Introduction

High-resolution satellite videos are playing an increasingly
important role as a means of monitoring dynamic
ground targets. Currently, satellite video object tracking is
confronted with small size, partial occlusion, residual shadow,
poor target-background discriminability, shape deformation and
poor general field illumination challenges. To solve the above
problems, we design a ThickSiam framework, which consists
of a Thickened Residual Block Siamese Network (TRBS-Net)
and an Improved Kalman Filter (IKF) module. The TRBSNet
is stacked by well-designed thickened residual blocks and
thickened maxpooling residual block, while the IKF module is
designed to simultaneously correct the trajectory and size of the
target. We propose an N-frame-convergence mechanism to deal
with the burn-in period problem existed in IKF module and
weightedly combine the results of TRBS-Net and IKF modules.
We also construct a testing dataset suitable for satellite video
object tracking task. We conducted ablation experiments on
the constructed dataset and compared the proposed ThickSiam
framework with other nineteen state-of-the-art trackers including
different features and backbones. The comparison results show
that our ThickSiam tracker obtained a precision value of 0.991
and a success value of 0.755 with a frames per second (FPS) value
of 56.849 implemented on a single NVIDIA GTX1070Ti GPU.

GIF

## Main Results
Tables


## Dataset
Coming soon

## Installation 
Coming soon

## Quick Start
Coming soon

## License
Licensed under an MIT license.
