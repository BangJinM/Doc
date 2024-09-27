1. Label Char 模式的空间是2048*2048，如果超过这个范围，就会导致文本无法显示
2. 艺术字 的字号和高度不匹配导致 文本不能正常居中
3. 输入框设置数字崩溃
4. 在老图的基础上修改了部分内容，meta中的uuid没有变化，导致发布后没有更新最新资源（直接走缓存资源）
   1. 偏好设置->缓存自动图集资源->false
   2. 删掉meta/修改名字
5. setInterval 调用次数比较多（几百次）的情况下耗时大
6. 引擎版本3.8 native 内存泄露严重
   1. [Memleak fix (#16354)  Hash = 47594d7280584ba527e39badaff6e7e5bcf17d39 ](https://github.com/cocos/cocos-engine/pull/16354)   Memleak fix (#16354)  