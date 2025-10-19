---
title: "在Illustrator中使用LaTeX"
layout: posts
# permalink: 
last_modified_at: 2025.10.19
categories:
  - doc
tags:
  - Illustrator
  - LaTeX
---

在科研绘图中，我们可以充分发挥自己手边的工具：PowerPoint、Visio，甚至像RFC那样直接用ASCII字符作图。但当我们需要快速、精细绘制不区分领域的矢量图形时，Adobe Illustrator（AI）就可以发挥它最大的优势。

AI可以满足一大部分的科研矢量绘图需求，无论是流程图、示意图还是架构图，总能用AI绘制出来。但是当图中出现了数学符号或者公式，原生 $$\LaTeX$$ 就无从下手了。我们虽然可以获得相应的字体文件，但一个一个调整间距、上下标、大小也是非人力所能及的。

[LaTeX2AI](https://github.com/isteinbrecher/LaTeX2AI)是一款为此需求而生的AI插件，它允许我们在AI中插入各类 $$\LaTeX$$ 公式，并且导出为PDF文件。

这允许我们抛弃活字印刷术，将AI和矢量绘图结合起来，实现各种我们需要的效果。

![示意图]({{ '/assets/images/20251019_illustrator_1.png' | relative_url }})

## 字体缺失

由于 $$\LaTeX$$ 使用的字体较为古老，AI并不支持。即使我们安装了相应字体，在AI中也无法显示，导出时自然会因为无法找到字体而产生意料之外的效果。如下图中红色背景的字符均缺失了相应的字体，回滚到了基础字形。如果公式中掺杂着希腊字母，还会变为小方块，使公式彻底无法阅读。

![字体缺失]({{ '/assets/images/20251019_illustrator_2.png' | relative_url }})

因此在AI中嵌入LaTeX2AI产生的pdf文件是不可行的。但如果我们可以将字体转为轮廓，一切将恢复原状。

在AI中，可以在“对象 $$\rightarrow$$ 拼合透明度”中勾选“将所有文本转换为轮廓”，此时温暖的，可编辑的数学公式便会成为冰冷的曲线，我们再也无法更改公式的内容，但可以正常导出、对公式上色，或是对公式进行一些奇怪的矢量变换：

![奇怪的变换]({{ '/assets/images/20251019_illustrator_4.svg' | relative_url }})
