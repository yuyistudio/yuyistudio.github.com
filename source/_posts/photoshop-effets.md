---
title: Photoshop梦幻效果
categories: photoshop
tags:
  - photoshop
  - ps
date: 2016-11-12 10:51:06
---

### 梦幻效果

![](/img/ps/radiant_defense_c.jpg)

一个2D游戏常用效果是，在暗色背景中显示外发光的物体，可以制造出华丽的效果。
例如[炫光防御][radiant defense]这款游戏。所有需要发光的物体都需要事先处理好，在PS中可以这么实现：

1. 打开要处理的图片，图层假设命名为base
2. 菜单-图像-画布大小，增大画布以便给炫光部分留出空间
3. 新加图层到最底层，填充黑色，以便作为背景观察效果（称为bk）
3. 复制base图层为blur图层
![](/img/ps/layers_c.jpg)
1. 选中blur图层，菜单-滤镜-模糊-高斯模糊，一边预览一边根据自己的感觉调整模糊的像素数设置
2. blur图层改为“线性叠加（减淡）”的混合模式，或者别的适合的混合模式，适当调整blur图层的alpha
![](/img/ps/blend_mode_c.jpg)
3. 如果感觉发光强度不够，可以将blur图层复制多份，叠加起来的效果会更加强烈。或者用画笔绘制纯色的轮廓，对轮廓进行模糊操作，可以得到单色的外发光效果。
![](/img/ps/cmp_c.jpg)
4. 最终后图片保存起来以便游戏使用。隐藏背景bk图层，菜单-裁剪-基于透明像素，这样就能缩小图片到最小。如果用Unity，直接保存成PSD格式即可。如果需要做texture pack，菜单-文件-存储为，导出为PNG格式即可。

在游戏中可以将Sprite的blend mode设置为additive，颜色会亮很多。
最终在PS里面可以得到如下效果。
![](/img/ps/demo_rd_c.jpg)

[radiant defense]: http://image.baidu.com/search/index?tn=baiduimage&word=radiant%20defense