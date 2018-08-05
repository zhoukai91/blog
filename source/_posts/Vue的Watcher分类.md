---
title: Vue中Watcher的分类
type: "vue"
date: 2018-05-06
categories: vue
tags: vue
---

刚刚看了一篇关于介绍Watcher的文章，让我茅塞顿开。在此记录下自己对Watcher的理解。

Watcher分类
---------
**内部-watcher**
vue组件上的每一条数据绑定指令(例如`{{myData}}`)和computed属性，通过compile最后都会生成一个对应的 watcher 对象。

**user--watcher**
 在watch属性中，由用户自己定义的，都属于这种类型，即只要监听的属性改变了，都会触发定义好的回调函数


**render-watcher**
每一个组件都会有一个 render-watcher, `function () {vm._update(vm._render(), hydrating);}`, 当 data/computed中的属性改变的时候，会调用该 render-watcher 来更新组件的视图


**三种 watcher 的执行顺序**
watcher 也有固定的执行顺序，分别是:

> 内部-watcher -> user-watcher -> render-watcher

优先执行内部watcher是为了保证指令和DOM节点的优先更新，这样当用户自定义的Wathcer的回调函数触发时DOM已经更新完毕。

ps：Vue里面的概念真是太多了，让我们这些初学者情何以堪！
心得：多多吸收知识，当杂乱的知识点多了以后，也许一个简单的Tip，就是一次知识的升华！ “^_^”


