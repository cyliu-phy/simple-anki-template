Anki模板介绍

## 简介
本人自用Anki模板，特点:
1. 颜值高（个人认为），模仿的少数派的样式，然后自行调整了行间距边距等，达到一个自己看着比较顺眼的程度
2. 数学公式用katex，渲染速度比默认mathjax快，大片公式速度提升明显
3. 更容易挖空，选中文字 `ctrl-u` 下划线即可挖空，而且挖空支持逐个显示，点击空格所在地方就会自动显示，再次点击会隐藏，点击反面会显示所有挖空。相比默认的cloze模板交互上还是更方便一点。
4. 代码高亮，使用prismjs进行代码高亮，只需写markdown风格的代码块即可自动高亮，例如

<pre><code>
```python
import this
love = this
this is love
True
```
</code></pre>

<details><summary>预览</summary>
<img src="https://s1.ax1x.com/2023/01/13/pSKC3y6.png">
</details>

但是要注意，代码块支持的换行仅有`<br>` 和换行符`\n`，如果高亮出现问题请 `ctrl-shift-x` 检查html源代码，有可能是别处复制的代码块带了原来的格式，用 `<p>` 和 `<div>` 换行，这种情况下可以 `ctrl-shift-v` 不带格式复制或者 `ctrl-shift-x` 直接把代码复制到html编辑器里。安卓上使用直接复制一般都正常，因为安卓复制会自动去掉格式。

## 使用方法
1. [release](https://github.com/cyliu-phy/simple-anki-template/releases)页面下载最新的文件，找到apkg文件，电脑上选择用Anki打开，AnkiDroid上点击右上角三个点，选择导入，导入apkg文件，在文件管理里找到下载的模板即可
2. 下载 media.7z 文件，解压到媒体文件夹，安卓上是`AnkiDroid/collection.media`，Windows上是`C:\Users\<your name>\AppData\Roaming\Anki2\<your profile>\collection.media`，Linux上是`~/.local/share/Anki2/<your profile>/collection.media`
3. 点击加号，添加卡片，类型里选择Basic(Advanced)，在各个字段添加需要的内容即可，其中只有第一个字段必填，其他字段不填相应部分不会显示。

<details><summary>预览</summary>
<img src="https://s1.ax1x.com/2023/01/13/pSKCD6P.png">
<img src="https://s1.ax1x.com/2023/01/13/pSKC60S.png">
<img src="https://s1.ax1x.com/2023/01/13/pSKC2kQ.png">
<img src="https://s1.ax1x.com/2023/01/13/pSKCWfs.png">
</details>

## 使用Material-Reviewer教程
<s>因为AnkiDroid自带的Appbar和Answer button在平板上占的空间太大，而且颜色和模板背景颜色不和谐，一直打算自己做一个，好在Anki在去年就开放了[JavaScript API](https://github.com/ankidroid/Anki-Android/wiki/AnkiDroid-Javascript-API)为模板创作增加了更多的可能性，看了看给的实例代码，发现已经有人做过了，https://github.com/krmanik/ankidroid-js-addon/tree/main/Reviewer%20addons/ankidroid-js-addon-material-reviewer/package ，那么就可以直接拿来用，首先，下载`index.js`和`Material-Icons.woff2`这两个文件，然后把index.js里面
```js
    src: local('Material Icons'), local('MaterialIcons-Regular'), url(../addons/ankidroid-js-addon-material-reviewer/package/Material-Icons.woff2);
```
改为
```js
    src: local('Material Icons'), local('MaterialIcons-Regular'), url(Material-Icons.woff2);
```
然后将这两个文件复制到上面说的媒体文件夹，在模板前面加上
```html
<script src="index.js"></script>
```

设置里`Apperance->Fullscreen mode->Hide the system bars and answer buttons`打开，把AnkiDroid自带的Appbar和Answer button隐藏掉。

![](https://s1.ax1x.com/2023/05/02/p9GGfyT.jpg)
</s>

此脚本在新版AnkiDroid上已失效，新的api似乎还没稳定，调用时有时候返回的是string有时候是map，太折腾了故放弃维护，好在最新版AnkiDroid已经原生支持了新Reviewer，在`Settings->About`界面连点8次图标启用开发者模式，然后在开发者模式菜单里启用New reviewer

![](https://s21.ax1x.com/2024/10/29/pA0O2Ss.jpg)

## 换字体教程
如果想换字体，第一步，把字体文件复制到媒体文件夹下，第二步，在模板style里面加上
```css
@font-face {
  font-family: "FontName";
  src: url("字体文件名");
}
```

然后再改
```css
.card {
	font: 20px/30px serif,'Noto Serif CJK SC';
}
```
在serif前面加上
```css
.card {
	font: 20px/30px FontName,serif,'Noto Serif CJK SC';
}
```
字体是按顺序加载的，如果前面的字体找不到相应的字会fallback到后面的，都找不到会fallback到系统字体。

## 已知问题
1. ~~使用material reviewer和自定义字体可能会造成卡片渲染卡顿，而且在有的设备、AnkiDroid版本上会导致我写的挖空代码执行比较慢，于是会出现挖空内容先出现再隐藏，根据自己设备按需使用，不要一味追求好看。~~
2. ~~material reviewer的anwser button高度可能不够，上面的文字可能显示不全，请自行修改 115行 `height`的值，以及没有适配夜间模式，需要的可以仿照我的模板里`style`里对dark mode的适配自行修改js脚本里`jsAddonStyleSheet`的值。~~
3. ~~新版AnkiDroid已经将媒体文件夹移动到`/sdcard/Android/data/com.ichi2.anki/files/AnkiDroid/collection.media/`，这个目录需要`SAF` (Storage Access Framework)或者adb才能访问，需要稍微折腾一下~~   
又改回来了
4. Anki媒体文件不支持同步文件夹，所以里面的katex相关的代码不会通过Ankiweb自动同步，需要手动复制进去
