# Pytorch Faster-RCNN

This project is aimed to reproduce the faster rcnn object detection model. It is developed based on the following projects:

1. [py-faster-rcnn](https://github.com/rbgirshick/py-faster-rcnn)

2. [faster_rcnn_pytorch](https://github.com/longcw/faster_rcnn_pytorch)

3. [tf-faster-rcnn](https://github.com/endernewton/tf-faster-rcnn)

4. [pytorch-faster-rcnn](https://github.com/ruotianluo/pytorch-faster-rcnn)

However, there are several unique features compared with the above implementations:

1) It is pure Pytorch code. We converted all the numpy code used in previous implementations to pytorch code.

2) It supports trainig batchsize > 1. We revise all the layers, including dataloader, rpn, roi-pooling, etc., so that the training can digest multiple images at each iteration.

3) It supports multiple GPUs. Since the model can take multiple images at once, we use a multiple GPU wrapper (nn.DataParallel here) to make it flexible to use one or more GPUs.

### Modules

#### Prepare Data

put VOCdevkit2007 under data folder. 

To train a resnet101, run:
```
 CUDA_VISIBLE_DEVICES=0 python trainval_net.py --dataset pascal_voc --net resnet101
 ```
Alternatively, to train a vgg16, run:
```
CUDA_VISIBLE_DEVICES=0 python trainval_net.py --dataset pascal_voc --net vgg16
```

