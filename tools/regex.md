# 正则表达式

**todo:**  

- Regex + Python  
- 更高级的用法

[参考](#reference)   
>
- [概要](#general)
- [元字符](#meta)
	- [定位](#location)  [^, $]
	- [字符类别](#classes) [., \w, \s]
	- [特殊空白字符](#white) [\n, \r]
	- [匹配次数](#times)  [*,?]
		- [贪婪匹配](#greedy) 
	- [匹配字符集合和范围](#sets) [a-z]
	- [捕获分组](#group) [(),(?:)]
- [Flags](#flag)
- [示例](#examples)


## <a id='reference'>参考</a>  
- [在线工具](https://regex101.com/) [python, golang, javascript, pcre(php)]
- [Regular expressions quick reference](https://www.computerhope.com/unix/regex-quickref.htm)
- [Computer Hope Regex](https://www.computerhope.com/jargon/r/regex.htm)
- [Python3.6: re — Regular expression operations](https://docs.python.org/3.6/library/re.html)

  
## <a id='general'>概要   
类似方言，每种工具语言都在基础上有自己的添加  
大多数编程语言中的正则表达式基于Perl的兼容正则表达式

难理解：  
1. 表达式写法：紧凑，不易读    
2. 各种语言的表达式语法不一样

   
   
## <a id='meta'>元字符(Standard Regex)   
**元字符(metacharacter)**:  一个字符或字符组合，预留，类似于编程语言中关键字，表示某一操作，e.g. \n表示换新行, ^表示从行首开始。要将元字符作为普通字符使用，需要'\'对其进行转义。


### <a id='location'>定位(Anchors and Boundaries)
>
元字符 | 意义 | 说明
------|-----|----
^ | 从行首开始
$ | 从行尾开始
\b| 单词边界 | ing\b, 匹配单词的末尾的ing； \bhe, 匹配单词首的he
\B| 非单词边界 | \Bing\B, 匹配非单词首尾部分的ing
\\<| 匹配单词首 | Python不支持
\\>| 匹配单词尾 | Python不支持

### <a id='classes'>字符类别(Character Classes)
>
元字符 | 意义 | 说明
---|---|---
. | 匹配除newline[^newline]的任意字符 | Python中newline的元字符为'\n'
\s | 匹配空字符(space, tab, form feed,等) 
\S | 匹配非空字符
\w | 匹配单词字符：字母、数字和下划线， 等同于[a-zA-Z0-9_]
\W | 匹配非单词字符 | 包括\s和部分\S

### <a id='white'>特殊空白符
>
元字符 | 意义 | 说明
-----| -----|-----
\n | a newline 
\t | a tab
\r | 回车键[^cr] | 不同于newline
\v | a vertical tab
\f | a form feed

### <a id='times'>匹配次数(Quantifiers)
>
元字符 | 意义 | 说明
---  | ---- | ----
\* | 匹配之前的字符0次以上 | 贪婪匹配，ca*t, 表示匹配c+a+t组合，其中a可有可无，有的话可以任意多个，ct, cat, caat, caaaat
\+ | 匹配之前的字符1次以上 
? | 匹配之前的字符0次或1次 | 非贪婪匹配
{m} | 匹配m次 | Python中不需'\'转义'{'，直接{m}即可
{m, n} | 匹配m~n次 | Python: {m, n}
{m,} | 匹配至少m次 | Python: {m, }

#### <a id='greedy'>贪婪匹配：
```
*?, +?, ??   
The '*', '+', and '?' qualifiers are all greedy; they match as much text as possible. 
Sometimes this behaviour isn’t desired; 
if the RE <.*> is matched against '<a> b <c>', 
it will match the entire string, and not just '<a>'. 
Adding ? after the qualifier makes it perform the match in non-greedy or minimal fashion;
as few characters as possible will be matched. 
Using the RE <.*?> will match only '<a>'.
```

### <a id='sets'>匹配字符集合和范围(Charater Sets and Ranges)
>
元字符 | 意义 | 说明
---- | ---- | ----
[字符集] | 匹配任一在字符集中的字符 |  [abcd], 匹配任一为abcd其一的字符
[^...] | 匹配任一不属于字符集的字符 | [^abcd], 匹配任一不为abcd的字符
[字符a-字符b] | 匹配任一在a、b字符之间的字符 | 字符范围由ASCII表[^ascii]定，[a-z], [0-9]
a\|b | 或操作，匹配a或b | abc\|xyz, 匹配abc或xyz; c(a\|e)f，匹配caf或cef

### <a id='group'>捕获分组(Capture and Group)
> 捕获其他表达式的匹配，并作为一个字符对待(分组)
>
元字符 | 意义 | 说明
---- |  --- | ----
(...) | 捕获表达式作为一个分组 | Python中不需对()进行转义; (ab){3}，连续匹配ab3次
(?:...) | 捕获但不分组 | Python: (?...); (ab)cd(?:ef), 捕获abcdef, 记ab为分组一，ef不计分组 

[^newline]: newline元字符表示一行的结束和新一行的开始，在编程语言中newline用'\n'表示
[^cr]: [回车键 carriage return](https://www.computerhope.com/jargon/c/cr.htm)
[^ascii]: [ASCII表](https://www.computerhope.com/jargon/a/ascii.htm)


## <a id='flag'>Flags
> 放在正则表达式的末尾，用于补充
> 
字符 | 意义
--- | ---
i | 忽略大小写
m | 多行匹配
s | 匹配新行
x | 允许空格和注释
J | 允许重复的组名
U | 非贪婪模式

## <a id='examples'>示例
![](../imgs/regex_example_email.png)