## 你见过火系的暴鲤龙吗？这个项目利用CycleGAN生成不同属性的神奇宝贝

[机器之心](javascript:void(0);) *昨天*

选自Riley Wong博客

**作者：Riley Wong**

**机器之心编译**

**参与：路**

> 水系暴鲤龙还可以变成火系、草系、电系？最近研究者 Riley Wong 做了一个项目，他训练了一个可以改变神奇宝贝属性的 CycleGAN。

了解属性相克，可以帮助训练师们更好地战斗。可是如果神奇宝贝的属性变了呢？有 reddit 评论表示：很想在游戏里见到不同属性的神奇宝贝～以及很好奇改变属性后的皮卡丘会是什么样。

![img](https://mmbiz.qpic.cn/mmbiz_gif/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibc7jrVHyILR6MFSbrLNtffsPDpicxf0f0lvSD6GBrnuo4NSBzKvgvDmQ/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

先看一下水系暴鲤龙和火系凤王「变身」后的结果：

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibxxFk0dibSuRMXFs5xKuZWyh0CTRvXlpjm2IIU9xp2ZObWZaGqAGfv4Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)*水系暴鲤龙、火系暴鲤龙、草系暴鲤龙、电系暴鲤龙齐聚一堂……*

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibazfRic1V0g8Xa10SV3tNQqdVQsYoJtZsiadFszAxe4ic9fm66eDD73RpQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)*火系凤王（Ho-oh）vs 恶系凤王*

**模型**

[CycleGAN](http://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650725257&idx=4&sn=bf367ff90e03f8189f7c67ae0e5ab76f&chksm=871b1ff7b06c96e1e355d8b360abd0c256af04e2ba72a8d2a3364bfea8ff80b347a734d17e9d&scene=21#wechat_redirect)（ICCV 2017）变革了基于图像的计算机图形学，可作为一种通用框架将一组图像中的视觉风格迁移到其它图像。例如，将夏天转化为冬天、将马转换为斑马及利用计算机图形渲染生成真实图像等。

Riley Wong 利用 [CycleGAN](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650763312&idx=4&sn=f888d8546ef1d6d7d3ff619057147391&chksm=871ab44eb06d3d58dd80ca618bd2a35fe9bce94989757cf5c6b0bcf358e21afab9fc545aa31f&mpshare=1&scene=1&srcid=&key=90581f21d61583cc1344f955467dc5d6f599d8c196438e734a4933d547ca3a9a518c9593f383c103d2c018e0f39e94d0f62733af51bc0b1990c2011143b8d62689257bd12432e240404e8cfb79c0af6c&ascene=1&uin=MjMzNDA2ODYyNQ%3D%3D&devicetype=Windows+10&version=62060833&lang=zh_CN&pass_ticket=j1uTOp9D07FsfGFhPHh28YNCJ%2FyHSoU6yZwOcgzUfvz0aEZLkGZyC5AWXxX7pG28) 框架执行该项目，他训练模型将不同属性的神奇宝贝图像风格相互转换，如将水系转换为火系。

他使用 PyTorch 实现该项目，GitHub 地址：https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix

**训练数据**

Riley Wong 写了一个脚本，将包含 1-7 代神奇宝贝的原始数据集按照主要属性进行分类。

- 原始神奇宝贝图像数据集地址：https://www.kaggle.com/vishalsubbiah/pokemon-images-and-types
- 脚本地址：https://github.com/rileynwong/sort-pokemon-images-by-type
- 按属性分类后的神奇宝贝图像数据集地址：https://github.com/rileynwong/pokemon-images-dataset-by-type

**效果**

下面展示了更多属性转换效果，左侧为神奇宝贝原始图像，右侧为风格迁移后的版本。

**水属性 → 其他属性**

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCib0Y4d6H82jfvDON2NThYz5lI9uJzjjHSsmk8pde8DFZTCmX2PGqNlJw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCib8O84r5dibxrlFjKLlWDa7teJeAHLGl9MC2ZgcgL4mB7QE8icYHzAeia1w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**火属性 → 其他属性**

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibJwgMgNQJ8LhMZHEOfI0xaeiaoicrk340nwkzX3icCdZCib6oFHiaf3lEF0w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibkib3qiccPC9OIJ8WTPXJHAxibubBOhPqqmgLDLjGOJfODszPoP1Cj2Eng/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**草属性 → 其他属性**

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibMUwFG4yraastI2hz8TRRP2Q8Nbt95usyrE21WRTPbqAvpFDZukjSOg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**电属性 → 其他属性**

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibyW4Of8AXXyKmRBiauibbg140mnj8fTJib5acDYib1QUelCFot3JtOXgfdg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**恶属性 → 其他属性**

![img](https://mmbiz.qpic.cn/mmbiz_png/KmXPKA19gW90UwI1pJ8fmO0Xqe4GNWCibWvF2ucBNamOwpNyHuQnygXPvX3H3DH9Ao6dwmDna3ic8FpahLBc0npg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

*参考链接：https://www.rileynwong.com/blog/2019/5/22/pokemon2pokemon-using-cyclegan-to-generate-pokemon-as-different-elemental-types*



**本文为机器之心编译，转载请联系本公众号获得授权。**

✄------------------------------------------------

**加入机器之心（全职记者 / 实习生）：hr@jiqizhixin.com**

**投稿或寻求报道：content@jiqizhixin.com**

**广告 & 商务合作：bd@jiqizhixin.com**









微信扫一扫
关注该公众号