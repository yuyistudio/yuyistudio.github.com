---
title: Unity:实现碰撞破碎效果
date: 2016/11/12 07:37
categories: unity
tags:
- unity
- 破碎
- 效果
---

## 基本思路
在碰撞发生时让主角隐藏，然后生成预先准备好的碎片prefab

## 实现
```cs
// 销毁或者隐藏原来的物体
Destroy(gameObject);
// 创建“碎片”物体
GameObject pieces = Instantiate(pieces_prefab);
pieces.transform.position = gameObject.transform.position;
```

1. `碎片物体`应当由多个小物体组成，小物体添加`RigidBody`和`Collider`组件
2. `Collider`之间可以稍微重合一小部分，以便达到爆炸的效果


---

Best Reards   
2016/11/12