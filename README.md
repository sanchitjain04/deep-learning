# Approaches for instance segmentation 
In this we will be discussing various approaches in which we can implement instance segmentation using various pretrained models such as mask-RCNN etc trained on coco dataset or Custom dataset.

First lets discuss what is instance segmentation and how it is different from semantic segmentation:
* Instance segmentation refers to method of identifying object outlines at the pixel level. **Instance segmentation** includes identification of boundaries of the objects at the detailed pixel level. For example, in the image below, there are 7 balloons at certain locations, and these are the pixels that belong to each one of the balloons.

![alt text](https://miro.medium.com/max/443/1*I5_PSpXNmPDp5K9zvUZLpg.png " instance segmentation ")

* In contrast to instance segmentation, semantic segmentation makes dense predictions inferring labels for each pixel so that every pixel in the image is labeled with the class of its enclosing object.

![alt text](https://www.jeremyjordan.me/content/images/2018/05/Screen-Shot-2018-05-17-at-7.42.16-PM.png " semantic segmentation ")

Above is an example of semantic segmentation, where the goal is to predict class labels for each pixel in the image.

## Various ways to implement instance segmenentation:

1. ### Mask R-CNN for Surgery Robot:

The codes are based on implementation of Mask R-CNN by [Mask R-CNN](https://github.com/matterport/Mask_RCNN) on Python 3, Keras, and TensorFlow. The model generates bounding boxes and segmentation masks for each instance of an object in the image. It's based on **Feature Pyramid Network (FPN)** and a **ResNet101** backbone. We can Use this on our own requirements by adjusting certain parameters.

* ### Training on our own dataset

  To train the model you need to modify two classes in surgery.py:
    * SurgeryConfig This class contains the default configurations. Modify the attributes for your training, most importantly the             NUM_CLASSES.
    * **SurgeryDataset** This class inherits from utils.Dataset which provides capability to train on new dataset without modifying the model.
    
    Now start training on your own dataset Training parapeters are mainly included in function train in **surgery.py**.
    
    For furthur details follow this [link](https://github.com/SUYEgit/Surgery-Robot-Detection-Segmentation)
 2. ### MaterPort Mask R-CNN   
   This implementation is  Mask R-CNN for object detection and instance segmentation on Keras and TensorFlow.
   Basically the first case is one of the use cases of this Mask R-CNN implementation.
  * Basically Mask R-CNN is an instance segmentation technique which locates each pixel of every object in the image instead of the bounding boxes. It has two stages: region proposals and then classifying the proposals and generating bounding boxes and masks. It does so by using an additional fully convolutional network on top of a CNN based feature map with input as feature map and gives matrix with 1 on all locations where the pixel belongs to the object and 0 elsewhere as the output. 
    
    
    ![alt text](https://miro.medium.com/proxy/1*IWWOPIYLqqF9i_gXPmBk3g.png " instance segmentation ")
    
    
    
    It consists of a backbone network which is a standard CNN such as ResNet50 or ResNet101. The early layer of network detect low-level features, and later layers detect higher-level features. The image is converted from 1024x1024px x 3 (RGB) to a feature map of shape 32x32x2048. The Feature Pyramid Network (FPN) was an extension of the backbone network which can better represent objects at multiple scales.
    
     As per our requrirement we can modify certain parameters and transform it as per our usage.
     
     The Link to its Github repository is [Mask](https://github.com/matterport/Mask_RCNN) 
     
3. ### Training DeepLab on Custom Dataset:
   Although DeepLab is an ideal solution for Semantic Segmentation, But it is useful to know its importance and how we can do custom training on it. Lets know what is this DeepLab:
   
   * DeepLab is one of the most promising techniques for semantic image segmentation with Deep Learning. Semantic segmentation is understanding an image at the pixel level, then assigning a label to every pixel in an image such that pixels with the same label share certain characteristics.
   * #### Preparing Dataset:
     Before you create your own dataset and train DeepLab, you should be very clear about what you want to want to do with it.   Here are the two scenarios:
       * Training the model from scratch: you are free to have any number of classes of objects (number of labels) for segmentation. This needs a very long time for training.
       * Use the pre-trained model: you are free to have any number of classes of objects for segmentation. Use the pre-trained model and only update your classifier weights with transfer learning. This will take far less time for training compared to the prior scenario.
       
       For Detailed info : please follow this links :[1](http://hellodfan.com/2018/07/06/DeepLabv3-with-own-dataset)
                                                     [2](https://www.freecodecamp.org/news/how-to-use-deeplab-in-tensorflow-for-object-segmentation-using-deep-learning-a5777290ab6b)
     
     
    
    
    
    
    
    
    
    
    
    
