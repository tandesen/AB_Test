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
  <a href="#进一步理解与应对方法">进一步理解与应对方法</a> •
  <a href="#related">Related</a> •
  <a href="#license">License</a>
</p>

![screenshot](https://raw.githubusercontent.com/amitmerchant1990/electron-markdownify/master/app/img/markdownify.gif)

## 楔子

当一个指标发生变化时，我们往往想通过细分维度的拆解来分析变化原因。比如一个 APP 中某个 **点击率** 增加了 **20%**，我们就可能想分别看不同系统（安卓与苹果）中指标的变化。我们期待不同系统中有`超过`和`低于`整体指标变化 **（20%）** 的情况，比如安卓涨了 **30%**，苹果涨了 **5%**，从而找出是哪个系统`驱动`了整体指标的增长（安卓）。这很常见，听起来也很合理，对吧？  

但对于一个 **比值类指标** 而言，比如点击率，可能会出现整体指标增加，而各个系统中指标都减少的情况。 :scream: 比如整体 **点击率** 增加了 **20%**，但每个系统中都减少了 **5%**。  

## 理论解释

在我不知道这个东西叫 `辛普森悖论` 之前，我是这么理解这件事情的。如果两边是 **数值类型的指标** 而不是比值类型的指标，比如我们看的是点击数量而不是点击率的变化，就不会出现这个问题，因为 **两边的加和是100%**。即安卓与苹果两个系统的点击数量总和就是整体的点击数量，所以整体数量的增加或者减少一定是由其中一部分来`驱动`的。  

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
  $\frac{a_2}{A_2} > \frac{a_1}{A_1}$
</p>

<p align="center">
  $\frac{b_2}{B_2} > \frac{b_1}{B_1}$
</p>

则

$$
\frac{a_2}{A_2} + \frac{b_2}{B_2} > \frac{a_1}{A_1} + \frac{b_1}{B_1}
$$

但我们 **不能** 得到：

$$
\frac{a_2+b_2}{A_2+B_2} > \frac{a_1+b_1}{A_1+B_1}
$$

因为分式加法 $\frac{a}{A} + \frac{b}{B} \neq \frac{a+b}{A+B}$ 。我们计算整体点击率和各个系统点击率的时候，分母是不一样的。可能工作中很多时候上式是对的，人们会解释成`部分驱动整体`，但出现反例时，他们就会惊掉下巴 :grimacing:  

## 辛普森悖论

当我知道了这个现象叫辛普森悖论之后，查了一些资料，又理解到：

* 出现辛普森悖论时有什么特点？
  - 层级之间 **指标** 数值相差很多。比如前面例子中，点击率指标在安卓和苹果系统的值可能相差很多倍。
  - 层级之间 **分母** 数值相差很多。比如前面例子中，用户浏览数量在安卓和苹果系统可能相差很多倍。而这种相差与 **指标** 值的相差是反过来的。即指标值苹果系统多的话，分母就是安卓系统多。

出现辛普森悖论的时候最好把具体的分子分母数字写下来，可以更好帮助我们理解，比如：

| 平台系统    | 点击数量（上周） | 浏览数量（上周） | 点击率（本周）  | 点击数量（本周） | 浏览数量（本周） | 点击率（本周）   |
| :---------  | :-----------:  | :----:         | --             |--               | --             |--               |
| 安卓        |  20            | 2000           | 1%              | 250            | 20000          | 1.3%            |
| 苹果        |  14            | 100            | 14%             | 30             | 200            | 15%             |
| 整体        |  34            | 2100           | 1.6%            | 280            | 20200          | 1.4%            |

在上面这个例子中，可以看到安卓系统的点击率从 **1%** 增加到了 **1.3%**，苹果系统的点击率从 **14%** 增加到了 **15%**，但是整体的点击率却下降了，从 **1.6%** 到 **1.4%**。 :octocat:  

仔细观察，就像我们前面说的，点击率这个指标在安卓与苹果两个系统之间相差的是很多的（十倍以上），上周 **1%** 对比 **14%**，本周 **1.3%** 对比 **15%**。而两个系统的分母（浏览数量）也相差很多，上周 **2000** 对比 **100**，本周 **20000** 对比 **200**，并且浏览数量是明显安卓系统多，而点击率明显是苹果系统多。苹果系统少量的点击数量提升带来了明显的点击率提升，而安卓系统由于分母（浏览数量）很大，即使增加了很多点击数量但带来的点击率提升也不明显，被很大的分母 `稀释` 了。

## 进一步理解与应对方法

就像前文说的，我们在看一个 **比值类** 指标的时候除了关注指标本身变化还应该密切关注 `整体体量`。同样的点击率提升 **1%**，对于我们千万级别用户的 APP 与几千个用户级别的情形不可相提并论。再举个极端点的例子，我们是卖土豆 🥔 的商家，计算我们土豆产品在所有土豆中的销售占比。上海是个大城市，整体市场能卖一百万的土豆，而祖国边陲黑龙江是个小地方，整体市场只能卖一千块钱的土豆。我们一袋土豆卖一百块，在黑龙江卖了一袋占的份额是 **$100/1000 = 10%$**。今天我二大爷过生日高兴我多买了一袋土豆，销售占比一下子提升了 **10%**，作为商家决策者如果只看销售占比这个指标的话，就会决策向黑龙江大量进货进行售卖。但这是不合理的，在大上海，要多卖多少袋土豆才能让指标涨 **10%** 哇！ 😲

* 如何应对辛普森悖论？
  - 统一分母：如果我们想看两个系统中哪个的变化（增长）对整体变化（增长）带来的影响更大，我们可以使用 **增长贡献率** 这类指标，比如安卓系统的增长贡献率是 $\frac{a_2-a_1}{(A_2+B_2)-(A_1+B_1)}$，苹果系统的是 $\frac{b_2-b_1}{(A_2+B_2)-(A_1+B_1)}$。这样统一了比值类指标的分母，所有维度层级的指标总和是 **100%**，就不会出现辛普森悖论。
  - 调配比例
  - 对于 **AB实验**，



* 点击率指标对比上周下降了，但是在苹果与安卓两个平台都下上升了，这可能么？为什么？
  - Instantly see what your Markdown documents look like in HTML as you create them.
* Sync Scrolling
  - While you type, LivePreview will automatically scroll to the current location you're editing.
* GitHub Flavored Markdown  
* Syntax highlighting
* [KaTeX](https://khan.github.io/KaTeX/) Support
* Dark/Light mode
* Toolbar for basic Markdown formatting
* Supports multiple cursors
* Save the Markdown preview as PDF
* Emoji support in preview :tada:
* App will keep alive in tray for quick usage
* Full screen mode
  - Write distraction free.
* Cross platform
  - Windows, macOS and Linux ready.

## How To Use

To clone and run this application, you'll need [Git](https://git-scm.com) and [Node.js](https://nodejs.org/en/download/) (which comes with [npm](http://npmjs.com)) installed on your computer. From your command line:

```bash
# Clone this repository
$ git clone https://github.com/amitmerchant1990/electron-markdownify

# Go into the repository
$ cd electron-markdownify

# Install dependencies
$ npm install

# Run the app
$ npm start
```

> **Note**
> If you're using Linux Bash for Windows, [see this guide](https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/) or use `node` from the command prompt.


## Download

You can [download](https://github.com/amitmerchant1990/electron-markdownify/releases/tag/v1.2.0) the latest installable version of Markdownify for Windows, macOS and Linux.

## Emailware

Markdownify is an [emailware](https://en.wiktionary.org/wiki/emailware). Meaning, if you liked using this app or it has helped you in any way, I'd like you send me an email at <bullredeyes@gmail.com> about anything you'd want to say about this software. I'd really appreciate it!

## Credits

This software uses the following open source packages:

- [Electron](http://electron.atom.io/)
- [Node.js](https://nodejs.org/)
- [Marked - a markdown parser](https://github.com/chjj/marked)
- [showdown](http://showdownjs.github.io/showdown/)
- [CodeMirror](http://codemirror.net/)
- Emojis are taken from [here](https://github.com/arvida/emoji-cheat-sheet.com)
- [highlight.js](https://highlightjs.org/)

## Related

[markdownify-web](https://github.com/amitmerchant1990/markdownify-web) - Web version of Markdownify

## Support

<a href="https://www.buymeacoffee.com/5Zn8Xh3l9" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/purple_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

<p>Or</p> 

<a href="https://www.patreon.com/amitmerchant">
	<img src="https://c5.patreon.com/external/logo/become_a_patron_button@2x.png" width="160">
</a>

## You may also like...

- [Pomolectron](https://github.com/amitmerchant1990/pomolectron) - A pomodoro app
- [Correo](https://github.com/amitmerchant1990/correo) - A menubar/taskbar Gmail App for Windows and macOS

## License

MIT

---

> [amitmerchant.com](https://www.amitmerchant.com) &nbsp;&middot;&nbsp;
> GitHub [@amitmerchant1990](https://github.com/amitmerchant1990) &nbsp;&middot;&nbsp;
> Twitter [@amit_merchant](https://twitter.com/amit_merchant)
