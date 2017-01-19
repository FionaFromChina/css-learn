#### 介绍

对于小的网站，你如何去组织CSS并不是很重要。你可以随便写一些CSS，也可以写一些SASS然后转换成一个CSS。

但随着网站的规模逐渐增大，项目也变得越来越复杂，你如何去组织自己的代码会影响到至少三个方面的效率：1）如何组织代码会影响到你需要花多长的时间来写代码；2）你需要写多少代码量；3）浏览器需要花多长时间来加载你的代码。同时，如果你是参与团队协作的话，高性能的代码就是非常必要的，如何去组织代码也就变得非常重要了。

上面的经验对于一个有着遗留代码的长期项目来说也是适用的。（可以参考另外一篇介绍如何维护遗留css的方法[1]）

#### 方法
有很多旨在减少CSS冗余，组织程序之间的合作和维护大型的CSS代码库的方法论（[2]）。在Twitter,FaceBook和Github上是卓有成效的，但其他很多项目都是很快地变成了一个“巨大的CSS”文件。

#### 常用的CSS处理方法
1. OOCSS[3]
2. SMACSS[4]
3. SUITCSS[5]
4. Atomic[6]
#### 为什么BEM比其他的方式好？

不管你决定在项目中使用哪种方法论，你都会从更有结构化的CSS和UI里面获益。有些风格可能不那么严谨，比较灵活，也可能有些会比较容易理解，能够更加适应团队开发。

> 我选择BEM方式而不是其他方式的原因是：相比较其他方法，它更不容易造成困惑（比如SMACSS），但依然能够用容易被识别的术语给我们提供一个好的架构方式。[7]


#### 块、元素和状态(modifier)
BEM是Block,Element和Modifier的缩写，具体的命名方法可以在这里看到。[8]

* Block：有明确意义的独立实体。如：header,container,menu,checkbox,input
* Element: 是Block的一部分，没有独立意义且依附于Block。如：menu-item,list-item,checkbox-caption,header-title
* Modifier: Block 或者Element的一个标志，用来改变外观或者行为。如：disabled,highlighted,checked,fixed,size,big,color-yellow

#### Under the hood
让我们来具体看一个例子，页面上一个具体元素如果用BEM的方式进行组织。我们以GitHub上的button为例子[9]

我们可以有一个普通的Button用于普通的例子，另外两个特殊的状态用于其他状态。因为我们使用BEM方法来命名类名，可以用Button，a，甚至div来命名，但命名规则需要遵循B-E-M语法。

```
HTML 
<button class="button">
Normal button
</button>

<button class="button button-state-success">
Success button
</button>

<button class="button button-state-danger">
Danger button
</button>
```
```
CSS
.button{
    display:inline-block;
    border-radius:3x;
    padding:7px 12px;
    border:1px solid #D5D5D5;
    background-image:liner-gradient(#EEE,#DDD);
    font:700 13px/18px Helvetica,arial;
}
.button-state-success {
    color:#FFF;
    background:#569E3D linner-gradient(#79D858,#569E3D) repeat-x;
    border-color:#4A993E;
    
}
.button-state-danger{
    color:#900;
}
```

#### 好处
* 模块化：这种命名方法不依赖于页面其他元素，所以不会有层叠的困扰。[10] 这样的话，也可以把样式从已经完成的项目转移到新的项目中去。
* 可重用性：将独立的块用不同的方法组织起来，并去重用它们，可以减少需要维护的CSS代码量。 通过一套风格指导，你可以构建Block的一套代码库，从而使CSS更加高效。
* 结构化：BEM使CSS代码有一个固定、简单的风格，易于阅读和理解。


#### 扩展阅读

1. https://blog.decaf.de/2015/06/24/why-bem-in-a-nutshell/
2. http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/
3. http://cssguidelin.es/#bem-like-naming
4. https://www.smashingmagazine.com/2014/07/bem-methodology-for-small-projects/
5. http://www.slideshare.net/MaxShirshin/bem-it-for-brandwatch
6. https://www.phase2technology.com/blog/used-and-abused-css-inheritance-and-our-misuse-of-the-cascade/
7. https://medium.com/objects-in-space/objects-in-space-f6f404727
8. https://webuild.envato.com/blog/how-to-scale-and-maintain-legacy-css-with-sass-and-smacss/
9. http://bluegg.co.uk/blog/building-my-health-skills-part-3


#### 例子学习
我们希望能够尽快给出“如何能够将现有的项目改造成BEM风格”的文章。同时你可以观看Nicole Sullivan的“CSS预编译高性能”。她给出了一个网站上普遍存在的一个问题并提出了如何追踪和解决他们的方案。


#### 附：

[1]. https://webuild.envato.com/blog/how-to-scale-and-maintain-legacy-css-with-sass-and-smacss/

[2]. https://github.com/ikkou/awesome-css#architecture

[3]. http://oocss.org/

[4]. http://smacss.com/

[5]. http://suitcss.github.io/

[6]. https://github.com/nemophrost/atomic-css

[7]. http://www.integralist.co.uk/posts/bem.html#4

[8]. http://getbem.com/naming/

[9]. http://primercss.io/buttons/

[10]. https://www.phase2technology.com/blog/used-and-abused-css-inheritance-and-our-misuse-of-the-cascade/

