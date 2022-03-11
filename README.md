# Image Classification SOTA  

`Image Classification SOTA` is an image classification toolbox based on PyTorch.

## Updates  


## Requirements
```
torch>=1.0.1
torchvision
```

## Getting Started  
### Prepare datasets  
It is recommended to symlink the dataset root to `image_classification_sota/data`. Then the file structure should be like  
```
image_classification_sota
├── lib
├── tools
├── configs
├── data
│   ├── imagenet
│   │   ├── meta
│   │   ├── train
│   │   ├── val
│   ├── cifar
│   │   ├── cifar-10-batches-py
│   │   ├── cifar-100-python
```

### Training configurations  
* `Strategies`: The training strategies are configured using yaml file or arguments. Examples are in `configs/strategies` directory.

### Train a model  

* Training with a single GPU  
    ```shell
    python tools/train.py -c ${CONFIG} --model ${MODEL} [optional arguments]
    ```

* Training with multiple GPUs
    ```shell
    sh tools/dist_train.sh ${GPU_NUM} ${CONFIG} ${MODEL} [optional arguments]
    ```

* For slurm users
    ```shell
    sh tools/slurm_train.sh ${PARTITION} ${GPU_NUM} ${CONFIG} ${MODEL} [optional arguments]
    ```

**Examples**  
* Train ResNet-50 on ImageNet
    ```shell
    sh tools/dist_train.sh 8 configs/strategies/resnet/resnet.yaml resnet50 --experiment imagenet_res50
    ```

* Train MobileNetV2 on ImageNet
    ```shell
    sh tools/dist_train.sh 8 configs/strategies/MBV2/mbv2.yaml nas_model --model-config configs/models/MobileNetV2/MobileNetV2.yaml --experiment imagenet_mbv2
    ```

* Train VGG-16 on CIFAR-10
    ```shell
    sh tools/dist_train.sh 8 configs/strategies/CIFAR/cifar.yaml nas_model --model-config configs/models/VGG/vgg16_cifar10.yaml --experiment cifar10_vgg16
    ```

## Projects based on Image Classification SOTA  
* [DyRep](https://github.com/hunto/DyRep): Bootstrapping Training with Dynamic Re-parameterization