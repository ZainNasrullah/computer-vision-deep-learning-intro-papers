# Machine Learning in Computer Vision Paper List

The list of assigned papers and some brief notes can be found below. Each week, two of the assigned papers are also briefly reviewed.

*Notes about the repository:*
1. The number preceding each filename denotes which week it was assigned.
2. All papers are annotated with highlights identifying bits that I found important.

**Update 2018/10/19**: I realized that I never finished uploading things here! All weeks have now been added. See the reading list below. s

## Week 1
**DeepLab Semantic Image Segmentation with CNN Atrous Convolution CRF (May, 2017) (Reviewed)**
- Proposes 'Atrous Convolution' which is basically convolution with upsampled filters. This allows for explicit control of the resolution at which feature maps are computed. As a result, filters can take advantage of enhanced fields of view of filters considering more context without increasing memory or computation.
- Proposes 'Atrous Spatial Pyramid Pooling' (ASPP) which considers multiple effective fields of view (learning the images at multiple scales) to enhance object segmentation.
- Implements a fully connected Conditional Random Field (a probabilistic graphical model) at the end of the network. This is shown to improve localization accuracy of object boundaries.
- Major Result: Achieves 79.7% mean IOU on the PASCAL VOC-2012 test set.
- Code is publicly available (implemented in Caffe).


**Dynamic Routing Between Capsules (November, 2017) (Reviewed)**
- Provides a brief overview of Capsule networks
    - Vectorized alternative to a scalar neuron
    - Describes both activation and parameters of an entity
- Proposes a dynamic routing algorithm to for teaching Capsule
    - Coupling coefficients between capsules describe the agreement between capsule layers. For example, the presence of an eye would suggest that its likely that a face exists at a higher layer.
    - "Routing-by-agreement" between capsules is expected to be more efficient than pooling as it doesn't discard potentially valuable knowledge.
- Shows that the addition of a Decoder network at the end of the Caps Net to visualize results can also act as a form of regularization
- Performs well on the MultiMNIST dataset (segmenting overlapping digits)
- Demonstrated that a Capsule network is more robust to affline transformations than a comparable CNN

**Deformable Convolutional Network (June, 2017)**
- Proposes Deformable Convolution and Deformable RoI Pooling to address CNN limitations with modeling geometric transformations
    - Based on the idea of augmenting spatial sampling location by introducing learned 2D offsets without additional supervision. Offsets are learned from preceding feature maps.
    - Shown to learn transformations affecting scale, aspect ratio and rotation
- New modules are plug and play replacements for existing layers in CNNs
- Experiments show improved performance when implemented in DeepLab, class-aware RPN, Faster R-CNN, and R-FCN

## Week 2
**In-Place Activated BatchNorm for Memory Optimized Training (December, 2017) (Reviewed)**
- Goal is to gain an optimal trade-off between computation and memory during forward and backward passes of a neural network
- Suggests a simple change to checkpointing which improves performance
    - Checkpointing: Store only the input x to a layer and use it to calculate the output z during the backwards pass
    - Suggestion: Store the input after batch normalization to perform less computations during the backwards pass.
- Proposes two variants of In-Place Activated Batch Normalization
    - Variant 1: Store the output z and use it to calculate the input x. This requires an invertible activation function such as leaky RELU but is shown to be more memory efficient than checkpointing as it requires less mathematical paramters.
    - Variant 2: Same as variant 1 but also reparameterize the gradient as a function of intermediate y. This can be more efficient because it isn't necessary to transorm y back into x.
    - Mathematical proofs provided in the paper
- Major Result: Proposed methods can obtain memory savings of up to 50% with only 1-2% additional computation.

**YOLO9000: Better, Faster, Stronger (December, 2016) (Reviewed)**
- Proposes multiple improvements to the original YOLO (You Only Look Once) algorithm yielding YOLOv2
    - Proposed Changes: adding batch normalization on convolutional layers, fine-tuning the initial classification network on higher resolution data before tuning the network for detection (high resolution classifier), adding anchor boxes in place of fully connected layers, using k-means to obtain good training set bounding box priors (tackles anchor box issue #1), predicting coordinates relative to the grid-cell (tackles anchor box issue #2), adding a passthrough layer that brings higher-resolution features from an earlier layer to access fine-grain features, and down sampling training data to predict well across a variety of different resolutions (multi-scale training).
    - Can run at multiple sizes and FPS'; scores 78.6 mAP at 40 FPS on VOC 2007.
    - Proposed the Darknet-19 network architecture upon which YOLOv2 is built
- Proposed a hierarchical classification model WordTree capable of merging image classification and detection datasets and thus closing the gap between available dataset sizes for the tasks
- Proposed a joint training algorithm that can be simultaneously trained for image classification (expanding the number of classes) and detection (bounding box coordinate prediction). This allows detection datasets to take advantage of the information available in classification datasets.


**MultiScale Context Aggregation By Dilated Convolutions (April, 2016)**
- Proposes the use of Dilated Convolutions (using larger filter map with k non-zero values) to aggregate multi-scale information without loss of resolution. Based on the fact that dilated convolutions can exponentially expand the receptive field without loss of resolution or coverage.
    - A 1-dilated convolution is the same as an ordinary convolution. A 2-dilated adds a single zero pixel between all pixels in the filter map thus increasing hte receptive field of a 3x3 filter to 7x7. Similarly, a 4-dilated convolution (three zero pixels between filter map pixels) transforms a 3x3 filter to 15x15. The receptive field grows exponentially while the number of parameters grow linearly.
- Proposes a Context module that takes advantage of different dilation factors.
    - Found that identify initialization (each layer passes the input forward) was more effective than random initialization
- Proposes a Front-End module that removes pooling layers and experimentally obtains better dense prediction accuracy. The rationale behind this is that certain aspects of the classification network aren't applicible to dense prediction.
    - Outperforms prior models (including Deeplab) on VOC-2012.

**(For additional summaries, please see the reviews folder or open up the annotated pdfs)**

## Week 3

**Deep Watershed Transform for Instance Segmentation (May, 2017) (Reviewed)**

**Mask R-CNN (January, 2018) (Reviewed)**

## Week 4

**The Reversible Residual Network: Backpropagation Without Storing Activations (July, 2017) (Reviewed)**

**Cascade Residual Learning: A Two-stage Convolutional Neural Network for Stereo Matching (August, 2017) (Reviewed)**

**Efficient Deep Learning for Stereo Matching (2016)**

**FlowNet: Learning Optical Flow with Convolutional Networks (May, 2015)**

## Week 5

**Detect to Track and Track to Detect (October, 2017) (Reviewed)**

**Global Data Association for Multi-Object Tracking Using Network Flows (June, 2008) (Reviewed)**

**Aligning Plot Synopses to Video (2015)**

**Book2Movie (2015)**

**Semi-supervised Learning with Constraints for Person Identification in Multimedia Data (2013)**

**Automatic Naming of Characters in TV Video (2006)**

## Week 6
**Learning Spatiotemporal Features with 3D Convolutional Networks (October, 2015)**


**Real-Time User-Guided Image Colorization with learned Deep Priors (May 2017) (Reviewed)**


**Temporal Relational Reasoning in Videos (November, 2017) (Reviewed)**


**Two-Stream Convolutional Networks for Action Recognition in Videos (November, 2014)**



## Week 7
**Look, Listen and Learn (August, 2017) (Reviewed)**


**Self-Critical Sequence Training for Image Captioning (November, 2017)**


**Show, Attend and Tell Neural Image Caption Generation with Visual Attention (April, 2016)**


**SoundNet Learning Sound Representations from Unlabeled Video (October, 2016) (Reviewed)**



## Week 8
**Ask Your Neurons A Neural-Based Approach to Answering Questions about Images (October, 2015)**


**Deep Compositional Question Answering with neural Module Networks (July, 2017) (Reviewed)**


**Learning to Reason End-to-End Module Networks for Visual Question Answering (September, 2017) (Reviewed)**


**Visual Question Answering Learnings From the 2017 Challenge (August, 2017) (Reviewed)**



## Week 9
**EXPLAINING_AND_HARNESSING_ADVERSARIAL_EXAMPLES (March, 2018)**

