---
layout: default-zh
title: 获取源码
---

## 拷贝代码!

你通过一个Git命令就能递归拷贝, 初始化{{site.project_title}}的所有模块.

**要获取源码,运行:**

    git clone git://github.com/Polymer/polymer-all.git --recursive

这将生成一个`polymer-all/`文件夹,文件夹目录如下:

- **platform/** — Platform片段和Polyfill.
- **polymer/polymer.js** — [{{site.project_title}} 核心](polymer.html)
- **polymer-elements/** — 核心工具元素集.
- **polymer-ui-elements/** — UI元素集.
- **projects/** — 基于{{site.project_title}}的大型实例,demo,工具等.
- 每个Platform (polyfill) 都有各自同级的目录列表.

更多代码库存储的目录结构如下.

### 环境测试

要检测你的开发环境是否正常,架一个本地Web服务器并运行自带的任意实例项目:

1. **开启本地Web服务器** 于签出得的 `polymer-all/`目录下.
2. 在浏览器里导航至
    [http://localhost/toolkit-ui/workbench/menu.html](http://localhost/toolkit-ui/workbench/menu.html), 或者你服务器运行的对应端口. 你会看到如下的菜单.

<iframe src="/polymer-all/toolkit-ui/workbench/menu.html" style="width:270px;height:220px;border:none;"></iframe>

### 关于分支

参看 [打分支流程](branching-strategy.html).

### 更新 {{site.project_title}} 的子模块

我们会定期在GitHub更新项目的子模块. 要更新你本地的模块副本, 在`polymer-all/` 目录下运行命令:

    git submodule update --init --recursive

## 存储的目录结构

整个{{site.project_title}}项目是由多个Git代码库组成. 都以子模块的形式包含在`polymer-all` 目录下.
不过, 理解方方面面有助于你翻阅代码库.

我们已经将代码库划分成了详细的块. 例如, 以下的代码库可能是很特殊的:

* `CustomElements`
* `HTMLImports`
* `ShadowDOM`
* `mdv`
* `PointerGestures`

有些代码库依赖于{{site.project_title}} 的其他库,而且必须是同级目录下才功能完整:

* `polymer`
* `platform`
* `toolkit-ui`

### /platform 库

[github.com/polymer/platform](https://github.com/polymer/platform)

每个Web平台特性都有对应的polyfill库.基于以下两条原因:

1. 使每个polyfill都能跨(现代)浏览器
2. 使每个polyfill都独立成形,并且能在项目中任意引用.

[`platform`](https://github.com/polymer/platform) 库与每个polyfill都同级目录对应, 包含最终合成polyfill所需的一体化的测试, 加载器, 和构建工具.

更多请参看 [工具和测试](tooling-strategy.html).

### /polymer 库

[github.com/polymer/polymer](https://github.com/polymer/polymer)

[`polymer`](https://github.com/polymer/polymer) 库包含了项目的关键. 它期望[`platform`](https://github.com/polymer/platform)的
polyfill库目录是同级的, 并通过它的工具和测试用例管理着
[{{site.project_title}} 核心](polymer.html).

如果你想查看开发进度, 直接签出 _master_ 分支:

    git clone -b master https://github.com/Polymer/polymer.git --recursive

<p class="alert">
<b>记住</b>: 如果你不指定 <em>master</em>, 默认得到的是 <em>stable</em> 分支.
更多请参看 <a href="branching-strategy.html">打分支流程</a>.
</p>

### /toolkit-ui 库

[github.com/polymer/toolkit-ui](https://github.com/polymer/toolkit-ui)

[`toolkit-ui`](https://github.com/polymer/toolkit-ui) 库包含有当你要写一个[{{site.project_title}} element](polymer.html)时所需的东西的类型的实例.

- **elements/** — `g-*` Custom Elements的定义.
- **workbench/** — `elements/` 里能找到的{{site.project_title}}-style元素的demo.

