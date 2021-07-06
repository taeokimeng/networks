# ResNeXt

Paper: [Aggregated Residual Transformations for Deep Neural Networks](https://arxiv.org/pdf/1611.05431.pdf)

## Introduction

Inception models has been accompanied with a series of complicating factors. It is in general unclear how to adapt the Inception architectures to new datasets/tasks, especially when there are many factors and hyper-parameters to be designed.

A 101-layer ResNeXt is able to achieve better accuracy than ResNet-200 but has only 50% complexity. ResNeXt exhibits considerably simpler designs than all Inception models.

## Method

### Template

![Template](./images/resnext/Table1_template.PNG)

Equivalent building blocks of ResNeXt

![ResNext Blocks](./images/resnext/Fig3_equivalent_building_blocks_of_resnext.PNG)

## Implementation details
* ImageNet dataset
* 224x224 input image size
* Identity shortcuts, projections for increasing dimensions
* Downsampling of conv3, 4, and 5 is done by stride-2 convolutions in the 3x3 layer of the first block in each stage.
* SGD with a mini-batch size of 256 on 8 GPUs (32 per GPU)
* Weight decay is 0.0001
* Momentum is 0.9
* Start learning rate from 0.1 and divide it by 10 for three times using the schedule.
* Batch normalization (BN) right after the convolutions
* ReLU is performed right after each BN, after the adding to the shortcut
* Implemented by Fig.3(c) because it is more succinct and faster than the other two forms

## Experiments

### Experiments on ImageNet-1K

All blocks in ResNet-50/101 are replaced with ResNeXt blocks.

![Training curves on ImageNet-1K](./images/resnext/Fig5_training_curves_on_imagenet1k.PNG)

![Ablation Experiments on ImageNet-1K](./images/resnext/Table3_ablation_experiments_on_imagenet-1k.PNG)

![Comparisons on ImageNet-1K](./images/resnext/Table4_comparisons_on_imagenet-1k.PNG)

The comparisons show that increasing cardinality has better results than going deeper or wider.

![State-of-the-art models](./images/resnext/Table5_state_of_the_art_models.PNG)

### Experiments on CIFAR
* Dataset: CIFAR-10 and 100
* Bottleneck template: <a href="https://www.codecogs.com/eqnedit.php?latex=\begin{bmatrix}&space;1\times1,&space;64\\&space;3\times3,&space;64\\&space;1\times1,&space;256&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;1\times1,&space;64\\&space;3\times3,&space;64\\&space;1\times1,&space;256&space;\end{bmatrix}" title="\begin{bmatrix} 1\times1, 64\\ 3\times3, 64\\ 1\times1, 256 \end{bmatrix}" /></a>
* Networks start with a single 3x3 conv layer, followed by 3 stages each having 3 residual blocks, and end with average pooling and a fully-connected classifier (total 29-layer deep)

![Test error and model size on CIFAR](./images/resnext/Table7_test_error_and_model_size_on_cifar.PNG)

![Test error vs. model size on CIFAR-10](./images/resnext/Fig7_test_error_model_size_on_cifar10.PNG)

Increasing cardinality is more effective than increasing width.