这是一个配合触动精灵的游戏脚本。
实现原理主要是分析游戏画面，但是微信跳一跳游戏画面比较情况复杂，
因此这个脚本的准确率不高，属于练手的项目。

策略：
通过颜色确定微信跳一跳中小人的位置，之后是确定跳跃目标的坐标。
因为下一块目标区域总是位于上方，因此可以通过从上到下扫描来判
断小人下一次是跳左边还是右边，例如先在左侧发现了板子，则下一次
跳到左边。
微信跳一跳的木块有一个特点，其上层表面所有像素的颜色值都是一样
的。因此可以在左右2边找一个“中心点”，这个中心点是各种大小木块
在屏幕显示中都会重合的一个坐标，在中心点附加搜寻是否存在这样的
像素，它的上下左右4个像素的颜色值和它一样，存在则它就是下一个跳跃
目标，否则选择中心点作为默认跳跃目标。

为了提高准确度，代码还对计算的目标坐标进行了一些微调。
脚本主要是通过距离来计算按压时间，可是这之间的关系未必是线性，而且
因为画面显示的其实是一个三维的场景，显然倾斜的视角不是45度，因此在
向左边跳和右边跳的时候，对于相同的屏幕直线距离换算成的按压时间是不
一样的，这点肉眼可以判断出来。

总而言之，通过画面去破解微信跳一跳这个游戏还是挺有难度的，最后写了2
天也没有成功，越到后面特殊的场景出现的越多，准确率也在下降，最高只刷
到了100多分。。。遗憾



main2.lua是网上的一个版本，原理非常简单，但是效率很高，效果很好。