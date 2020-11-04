**赛事介绍**
为了规范城镇户外广告设施和店招标牌设施的设置行为，确保广告设施的安全可靠，创造健康、有序的城市视觉环境，城市管理部门需对违法广告设施做定期肃清。但目前执法依赖执法人员在街道拍照取证，由于涉及街道范围较广，需要耗费大量人力，而且效率也较低。

本赛场聚焦违法广告的智能检测，要求选手研究开发高效可靠的计算机视觉算法，提升违法广告检验的准确度，降低对大量人工的依赖，提升违法广告检测的效果和效率。要求算法既要检测场景中是否包含违法广告，又要给出违法广告具体的位置和类别，既考察违法广告检出能力、也考察违法广告定位和分类能力。

下面对赛题中判别的三种违法广告类型做出详细描述：

1、遮窗广告、招牌：原建筑立面规划建设为通风窗户，商户在经营中设置门头店招或宣传广告时直接将其封堵或覆盖。

2、非交通性指示牌：除《道交法》规定的警告标志版（警告车辆，行人注意道路前方危险地点的标志）、禁令标志（禁止或限制车辆、行人某种交通行为的标志）、指示标志（指示车辆、行人行进的标志）、指路标志（传递道路方向、地点、距离信息的标志）、旅游区标志（提供旅游景点方向、距离的标志）、道路施工安全标志。（通告道路施工区通行的标志）、限速标志（警告车辆减速行驶的标志）以外，企业单位擅自模仿样式设置的指引标识标牌。

3、一店多招：同一店铺在同一立面设置了2处以上的店招标牌。

**时间**
2020.8-2020.10

**初赛**
比赛数据：2000张非法图片/2000张合法图片/2000张测试集
框架：mmdetection 
模型：dh_faster_rcnn 24epochs thresh_hold=0.2 初赛线上0.20359
      backone:resnet101
      多尺度训练/多尺度测试
      数据增强：ShiftScaleRotate/RandomRotate90/RandomBrightnessContrast/及常规 ....
      训练策略：单卡/lr=0.00125/epoch=24/step=[12,18]
初赛成绩：12/373


**复赛**
比赛数据：1600张增量数据（800张非法有标注图片/800张合法无标注图片）/1000张测试
框架：mmdetection/PaddlePaddle
模型：cascade_rcnn 24epochs thresh_hold=0 复赛线上 0.314
      backone:resneXt101(感觉这是个可提分点，奈何mmd暂不支持resnXt152）
      多尺度训练/多尺度测试
      数据增强：ShiftScaleRotate/RandomRotate90/RandomBrightnessContrast/及常规 ....
      训练策略：单卡/lr=0.00125/epoch=24/step=[8,15]
      

      cascade_rcnn_dcnv2_se154_vd_fpn_gn_cas（基于 PaddlePadddle,object365冠军方案）
      效果不好，但是肉眼觉的效果可以，其他检测可以尝试
      链接地址：https://github.com/PaddlePaddle/PaddleDetection/blob/release/0.4/docs/featured_model/champion_model/CACascadeRCNN.md
      特点：针对大规模物体检测算法的特点，我们提出了一种基于图片包含物体类别的数量的采样方式（Class Aware Sampling）。基于这种方式进行训练模型可以在更短的时间使模型收敛到更好的效果

复赛成绩 ：19/373
