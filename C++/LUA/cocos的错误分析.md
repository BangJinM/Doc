# cocos的错误分析

### 1.鼠标事件无反应

​	1.上一层挡住

​	2.鼠标监听没有绑定

### 2.ccui.Button:create(v.image, v.image, v.imageU,ccui.TextureResType.plistType)

​	生成一个Button无反应的原因有一下两个，一个是没有找到图片，第二个是图片没有打图集。