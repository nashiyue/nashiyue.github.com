---
layout: post
title: "Android appcompat_v7" 
date:   2014-12-01 19:06:17
categories: Android
---
   很久没有写Android代码了，在新本上重新安装Android环境，然后测试的时候，
发现新建Hello工程的同时,还多出一个项目appcompat_v7.感觉有点乱，
虽然之前，碰到过这种依赖问题，但是你想啊，新建一个Hello工程,
也给你弄个依赖项目，这也是蛮拼的。

   先简单的介绍下，appcompat_v7 出现的源由：
<b>在22.6.x版本后，为了让Android Project 在API 7+的sdk版本（即Android2.1版本）
可以访问ActionBar的API</b>，才专门增加这个project，目的为了兼容低版本的SDK。

   怎么避免？
在程序配置界面，把Minimum Required SDK （应用程序所支持的Android最低版本）
设置为API14：Android4.0项，其它参数不变。（因为appcompat_v7包是一个能让2.1以上
全使用上4.0版本的界面的支持库，那我们创建项目时直接把最小SDK选在Android4.0以上
就不需要这个支持库了。）
	
<font color="red"><b>注意:</b></font>
  <font color="red">可能会报Java 空指针问题</font>
   找到工程中 <b>project.properties</b> 文件
   将<font color="red">android.library.reference.1=../appcompat_v7</font>这一行删除即可
