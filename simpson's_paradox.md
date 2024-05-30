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
  <a href="#key-features">前言</a> •
  <a href="#how-to-use">How To Use</a> •
  <a href="#download">Download</a> •
  <a href="#credits">Credits</a> •
  <a href="#related">Related</a> •
  <a href="#license">License</a>
</p>

![screenshot](https://raw.githubusercontent.com/amitmerchant1990/electron-markdownify/master/app/img/markdownify.gif)

## 前言

当一个指标发生变化时，我们往往想通过细分维度的拆解来分析变化原因。比如一个 APP 中指标 **活跃用户数** 增加了 **100**，我们就可能想分别看不同系统（安卓与苹果）中指标的变化。我们期待看到不同系统中指标变化有`超过`和`低于`整体指标变化 **（100）** 的情况，从而找出是哪个系统`驱动`了整体指标的变化。这听起来很合理，对吧？  
    
但对于一个 **比值类指标** 而言，比如点击率，可能会出现整体指标增加，而各个系统中指标都减少的情况。  :scream:  

在我不知道这个东西叫 `辛普森悖论` 之前，我是这么理解这件事情的。如果两边是 **数值类型的指标** 而不是比值类型的指标，比如我们看的是点击数量而不是点击率的变化，就不会出现这个问题，因为 **两边的加和是100%**。即安卓与苹果两个系统的点击数量总和就是整体的点击数量，所以整体数量的增加或者减少一定是由其中一部分来`驱动`的。

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
