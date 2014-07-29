---
layout: default-zh
title: 入门指南

load_polymer: true

imports:
#- toolkit-ui/elements/g-panels.html
#- toolkit-ui/elements/g-tabs.html
#- samples/components/basic-element.html
#- samples/components/tk-element.html
#- samples/components/tk-element-databinding-color.html
#- samples/components/tk-element-databinding.html
#- samples/components/tk-element-ready.html
#- samples/components/tk-element-property-public.html
#- samples/components/tk-element-property-public-publish.html
#- samples/components/tk-element-event-binding.html
#- samples/components/tk-element-public-access.html
#- samples/components/tk-node-finding.html
##- samples/components/tk-twoway-binding.html
#- samples/components/tk-binding-to-elements.html
---

[Custom Elements](/platform/custom-elements.html) 是基于
{{site.project_title}} 的应用的核心开发组件. 你通过将这些Custom Elements整合到一块来开发应用,这些Custom Elements要么是
{{site.project_title}}提供的,要么是你自己创建的,或者第三方的.

## 基础

{{site.project_title}} 通过提供更多吸引人的东西来发展[Custom Elements](/platform/custom-elements.html) 的概念. 不过, 如果你只对创建一个通用的的Custom Element有兴趣, `platform.js`就足够了. 它包含的正是平台上所缺失的特性的polyfills,如[Shadow DOM](platform/shadow-dom.html) 和 [HTML Imports](platform/html-imports.html).

1. 加载 **platform.js** 来弥补平台所缺失的特性.
2. 和组件一起加载`<link rel="import" href="/path/to/component-file.html">`
3. 在你的页面里引用custom element.

这是个纯例子:

    <!DOCTYPE html>
    <html>
      <head>
        <!-- 1. 弥补平台所缺失的特性 -->
        <script src="polymer-all/platform/platform.js"></script>
        <!-- 2. 加载组件 -->
        <link rel="import" href="x-foo.html">
      </head>
      <body>
        <!-- 3. 用组件的标签声明组件. -->
        <x-foo></x-foo>
      </body>
    </html>

<p class="alert"><b>注意</b>: 你必须要在Web服务器里运行你的应用. 
这是使<a href="/platform/html-imports.html">HTML Imports</a> 此polyfill
  正常工作的正确方式. 这个需要会在浏览器原生支持后消失的.</p>

## 组件

### 创建一个基础的custom element

{{site.project_title}}所提供的平台化的polyfill允许你加载和显示
custom elements. 只需加载`platform.js` 就能得到这项新技术的支持.

{% include samples/basic-element.html %}

**提示:** `name` 属性是必需的,指定的即是你所写的标签(例. `<tag-name>`). 它必须是以 "-" 分隔的字符串.
{: .alert }

### 创建一个{{site.project_title}} 元件

{{site.project_title}} 提供更多吸引人的东西来创建custom elements. 我们将这类增加的 custom elements 称之为"{{site.project_title}} elements". 要新建一个, 跟着以下步骤:

1. 载入 [{{site.project_title}} 核心](/polymer.html) (`polymer/polymer.js` or `polymer.min.js`).

    **注意:** 加载`polymer.js` 会载入 `platform.js`.
录你要写一个{{site.project_title}} element时你仅需要加载`polymer.js` .
    {: .alert }

1. 用 `<polymer-element>`声明你的custom element .

下面实例中, 我们已经将基础的 custom element 转换成一个名为`tk-element`的{{site.project_title}} element .

{% include samples/tk-element.html %}

#### 给你的组件追加属性/方法

如果你想为你的element追加公共的属性/方法,
引入一个`<script>` 调用 `{{site.project_title}}('your-tagname')`.
`{{site.project_title}}(..)` 是个为[`document.register`](/platform/custom-elements.html#documentregister) 提供的快捷包装, 同时也赋予了element特殊的特性像数据绑定和事件映射. 
它的第一个参数是你所创建的element的名称. 第二个参数 (可选) 是一个用来定义你的element的 `prototype` 的对象. 

{% include samples/tk-element-proto.html %}

## 声明式的数据绑定

你可以将属性绑定到你的组件上,使用声明式的数据绑定和来自 [Model Driven Views](/platform/mdv.html) 的 "double-mustache" 语法 (`{%raw%}{{}}{%endraw%}`). 
`{%raw%}{{}}{%endraw%}` 将被括号之间引用的属性的值所替换.

{% include samples/tk-element-databinding.html %}

### 绑定到标记上

你可以在大部分HTML标记上使用绑定表达式, 除了标记本身的名称. 以下实例里, 我们为组件新建了一个叫`color`的属性,它的值被绑定到了custom element的样式的`color`属性上.

{% include samples/tk-element-databinding-color.html %}

### 组件和原生elements之间的绑定 ####

以下实例演示了组件属性绑定到原生input elements的属性上.

{% include samples/tk-binding-to-elements.html %}

## 追加生命周期方法ready()

当一个element被成功注册并初始化好后,它会调用自己的`ready` 方法, 如果有的话. `ready` 回调是类构造函数作初始化处理的最佳地方.

{% include samples/tk-element-ready.html %}

## 属性的公布

属性的公布可以用来定义一个element的 "公共 API". {{site.project_title}}
为公布的属性制定了双向数据绑定且可以使用MDV的 `{%raw%}{{}}{%endraw%}`来访问属性的值.

要_公布_ 一个属性,可通过在你的`<polymer-element>`的`attributes`列表里追加属性的方式. 如此声明的属性默认值是`null`. 
要自定义属性的默认值,需将同名的属性追加到组件的注册时的属性上(如下).

以下实例是在element上定义了两个绑定数据和属性, `owner` 和 `color`,并赋予它们默认值:

{% include samples/tk-element-property-public.html %}

注意: 本实例里用户通过配置element的初始的属性值修改了`owner` 和 `color`的默认值(例. `<tk-element-property-public owner="Scott" color="blue">`).

[更多属性的公布参看](/polymer.html#published-properties)

{% comment %}
#### 使用公共的对象(高级)

还有另一个办法可以公布一个属性 (但你可能永远不会用到它): 即 `publish` 对象. 在`publish`对象里的属性将如列在`attributes`的属性一个被公布.

{% include samples/tk-element-property-public-publish.html %}

### 监听切换

### 在一个element上访问公共属性

一个element的公共属性可以在自身的custom element通过属性来设置, 如 `index.html` 所示.

{% include samples/tk-element-public-access.html %}  
{% endcomment %}


## 自动节点索引

Shadow DOM 是个自包含的类document的子树; 那里边的id不受其他树里面的id的影响. 每个 {{site.project_title}} element 都在element的模板里生成一份id对节点的映射图. 此映射图可以通过`$` 在element上索引到. 

{% include samples/tk-node-finding.html %}
