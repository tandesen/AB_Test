<h1 align="center">
  <br>
  <img src="https://raw.githubusercontent.com/tandesen/AB_Test/main/pictures/tattoo2.jfif" alt="Markdownify" width="280"></a>
  <br>
  T.S.
  <br>
</h1>

<h4 align="center">辛普森悖论 <a href="https://en.wikipedia.org/wiki/Simpson%27s_paradox" target="_blank">Wiki</a>.</h4>

<p align="center">
  <img src="https://img.shields.io/badge/小红书-德森大老爷-red"
         alt="Gitter">
  <a>
	  <img src="https://img.shields.io/badge/B站-德森大老爷-purple">
  </a>
  <a>
      <img src="https://img.shields.io/badge/github-tandesen-green">
  </a>
  <a>
    <img src="https://img.shields.io/badge/$-donate-ff69b4.svg?maxAge=2592000&amp;style=flat">
  </a>
</p>

<p align="center">
  <a href="#楔子">楔子</a> •
  <a href="#理论解释">理论解释</a> •
  <a href="#辛普森悖论">辛普森悖论</a> •
  <a href="#进一步理解与应对方法">进一步理解与应对方法</a>
</p>


## 楔子

当一个指标发生变化时，我们往往想通过细分维度的拆解来分析变化原因。比如一个 APP 中某个 **点击率** 增加了 **20%**，我们可能想分别看不同系统（安卓与苹果）中指标的变化。我们期待不同系统中有`超过`和`低于`整体指标变化 **（20%）** 的情况，比如安卓涨了 **30%**，苹果涨了 **5%**，从而找出是哪个系统`驱动`了整体指标的增长（安卓）。这很常见，听起来也很合理，对吧？👨‍🦲  

但对于一个 **比值类指标** 而言，比如点击率，可能会出现整体指标增加，而各个系统中指标都减少的情况。 :scream: 比如整体 **点击率** 增加了 **20%**，但每个系统中都减少了 **5%**。  

## 理论解释

在我不知道这个东西叫 `辛普森悖论` 之前，我是这么理解这件事情的。如果两边是 **数值类型的指标** 而不是比值类型的指标，比如我们看的是点击数量而不是点击率的变化，就不会出现这个问题，因为 **两边的加和是100%**。即安卓与苹果两个系统的点击数量总和就是整体的点击数量，所以整体数量的增加或者减少一定是由其中一部分来`驱动`的。但安卓与苹果的点击率之和不是整体的点击率（分母不一样）。  

详细地说，设我们在安卓与苹果上的点击人数分别为 **a** 与 **b**，而浏览页面的人数分别为 **A** 与 **B**，则安卓与苹果的点击率分别为 **$\frac{a}{A}$** 与 **$\frac{b}{B}$**。设我们本周的点击数量在安卓与苹果两个平台上都比上周增加了，用 _下角标1_ 表示上周数据，_下角标2_ 表示本周数据，则有：  

<p align="center">
  $a_2 > a_1$
</p>

<p align="center">
  $b_2 > b_1$
</p>

则我们整体的点击数量一定也增加了。因为由上式可以得到：

$$
(a_2 + b_2) > (a_1 + b_1)  
$$

但对于点击率而言，如果我们有：

<p align="center">
  <h3 align="center">$\frac{a_2}{A_2} > \frac{a_1}{A_1}$</h3>
</p>

<p align="center">
  <h3 align="center">$\frac{b_2}{B_2} > \frac{b_1}{B_1}$</h3>
</p>

则

$$
\frac{a_2}{A_2} + \frac{b_2}{B_2} > \frac{a_1}{A_1} + \frac{b_1}{B_1}
$$

但我们 **不能** 得到：

$$
\frac{a_2+b_2}{A_2+B_2} > \frac{a_1+b_1}{A_1+B_1}
$$

因为分式加法 $\frac{a}{A} + \frac{b}{B} \neq \frac{a+b}{A+B}$ 。我们计算整体点击率 (上面最后这个式子) 和各个系统点击率的时候，分母是不一样的。可能工作中很多时候上面最后这个式子是对的，人们会解释成`某些部分驱动了整体`，但当出现反例时，他们就会惊掉下巴。 :grimacing:  

## 辛普森悖论

当我知道了这个现象叫辛普森悖论之后，查了一些资料，又理解到：

* 出现辛普森悖论时有什么特点？
  - 层级之间 **指标** 数值相差很多。比如前面例子中，点击率指标在安卓和苹果系统的值可能相差很多倍。
  - 层级之间 **分母** 数值相差很多。比如前面例子中，用户浏览数量在安卓和苹果系统可能相差很多倍。而这种相差与 **指标** 值的相差是反过来的。即点击率苹果系统多的话，分母点击数量就是安卓系统多。

出现辛普森悖论的时候最好把具体的分子分母数字写下来，可以更好帮助我们理解，比如：

| 平台系统    | 点击数量（上周） | 浏览数量（上周） | 点击率（上周）  | 点击数量（本周） | 浏览数量（本周） | 点击率（本周）   |
| :---------  | :-----------:  | :----:         | --             |--               | --             |--               |
| 安卓        |  20            | 2000           | 1%              | 250            | 20000          | 1.3%            |
| 苹果        |  14            | 100            | 14%             | 30             | 200            | 15%             |
| 整体        |  34            | 2100           | 1.6%            | 280            | 20200          | 1.4%            |

在上面这个例子中，可以看到安卓系统的点击率从 **1%** 增加到了 **1.3%**，苹果系统的点击率从 **14%** 增加到了 **15%**，但是整体的点击率却下降了，从 **1.6%** 到 **1.4%**。 :octocat:  

仔细观察，就像我们前面说的，点击率这个指标在安卓与苹果两个系统之间相差的是很多的（十倍以上），即上周 **1%** 对比 **14%**，本周 **1.3%** 对比 **15%**。而两个系统的分母（浏览数量）也相差很多，上周 **2000** 对比 **100**，本周 **20000** 对比 **200**，并且浏览数量是安卓系统多，而点击率是苹果系统多。苹果系统少量的点击数量提升带来了明显的点击率提升，而安卓系统由于分母（浏览数量）很大，即使增加了很多点击数量但带来的点击率提升也不明显，被很大的分母 `稀释` 了。

## 进一步理解与应对方法

就像前文说的，我们在看一个 **比值类** 指标的时候除了关注指标本身变化还应该密切关注 `整体体量`。同样的点击率提升 **1%**，对于我们千万级别用户的 APP 与几千个用户级别的情形不可相提并论。再举个极端点的例子，我们是卖土豆 🥔 的商家，计算我们土豆产品在所有土豆中的销售占比。上海是个大城市，整体市场能卖一百万的土豆，而祖国边陲黑龙江是个小地方，整体市场只能卖一千块钱的土豆。我们一袋土豆卖一百块，在黑龙江卖了一袋占的份额是 **100/1000 = 10%**。今天我二大爷过生日高兴我多买了一袋土豆，销售占比一下子提升了 **10%**，作为商家决策者如果只看销售占比这个指标的话，就会决策向黑龙江大量进货进行售卖。但这是不合理的，在大上海，要多卖多少袋土豆才能让指标涨 **10%** 哇！ 😲

* 如何应对辛普森悖论？
  - 统一分母：如果我们想看两个系统中哪个的变化（增长）对整体变化（增长）带来的影响更大，我们可以使用 **增长贡献率** 这类指标，比如安卓系统的增长贡献率是 $\frac{a_2-a_1}{(A_2+B_2)-(A_1+B_1)}$，苹果系统的是 $\frac{b_2-b_1}{(A_2+B_2)-(A_1+B_1)}$。这样统一了比值类指标的分母，所有维度层级的指标总和是 **100%**，就不会出现辛普森悖论。
  - 指标加权：基于维基百科上的解释与建议，我们可以对不同系统的点击率乘以不同的系数来分配权重，但具体怎么分配权重（我想应该是基于分母值）以及如何进行合理的解释说服他人，我不知道。维基百科上还说当出现辛普森悖论的时候往往说明我们拆分的维度不是影响整体指标的关键因素。比如我们这个例子中，整体的点击率的变动并不是由于不同系统造成的（这个我理解也不是很深刻）。
  - 对于**AB实验**：在AB实验中，我们需要对实验组与对照组分配相同的流量（实际中不会 _完全一样_，但也不会相差很多）。而当我们AB实验中某点击率指标发生了辛普森悖论，往往说明我们的分母，即实验组与对照组分配的流量，产生了很大的差距。我们要重新检查实验的设置，看是什么原因导致了流量分配的巨大差异。

---
😎
