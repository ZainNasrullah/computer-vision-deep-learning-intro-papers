# Machine Learning in Computer Vision Paper List

The list of assigned papers and a short description can be found below. Each week, two of the assigned papers are also briefly reviewed.

*Notes About the Repository:*
1. The number preceding each filename denotes which week it was assigned.
2. All papers are annotated with highlights.

## Week 1
**DeepLab Semantic Image Segmentation with CNN Atrous Convolution CRF (May, 2017) (Reviewed)**
- Proposes 'Atrous Convolution' which is basically convolution with upsampled filters. This allows for explicit control of the resolution at which feature maps are computed. As a result, filters can take advantage of enhanced fields of view of filters considering more context without increasing memory or computation.
- Proposes 'Atrous Spatial Pyramid Pooling' (ASPP) which considers multiple effective fields of view (learning the images at multiple scales) to enhance object segmentation.
- Implements a fully connected Conditional Random Field (a probabilistic graphical model) at the end of the network. This is shown to improve localization accuracy of object boundaries.
- Major Result: Achieves 79.7% mean IOU on the PASCAL VOC-2012 test set.
- Code is publicly available (implemented in Caffe).


**Dynamic Routing Between Capsules (November, 2017) (Reviewed)**

**Deformable Convolutional Network (June, 2017)**

## Week 2
**In-Place Activated BatchNorm for Memory Optimized Training (December, 2017) (Reviewed)**

**YOLO9000: Better, Faster, Stronger (December, 2016) (Reviewed)**

**MultiScale Context Aggregation By Dilated Convolutions (April, 2016)**

## Week 3

**Deep Watershed Transform for Instance Segmentation (May, 2017) (Reviewed)**

**Mask R-CNN (January, 2018) (Reviewed)**


