# 图片转 pos,canny,scribble  


## 介绍


在学习 controlnet 的时候，我们通过输入一个 pos/depth/canny 图片，可以画出一个 pos/depth/canny 相关的图片。 


平常我们也没有这些  pos/depth/canny 图片的，所以需要输入一个图片来生成  pos/depth/canny 图片。  

分四类节点：Pose、canny、Scribble、Depth，下面分类来看。  


## Pose  


Pose 有四个 node。  


| 节点|  示例 |
|:-:|:-:|
|OpenPose Pose|  ![](./OpenPose-Pose.png)|
| DWPose Estimator| ![](./DWPose-Estimator.png) |
|AnimalPose Estimator (AP10K)| ![](./AnimalPose-Estimator.png) |
|DensePose Estimator| ![](./DensePose-Estimator.png) |


## Scribble


| 节点|  示例 |
|:-:|:-:|
|Scribble Lines| ![](./Scribble-Lines.png) |
|Scribble XDoG Lines| ![](./Scribble-XDoG-Lines.png) |
|Scribble PiDiNet Lines| ![](./Scribble-PiDiNet-Lines.png) |
|Fake Scribble Lines (aka scribble_hed)| ![](./Fake-Scribble-Lines.png) |

## Canny



| 节点|  示例 |
|:-:|:-:|
|Canny| ![](./Canny.png)  |
|Canny Edge| ![](./Canny-Edge.png) |
|PyraCanny| ![](./CannyPyra.png) |


## depth

| 节点|  示例 |
|:-:|:-:|
|Depth Anything| ![](./Depth-Anything.png)  |
|Depth Anything V2 | ![](./Depth-Anything-V2.png) |
|MiDaS Depth Map| ![](./MiDaS-Depth-Map.png) |
|LeReS Depth Map | ![](./LeReS-Depth-Map.png) |
|Zoe Depth Anything| ![](./Zoe-Depth-Anything.png) |
