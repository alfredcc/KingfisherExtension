# KingfisherExtension


##介绍


文章：[Producter Tips](http://tips.producter.io/kingfisherextension-jie-shao/)


对[Kingfisher](https://github.com/onevcat/Kingfisher)进行了简单的封装，

好处：
	
	1. 在用`pod`管理依赖的情况下，不需要到处`import Kingfisher`。
	2. 代码较为集中，方便管理。若以后需要替换`Kingfisher`也很方便。


还可以很集中地添加默认值，在我自己的项目中，全部图片都是默认


```swift

let defaultOptions: KingfisherOptionsInfo = [
    .Options([.BackgroundDecode, .LowPriority]),
    .Transition(ImageTransition.Fade(0.55))
]

```

如果需要对`Kingfisher`下载下来的图片需要作特殊处理，例如作圆角处理，但又不想保存两份，怎么办？
在这个`Extension`中，我简单写了个圆角处理的方法，如果有兴趣，可以看看源码。

原理：直接调用`KingfisherManager`中的`downloadImageWithURL`，得到图片，对图片进行处理后再调用`KingfisherManager`中的`storeImage`来保存图片。


```swift

cell.imageView.kfe_setRoundImageWithURLString(avatarURLStrings[indexPath.row], cornerRadiusRatio: 0.25)

```






