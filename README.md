这个小功能没什么难的，就是canvas的语法，函数老是记不住，都得现翻MDN。
总结一下知识点：
1.canvas中创建精灵对象，如何做到刷新。我之前想的是每个对象之间完全独立，自己更新自己的动画，发现一个问题就是一个实例如果用clearrect清空画布的时候，是不知道这个区域中是否含有其他实例的。所以我就对外暴露出两个方法，一个update，一个draw。在外层容器中的raf循环中来update&draw。
2.关于设备像素比的问题。功能做完后我在pc上看没看出啥瑕疵，结果到了手机上，图片糊的都哭了。搜索了一番发现是设备像素的问题。dpr越高越模糊，因为canvas的width，heigh和css的还不一样。解决办法就是将画布宽高放大dpr倍，但是css宽高不变，然后里面插入图片也相应放大dpr倍。但是实际展示还是以前的大小。类似于大图缩放，就解决了模糊问题。

效果展示
![show](http://b00.cdn.ipalfish.com/0/img/ab/0c/b46d4d85f792759014db334c571f)