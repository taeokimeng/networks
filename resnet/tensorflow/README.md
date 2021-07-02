# ResNet, ResNetV2, ResNext

## Train ResNet with TensorFlow

Dataset: CIFAR-10

Batch size: 128

Shortcut: Projection shortcut (Option B, 1x1 convolution)

### [ResNet](https://arxiv.org/pdf/1512.03385.pdf)

Epochs: 200

#### Classification Error on the CIFAR-10 Test Set

|model|# params|error|
|-----|--------|-----|
|ResNet20|274,442|9.25|
|ResNet110|1,742,762|7.49|

#### ResNet20

![ResNet20](./images/ResNet20v1e200.png)

#### ResNet20 vs. ResNet110

![CIFAR10_ResNet20_ResNet110_Epoch200](./images/cifar10_resnet20_110_train_test_epoch200.png)

#### ResNet20 with Horizontal Flip vs. ResNet20 with Horizontal Flip and Vertical Flip

![CIFAR10_ResNet20_HF_HFVF_Epoch200](./images/cifar10_resnet20_hf_hfvf_train_test_epoch200.png)

### [ResNetV2](https://arxiv.org/pdf/1603.05027.pdf)

#### ResNet20V2
![ResNet20v2](./images/cifar10_resnet20v1_resnet20v2_train_test_epoch200.png)

### [ResNext](https://arxiv.org/pdf/1611.05431.pdf)

#### ResNext29

Experiments on CIFAR followed the paper.

Epochs: 300

