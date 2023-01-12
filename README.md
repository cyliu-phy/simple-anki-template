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
