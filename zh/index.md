---
layout: default-zh
#title: Welcome
---

{% include zh/alpha.html %}

{{site.project_title}} 是一个全新的Web库, 于Web组件的基础之上构建,被设计成引领Web平台在现代浏览器上的发展.
{: .lead }

<p class="download centered"><a href="https://github.com/{{site.project_title}}/polymer-all/releases/download/v{{site.latest_version}}/polymer-all-v{{site.latest_version}}.zip" class="btn btn-success btn-large" alt="Download the latest {{site.project_title}}" title="Download the lateset {{site.project_title}}"><i class="icon-white icon-download"></i> 下载 Polymer v{{site.latest_version}}</a></p>

<div class="centered"><iframe id="video" src="http://www.youtube.com/embed/videoseries?list=PLRAVCSU_HVYu-zlRaqArF8Ytwz1jlMOIM" frameborder="0" allowfullscreen></iframe>
</div>

## 速度入门

1. 下载以上链接的 `polymer-all` .zip包. 如果你想使用Git,参看 [获取源码](/getting-the-code.html).
2. **架个Web服务器** 到你应用的目录.
3. 引入 `polymer.min.js` (发布的时候绑定)到你的主页面:

        <script src="polymer.min.js"></script>

4. 细读 [入门指南](./getting-started.html).
5. 学习如何通过[Polymer core](/polymer.html)完成你的web 组件.
6. 试用[polymer-elements](https://github.com/Polymer/polymer-elements), [polymer-ui-elements](https://github.com/Polymer/polymer-ui-elements), 和 [toolkit-ui](https://github.com/Polymer/toolkit-ui) (*也是需要在Web服务器里运行)*.
7. 参与[邮件清单](./discuss.html)! 提问和反馈.

## {{site.project_title}} 是什么?
{: style="clear:both" }

{{site.project_title}} 包含两层含意:

- 一个包含有核心平台式功能的集合 ([Shadow DOM](/platform/shadow-dom.html),
[Custom Elements](/platform/custom-elements.html), [MDV](/platform/mdv.html)).
最开始, 这些核心功能可被一组polyfill开启支持. 由于浏览器开始原生支持这些新功能,polyfill平台层会随着时间的推移而缩小.
- 基于这些核心技术而构建的下一代Web框架称为**_{{site.project_title}}_**.

架构图如下:

<figure id="architecture-diagram">
  <!-- <img src="/images/architecture-diagram.svg" alt="Architecture Diagram" titld="Architecture Diagram"> -->
  <iframe src="/images/architecture-diagram.svg?{{'now' | date: "%Y%m%d"}}"></iframe>
  <figcaption>架构图</figcaption>
</figure>

## 指导准则

{{site.project_title}} 总体目标是管理起繁杂的Web应用构建. 我们的准则是:

**一切都是组件** — 封装是创建可扩展性, 可维护性的应用的关键. {{site.project_title}} 的所有资源都是组件, 甚至包括那些个不可见的. 要搭建一个应用, 开发者要创建新的组件, 或者使用 {{site.project_title}} 所提供的,然后将它们整合到一起. 专注于个别, 组件化的结构能使开发者对他们的应用进行"局部思考", 减少复杂度. 通过这种各个击破的手段, 应用可以同时变得简单化的也可以任意复杂化.

**极端实用主义** — 开发者应该写出**最小化**的代码量来完成他们的应用. 任何复杂都应该重新拆分成一个组件,交由{{site.project_title}}管理, 或追加到浏览器平台自身上. {{site.project_title}} 提供简洁的语法在无需削减功能的情况下随时可以避免滥用.

**高度灵活** —  随你使用最多还是最少的框架. 一个应用仅加载`polymer-all/platform/platform.js` 而从polyfill中受益, 或者追加 `polymer-all/polymer/polymer.js` 来增强Web组件的扩展性. 我们为把这类elements称为
 ["{{site.project_title}} elements"](/polymer.html).

