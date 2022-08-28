# multi-view-3d-reconstruction
《基于多视角图像的三维重建》

一、引言

1.1 三维重建

 <table align="center">
  <tr>
    <td><img src="figures/fig1_3d_recon.png" width="600" ></td>
  </tr>
  <tr>
    <td>图1-三维重建方式分类</td>
  </tr>
</table>

+ 三维重建
  + 激光雷达  【准确/稀疏/场景受限/探测距离受限/贵】 --> 自动驾驶
  + 结构光/ToF 【快速出深度图/场景受限/探测距离受限/较贵】 --> KinectV1/V2、奥比中光
  + 基于图像的三维重建 【成本低/算法性能在不断提升】
    + 单目深度估计
    + 双目立体匹配
    + 基于多视角图像的三维重建

1.2 基于图像的三维重建

基于图像的三维重建根据输入视图数可分为：单目深度估计、双目立体匹配和多视图三维重建

 <table align="center">
  <tr>
    <td><img src="figures/fig2_mono_depth_est.png" width="500"></td>
    <td><img src="figures/fig3_stereo_disparity.jpg" width="500"></td>    
    <td><img src="figures/fig4_multi-view_stereo.jpg" width="500"></td>
  </tr>
  <tr>
    <td>单目深度估计</td>
    <td>双目立体匹配</td>    
    <td>多视图三维重建</td>
  </tr>
</table>

1.3 基于多视角图像的三维重建
