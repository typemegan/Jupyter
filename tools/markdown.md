
# Markdown语法
[参考](#reference)
> + [标题](#header)
+ [字体格式](#format) [粗体，斜体，下划线，删除线，上标，下标，高亮]
+ [链接](#link)
+ [图片](#picture)
+ [注释](#footnote)
+ [段落](#paragraph)
+ [列表](#list)
+ [表格](#table)

## <a id='reference'>参考</a>
- [commonmark.org: 入门+测试](https://commonmark.org/help/)
- [Formatting your text with Markdown](https://www.pivotaltracker.com/help/articles/formatting_your_text_with_markdown/)
- [Markdown quick reference](https://en.support.wordpress.com/markdown-quick-reference/)


## <a id='header'>标题:</a>
# headline1
## headline2
### headline3
#### headline4  

headline
===
headline2 
---


### 分割线：

---
*** 

## <a id='format'>字体格式：</a>

**bold**  
__strong__  
_斜写_  
*斜写*  
<u>下划线</u>  
hello<sup>上标</sup>   
hello<sub>下标</sub>   
[^4]footnotes[^4]

Amazing  
A*maz*ing  (局部强调)  
<del>删除线</del>  
~~strike through~~ [删除线，显然在Markdown里没有该效果]   
<mark>高亮</mark>  
<span style="background-color:red">高亮</span>  
==高亮== 
 
## <a id='link'>链接</a>
[本地链接](#paragraph)  

[网页链接](https://macdown.uranusjr.com/)   
[索引链接][1]....[索引1][1]...[索引2][2] 所跟的id不显示
[1]:https://github.com/
[2]:https://www.slideshare.net/


## <a id='picture'>图片</a>
![alt text, 可以为空](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRNqCaZ7HmfqsbZh-KEQCiFlW8QTt_OBgvCQRbGOA8OLmMjWpYzng) [显示链接图片，不显示链接信息，也不可跳转]    

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRNqCaZ7HmfqsbZh-KEQCiFlW8QTt_OBgvCQRbGOA8OLmMjWpYzng" width="50" height="60"> [设置显示的图片大小]    

![](../imgs/hellokitty_48px.png) [插入本地图片]   
<img src="../imgs/hellokitty_48px.png"> [插入本地图片]

索引图片:![][img_index]...![][img_index]
[img_index]:../imgs/hellokitty_48px.png "图片标题，可以为空"


## <a id='footnote'>Footnotes(注释)</a>
李白[^李白]与杜甫[^杜甫] 唐诗[^李白] [貌似一个注释只能用在一处]

[^李白]: 李白，唐代诗人
[^杜甫]: 杜甫，唐代诗人   
[^辛弃疾]: 宋代

## <a id='paragraph'>段落</a>

#### 换行: 
space*2+enter    
或者\+换行\
    
#### 块(BlockQuote)：
> 块  
> > 内块
> > > 内内块

#### 代码段：   
<code>
a=100   
for i in range(100):  
	 print(i)
</code>

`printf`

```
alert 'hello'
generator
iterable
```
    行首缩进至少4个空格

语法高亮:
     
```css
#button {
	border: none;
}
```

```python
import os
print()
x = 12
```

## <a id='list'>列表：</a>
* 无序
* 无序
- 无序
- 无序
+ 无序
+ 无序

1. 有序
2. 有序

**注意：行首任意数字后跟点都会被视为列表**   
解除：转义点    
1989. [未转义]  
1989\. [转义后]


## <a id='table'>表格</a>
列1 | 列2
--- |----
1   | 2 
3   | 4

左对齐 | 居中对齐 | 右对齐
:--- |:------:| ----:
12   |  12    | 12
55   |   20 |56


