---
title: markdown 速查手册
date: 2016-02-28 22:36:40
tags: hexo
categories: work
---

# Markdown 语法速查手册

## 1 标题与文字
### 标题

``` javascript
 # 这是H1 <一级标题>
 ## 这是H2 <二级标题>
 ###### 这是H6<六级标题>
```

## 2 列表
### 无序列表
``` javascript
* 项目1
* 项目2
* 项目3
```
* 项目1
* 项目2
* 项目3

### 有序列表
``` javascript
1. 项目1
2. 项目2
3. 项目3
	* 项目1
	* 项目2
```
1. 项目1
2. 项目2
3. 项目3
	* 项目1
	* 项目2

## 3 其他
### 图片
``` javascript
![图片名称](https://gitcafe.com/assets/project/small_default.png)
```
![图片名称](https://gitcafe.com/assets/project/small_default.png)

### 链接
``` javascript
[链接名称](http://gitcafe.com)
```
[链接名称](http://gitcafe.com)

### 引用
``` javascript
> 第一行引用文字
> 第二行引用文字
```
> 第一行引用文字
> 第二行引用文字

### 水平线
``` javascript
***
```
***

### 代码
``` javascript
`<hello world>`
```
`<hello world>`

### 代码块高亮
``` ruby
	``` ruby
		def add(a, b)
			return a + b
		end
	` ``
```
效果
``` ruby
	def add(a, b)
		return a + b
	end
```


### 表格
``` javascript
	| 表格标题 | 表格标题 |
	| :------: | :------: |
	| 内容| 内容 |
	| 内容| 内容 |
```
| 表格标题 | 表格标题 |
| :------: | :------: |
| 内容| 内容 |
| 内容| 内容 |