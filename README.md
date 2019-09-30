# Approaches for instance segmentation 
In this we will be discussing various approaches in which we can implement instance segmentation using various pretrained models such as mask-RCNN etc trained on coco dataset or Custom dataset.

First lets discuss what is instance segmentation and how it is different from semantic segmentation:
* Instance segmentation refers to method of identifying object outlines at the pixel level. **Instance segmentation** includes identification of boundaries of the objects at the detailed pixel level. For example, in the image below, there are 7 balloons at certain locations, and these are the pixels that belong to each one of the balloons.

![alt text](https://miro.medium.com/max/443/1*I5_PSpXNmPDp5K9zvUZLpg.png " instance segmentation ")

* In contrast to instance segmentation, semantic segmentation makes dense predictions inferring labels for each pixel so that every pixel in the image is labeled with the class of its enclosing object.

![alt text](https://www.jeremyjordan.me/content/images/2018/05/Screen-Shot-2018-05-17-at-7.42.16-PM.png " semantic segmentation ")

Above is an example of semantic segmentation, where the goal is to predict class labels for each pixel in the image.
