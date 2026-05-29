---
title: "在Illustrator中使用LaTeX"
layout: single
# permalink: 
last_modified_at: 2026.5.27
categories:
  - Doc
tags:
  - Illustrator
  - LaTeX
---

在科研绘图中，我们可以充分发挥自己手边的工具：PowerPoint、Visio，甚至像RFC那样直接用ASCII字符作图。但当我们需要快速、精细绘制不区分领域的矢量图形时，Adobe Illustrator（AI）就可以发挥它最大的优势。当然需要注意的是，此AI (Adobe Illustrator)并非彼AI (Artificial Intelligence)，搜索时还是建议使用“Illustrator”等关键词进行搜索。

当使用AI进行实际绘图时，需要接触大量快捷键的使用，故存在一定的学习曲线，不能像Draw.io这类软件一样上手快，有直观的鼠标操作方法。当然，Illustrator默认情况下也没有像Draw.io那样丰富的符号或是箭头自动吸附机制，但你可以从零造一个属于自己的符号库，善用钢笔工具（钢笔工具是一种可以使用“锚点”与“手柄”绘制贝塞尔（Bézier）曲线的工具，具有很强的灵活性。一些翻译也将这位法国工程师Bézier按法语发音翻译为贝济埃），效率会越来越高，同时也对整个图片有更好的掌握。

从上面的分析可以看出，Illustrator可以满足一大部分的科研矢量绘图需求，无论是流程图、示意图还是架构图，总能用某种方法使用Illustrator绘制出来。但是当图中出现了数学符号或者公式，原生 $$\LaTeX$$ 就无从下手了。我们虽然可以获得相应的字体文件，但一个一个调整间距、上下标、大小也是非人力所能及的。

[LaTeX2AI](https://github.com/isteinbrecher/LaTeX2AI)是一款为此需求而生的Illustrator插件，它允许我们在Illustrator中插入各类 $$\LaTeX$$ 公式，并且导出为PDF文件。

这允许我们抛弃活字印刷术，将Illustrator和矢量绘图结合起来，实现各种我们需要的效果。

![示意图]({{ '/assets/images/20251019_illustrator_1.png' | relative_url }})

## 字体缺失

由于 $$\LaTeX$$ 使用的字体较为古老，Illustrator并不支持。即使我们安装了相应字体，在Illustrator中也无法显示，导出时自然会因为无法找到字体而产生意料之外的效果。如下图中红色背景的字符均缺失了相应的字体，回滚到了基础字形。如果公式中掺杂着希腊字母，还会变为小方块，使公式彻底无法阅读。我们希望的是一个pdf文件嵌入后，不会因为字体原因导致在不同设备上显示效果不同。这张图的矢量版理应与打印在“电子纸”上一样，无论这张纸在哪里，上面的内容不能变。

![字体缺失]({{ '/assets/images/20251019_illustrator_2.png' | relative_url }})

普通字体暂且不谈，可以通过嵌入字体文件、嵌入字体子集的形式分发；而如果我们自己也不想装这个字体，即使装了映射可能也会出错，那么就可以采用一种称为“转曲”的操作。使用该操作，将数学公式直接转换为曲线，曲线是不会随着设备迁移而变化的，放之四海而皆准的。故我们可以将字体转为轮廓，一切将恢复原状。

原始文本如下图所示，文本可编辑。
![原始文本]({{ '/assets/images/20260529_illustrator_1.jpg' | relative_url }})

转曲后文本如下图所示，文本不再可编辑，已经成为多条独立曲线。
![转曲文本]({{ '/assets/images/20260529_illustrator_2.jpg' | relative_url }})

虽然文本对象在Illustrator中可以使用“创建轮廓”功能直接转曲，但由于LaTeX2AI插件插入的公式事实上是一个pdf对象，不是文本对象，故可以在“对象 $$\rightarrow$$ 拼合透明度”中勾选“将所有文本转换为轮廓”，此时温暖的，可编辑的数学公式便会成为冰冷的曲线，我们再也无法更改公式的内容，但可以正常导出、对公式上色，或是对公式进行一些奇怪的矢量变换：

![奇怪的变换]({{ '/assets/images/20251019_illustrator_4.svg' | relative_url }})
