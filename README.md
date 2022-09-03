# multi-view-3d-reconstruction
《基于多视角图像的三维重建》

## 一、引言

### 1.1 三维重建

三维重建根据所用传感器的不同，可以分为**主动式三维重建**和**被动式三维重建**。主动式三维重建根据传感器去主动探测深度信息，常用的传感器包括激光雷达（LiDAR），结构光（Structured Light）和ToF（Time-of-Fight, 飞行时间）等。主动式三维重建适用的场景受限，而且通常硬件设备价格昂贵。而被动式三维重建通常只需要相机，而且适用场景较为广泛，因此受到研究人员的重视/青睐。被动式三维重建根据算法输入视图数目的不同，可以分为单目深度估计、双目立体匹配和多视图三维重建三种方式。

 <table align="center">
  <tr>
    <td><img src="figures/fig1_3d_recon.png" width="600" ></td>
  </tr>
  <tr>
    <td>三维重建方式分类</td>
  </tr>
</table>

+ 三维重建
  + 激光雷达  【准确/稀疏/场景受限/探测距离受限/贵】 --> 自动驾驶
  + 结构光/ToF 【快速出深度图/场景受限/探测距离受限/较贵】 --> KinectV1/V2、奥比中光
  + 基于图像的三维重建 【成本低/算法性能在不断提升】
    + 单目深度估计
    + 双目立体匹配
    + 多视图三维重建

### 1.2 基于图像的三维重建

基于图像的三维重建根据输入视图数可分为：单目深度估计、双目立体匹配和多视图三维重建。具体到每一种方式，如果三维重建是以恢复场景几何结构为目标，那么单目深度估计的深度图如果没有施加多视图的几何一致性（连续性）约束的话，那么重建三维几何的质量无法保证；而双目立体匹配计算的深度和双目相机的焦距和基线有关，如果需要获得较大的深度感知范围，则需要很大的基线距离，因此限制了双目立体匹配的应用范围。多视图立体匹配的输入图像为多幅单目图像，通过多视图之间的相似性搜索进行深度图的预测。多视图立体匹配的图像无需进行校正， 图像采集成本低，适用范围广， 因此多视图立体匹配广泛应用于各种场景的三维模型重建中。

 <table align="center">
  <tr>
    <td><img src="figures/fig2_mono_depth_est.png" width="500"></td>
    <td><img src="figures/fig3_stereo_disparity.jpg" width="500"></td>    
    <td><img src="figures/fig4_multi-view_stereo.jpg" width="500"></td>
  </tr>
  <tr>
    <td>单目深度估计 (Eigen et al. 2014)</td>
    <td>双目立体匹配 (Middlebury Stereo Benchmark)</td>    
    <td>多视图三维重建 (MVS Tutorial)</td>
  </tr>
</table>


 + 单目深度估计
 + 双目立体匹配： `depth=f·b/disp`, 式中f为focal length(焦距)，b为baseline(基线)，深度探测范围受限于相机之间的基线距离
 + 多视图三维重建

### 1.3 基于多视角图像的三维重建
基于多视角图像进行三维重建的流程为：输入多视角采集的图像，输出对应场景的三维几何模型（点云/表面网格）。通常步骤包括：输入图像采集、运动恢复结构（Structure-from-Motion, SfM）、多视图立体匹配（Multi-view Stereo, MVS）和表面重建等步骤。


 <table align="center">
  <tr>
    <td><img src="figures/fig5_3d_recon.png" width="600" ></td>
  </tr>
  <tr>
    <td>基于多视角图像的三维重建</td>
  </tr>
</table> 

+ 输入图像采集
+ 运动恢复结构
+ 多视图立体匹配
+ 表面重建

## 二、数据集与评测指标
### 2.1 多视图三维重建数据集
多视图三维重建（此处指MVS）常用数据集包括**DTU**、**Tanks and Temples**和**ETH3D**，以及用于深度学习网络模型训练的**BlendedMVS**。具体内容可以参考[multi-view-stereo-benchmark](https://github.com/XYZ-qiyh/Awesome-Learning-MVS#multi-view-stereo-benchmark)
<!--
+ DTU
+ Tanks and Temples
+ ETH3D
+ BlendedMVS
--->

 <table align="center">
  <tr>
    <td><img src="figures/datasets/DTU_scan83.png" width="500"></td>
    <td><img src="figures/datasets/TT_Truck.jpg" width="500"></td>    
    <td><img src="figures/datasets/ETH3D_courtyard.JPG" width="500"></td>
  </tr>
  <tr>
    <td>DTU_scan83</td>
    <td>Tanks and Temples_Truck</td>    
    <td>ETH3D_courtyard</td>
  </tr>
</table>


### 2.2 多视图三维重建评测指标
为了评价三维点云重建的性能，使用F-score或平均绝对误差距离指标来定性评价重建结果的准确性和完整性。
+ F-score的计算可以参考https://tanksandtemples.org/tutorial/
+ 平均绝对误差距离的计算可参考Yao Yao MVSNet paper


## 三、运动恢复结构

### 3.1 对应点搜索

### 3.2 增量式重建

