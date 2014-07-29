---
layout: default-zh
title: 工具和测试
---

## 压缩, 测试, 和文档化

要运行测试, 生成压缩文件, 或生成文档你的系统需要安装 `node` 和
`grunt-cli`.

* 安装[NodeJS](http://nodejs.org) 要用其官方网站的命令
* 使用 `npm` 来安装 [GruntJS](http://gruntjs.com) 获得command-line支持
	
		npm install -g grunt-cli

接着在你想使用工具的仓库下, 安装node依赖和通过Grunt完成任务.到项目的根目录下(如. `<somepath>/platform/`),运行:

    npm install

### 任务

以上都安装完后,可以运行测试或者通过 `grunt` 来执行任务了.

生成压缩项目文件 (默认):

    grunt

生成文档:

    grunt docs
    
运行测试:

    grunt test

## Source maps

{{site.project_title}} polyfill 了 [HTML Imports](/platform/html-imports.html) 的规范. 为了在运行时能能够调试代码, 组件引用的脚本是被注入到主文档的`<head>`里的. 支持[source maps](http://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) 的工具/浏览器 会识别出这些脚本属于各自的源组件.

## 调试 Shadow DOM

在Chrome里, 默认情况下原生的Shadow DOM 是无法查看的. 也就是说, 你无法通过DevTools翻看一个Shadow Root. 

为了能查看Shadow DOM, 在 DevTools 的设置的General选项卡里将"Show Shadow DOM"勾选:

![Enable "Show Shadow DOM" in the Devtools](/images/showshadowdom.png 'Enable "Show Shadow DOM" in the Devtools')

重启DevTools后, Shadow DOM 已可查看并且渲染成一个个的`#document-fragment`.
