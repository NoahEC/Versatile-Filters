## Versatile Filters

Code for paper: [Learning Versatile Filters for Efficient Convolutional Neural Networks (NeurIPS 2018)](https://papers.nips.cc/paper/7433-learning-versatile-filters-for-efficient-convolutional-neural-networks)

We introduce versatile filters to construct efficient convolutional neural network. Considering the demands of efficient deep learning techniques running on cost-effective hardware, a number of methods have been developed to learn
compact neural networks. Most of these works aim to slim down filters in different ways, e.g. investigating small, sparse or binarized filters. In contrast, we treat filters from an additive perspective. A series of secondary filters can be derived from a primary filter. These secondary filters all inherit in the primary filter without occupying more storage, but once been unfolded in computation they could significantly enhance the capability of the filter by integrating information extracted from different receptive fields. Besides spatial versatile filters, we additionally
investigate versatile filters from the channel perspective. The new techniques are general to upgrade filters in existing CNNs. Experimental results on benchmark datasets and neural networks demonstrate that CNNs constructed with our versatile filters are able to achieve comparable accuracy as that of original filters, but require less memory and FLOPs.

![](http://code-sh.rnd.huawei.com/noah-research-edge-computing/Versatile-filters/uploads/e175ce43629b0100c43e3ca7153bc770/image.png)

Fig. An illustration of the proposed versatile convolution filter. The input data is first divided into several areas according to the size and parameters of the a 5 x 5 convolution filter, the proposed versatile convolution filter is then applied three times according to its secondary filters (i.e., 5 x 5 blue, 3 x 3 green, and 1 x 1 red) to generate multiple features.

Experimental results on ImageNet dataset. Details in our paper [Learning Versatile Filters for Efficient Convolutional Neural Networks (NeurIPS 2018)](https://papers.nips.cc/paper/7433-learning-versatile-filters-for-efficient-convolutional-neural-networks)
![](http://code-sh.rnd.huawei.com/noah-research-edge-computing/Versatile-filters/uploads/8647a4108e5d287a6dbdb12b961e09a0/image.png)


### Files description
Platform: Pytorch 0.4

`vcnn.py` is the implementation of Versatile Convolution (an example of VGG-16). The `VConv2d` class can be used to replace the `nn.Conv2d` in any CNN.

`imagenet-vcnn.py` is the script for training ImageNet on Cloud DLS.

`config.png` is a config example on Cloud DLS.

### Hyper-paprameters
In `VConv2d`:
- `delta`: (c-\hat{c}) in Eq.(6)
- `g`: g in Eq.(6)

## Performance
| backbone | method                    | top1 acc | top5 acc |
|--------|---------------------------|----------|----------|
| VGG-16 | baseline                  | 71.5     | 90.1     |
|        | spatial versatile         | 72.2     | 91.1     |
|        | spatial+channel versatile | 70.4     | 89.6     |
