将网页显示成 如 亚洲中华文化圈 传统书写方式 那样的 竖排排版。

Make webs render in vertical lined layout, like traditional CJK writing method in east asian culture circle.

## 使用

1. 安装
   - [AMO Firefox Addon](https://addons.mozilla.org/firefox/addon/vertical-ize-cjk-lines/)
   - 在Firefox/Chrome的addon dev模式中load进去
2. 打开要阅读的网页
   1. 手动从上到下滚动一遍，让所有ajax内容和图片加载（**需要**等所有加载完成！）
   2. 手动滚回顶部，让导航栏位置正确
   3. 调整好窗口高度。这将是转换后的排版宽度
3. 点工具栏上的按钮，转换完成
4. 使用`shift+鼠标滚轮`来在行间滚动

## 效果及兼容性

网页兼容性约80%。

转换后的竖排尽量保留了网页原本横版排版时的元素相对位置。

转换后**原网页的js建立的交互性有损失**，但文字选择、链接点击依旧完美可用（锚链接只能看跳转到刚看见标题）。

这个项目目前位于poc阶段

![](screenshots/李東垣-维基百科.webp)

更多截图见`screenshots/`

## 原理

> 也欢迎开issue探讨

### 当前方案

简要描述：

1. 不得已只能先干掉原网页中的能干掉的脚本

2. 使用CSS`transform`的`rotate`把**整个网页旋转**

3. 使用已旋转过CJK的自定义字体
   
   > 目前是FontForge中乱炖一通出来的。不懂字体，欢迎指正

4. 旋转图片

### 其他方案

尝试过和想过其他方案。有些失败。欢迎探讨

#### 正经方案

- 让浏览器原生支持。等个大神出现改Firefox/Chromium源代码。若w3c定个标准我们就完成任务了

- 使用CSS现有的[`writing-mode: vertical-rl`](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode)（支持不好，不如`sideways-*`）。但这需要整个网页开始设计时就考虑

#### 不正经方案

- 在Firefox的Browser Toolbox（非web toolbox）中将
  
  ```
  html#main-window body hbox#browser vbox#appcontent tabbox#tabbrowser-tabbox tabpanels#tabbrowser-tabpanels.plain hbox#panel-1-92.browserSidebarContainer vbox.browserContainer stack.browserStack browser
  ```
  
  旋转。失败，Firefox崩溃

- 使用旋转CJK的字体和旋转图片后，用canvas或Headless browser等方案对原网页进行实时截图，然后旋转展示截到的图给用户。
  
  这样可以避免去除原网页js，但鼠标如何与内容交互需要一个方案

- 旋转屏幕，系统有这种设置。有些Linux WM据说可以旋转一个窗口

## 其他竖排阅读软件

- Vivaldi的阅读模式支持竖排

移动端支持字定义字体，且支持竖排阅读的APP：

- [静读天下](https://www.moondownload.com/chinese.html)

- [讀書尚友](https://play.google.com/store/apps/details?id=info.ebstudio.bookviewer.free) by 青空文庫ビューア （[官网](http://ebstudio.info)）。支持[iOS](https://apps.apple.com/jp/app/id1579254502)

> 欢迎补充

## 其他传统中华文字相关项目

- 篆书字体收集
  
  [GitHub - garywill/cc-visualize at resource](https://github.com/garywill/cc-visualize/tree/resource)

- [全文繁简字对应关系可视化工具](https://github.com/garywill/cc-visualize)

- [**大术专搜**](https://github.com/garywill/BigSearch/blob/master/src/README_zh.md)（一个搜索、查询工具）中收集的汉语工具部分

