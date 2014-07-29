---
layout: default-zh
title: 常见问题
---

{% include zh/alpha.html %}

*没找到你问题的答案? 请到[邮件清单](/discuss.html)提问!*

## {{site.project_title}} 

#### 为什么我要关注这个项目? {#why}

{{site.project_title}} 是一个全新的Web库, 主打现代Web平台, 非常有助于基于Web组件来构建Web应用.

与之前的其他框架不同的是,  {{site.project_title}} 通过鼓励尽可能多的用上[custom element](/platform/custom-elements.html) 来以最大限度的拥抱HTML. 其中包含一小部分针对这些新兴Web标准(Custom Elements,  Shadow DOM,  etc.)的独立polyfill会随着时间的推移,  逐渐减少直至浏览器提供商把原生API完全实现而消失.

{{site.project_title}} 虽还处于它的萌芽期,  但我们已为它的潜力而且激动不已! 

#### 这些将彻底改变整个互联网还能解决我所有的烦恼的魔法般灵光的组件都在哪? {#uicomponents}

这目前只是我们共识到一个闪光点, 但我们已经打下了稳固和科学的基础, 并且我们正为此疯狂的工作直至将我们的雄心壮志变成现实, 敬请期待吧!

#### 那, 这些组件都还没有.是否其他{{site.project_title}}的作品都完善了? {#readiness}

我们可没这么想, 但如果你甘当小白鼠你可要试试.都跑跑demo, 耍耍toolkit.最重要的是, 要多加入邮件清单给我们反馈!

#### 我不喜欢你们的{组件 | toolkit语法 | 外观}! {#dislike}

<!-- 
<figure id="architecture-diagram" style="float:right">
  <iframe src="/images/architecture-diagram.svg?{{'now' | date: "%Y%m%d"}}" style="width:150px;"></iframe>
  <figcaption>Architectural Diagram</figcaption>
</figure> -->

没关系.我们已将{{site.project_title}}设计得层次很简洁分明所以你可以仅使用你看得上的部分. 你可以使用我们提供的全部, 单个polyfill,  或者两者之间的任意部分.全由你作主.
<!-- {: style="clear:both"} -->

#### 如果我想使用{{site.project_title}}我必须得使用Sandbox工具吗? {#sandbox}

不, Sandbox只是一个能使你玩起组件来更加容易且对 {{site.project_title}}更加有感觉的demo.它不会试图变成任何形式的开发工具的. 

#### {{site.project_title}} 都支持哪些浏览器? {#browsersupport}

{{site.project_title}} 目标是支持 [evergreen browsers](http://www.yetihq.com/blog/evergreen-web-browser/). 毕竟, 我们是在模拟未来, 正如某人所说,  "如果你总盯着后视镜那你前方肯定有麻烦了". 在实践过程中, 这意味着我们支持以下浏览器的最新版, Chrome,  Safari,  Internet Explorer,  和 Firefox. 注意, 这是比其他框架所支持的浏览器还要少一些的.例如,  {{site.project_title}} 只支持IE10+. {{site.project_title}} 有些部分如果不过多考虑扩展性可能会支持更多浏览器--如果发现未支持的浏览器上有bug, 请报给我们.绝大多数东西无需过多工作也能支持IE9;哪部分有bug请随意报上来.IE8由于其对DOM支持不足因此没法兼容. 

更多资料请参考我们的 [浏览器兼容性](compatibility.html).

#### 其他浏览器什么时候能原生支持这些API? {#nativesupport}

我们的[架构图](/images/architecture-diagram.svg)里基础层是基于最新的Web标准的.任何层的需求度会随着浏览器原生支持度的增加而逐渐减少直至最终消失.很难说什么时候每个浏览器都原生支持这些特性, 但开发者的呼声越高被支持就越快. 

#### 移动这块你们是什么打算? {#onmobile}

我们的核心目标之一就是让{{site.project_title}}在移动设备的支持上得到一等公民般的待遇.例如, 目前{{site.project_title}}的绝大部分支持Chrome for Android 和 Mobile Safari.我们也在研究响应式的组件能在桌面浏览器, 平板和手机上自适应.

#### 为什么与x-tags扯上关系? {#xtags}

[x-tags](http://x-tags.org/) 是Mozilla正在开发的一个很酷的项目,  它也不直接隶属于{{site.project_title}}. 不过, {{site.project_title}} 和 x-tags 两者者基于最新的Custom Elements标准, 这意味着两者的组件默认即是相互兼容的.Google 和 Mozilla 都为Custom Element 规范提供polyfill. X-Tag两者都支持, 因此你能在{{site.project_title}} 的组件上沿用X-Tag.我们正积极的为它们和组件集合的最大兼容性而作努力.

#### {{site.project_title}} 与Twitter的 Bootstrap 或者 Adobe的 Topcoat究竟区别在哪? {#uiframeworks}

Bootstrap 和 Topcoat 都是很强大的 CSS/UI 库. 我们对{{site.project_title}}的定位不同. 我们最终打算为惊艳四座的UI 组件构建一系列的标准, {{site.project_title}}是完全系统而整体的, 有助于有兴趣的开发者基于Web 组件技术打造Web 应用. {{site.project_title}}也提供支持扩展的更多API([MDV](/platform/mdv.html),  templates,  and data-binding) 以满足当今的Web应用.

#### 不对, 以前的Toolkitchen呢? {#toolkitchen}

Toolkitchen是我们给这个项目取的第一个名称. 我们对它无爱了, 这就更名为了{{site.project_title}}.

#### Google与这个项目是个什么关系? {#google}

我们仅是认为Web 组件是出类拔萃的几个家伙--我们大部分人在Google工作.我们对社区如此活跃的参与感到激动不已也早有准备, 非常期待你也加入!

#### {Angular JS | Closure | Google Web Toolkit}与这个项目有关联吗? {#frameworks}

都没有.

#### polymer.dart为何被{{site.project_title}}扯上了? {#dart}

polymer.dart 是Dart团队为 {{site.project_title}} 创建而维护的一部分.Dart团队正在与{{site.project_title}}团队合作确保polymer.dart组件和polyfill都完全与{{site.project_title}}兼容. 

#### 我看到一堆XHR连接请求.干嘛用的? {#xhrrequests}

polyfill目前所受到的一个限制是{{site.project_title}}带耦合性的通过XHR模拟HTML Import. 我们正在测试改进打包系统和生成步骤来减少网络请求.当此API被浏览器原生支持, 一切还会照常工作的. 资源将会被正常的加载, 也会得益于并行加载和缓存策略等. 

#### 性能不是很理想, 你们都不关心吗? {#performancestuff}

我们真心的想使整个Web平台都得到60fps的流畅度.这么说吧,  我们还没有按基准对所有polyfill进行过测试--毕竟, 我们还处于初级阶段! 如果你有兴趣帮助我们进行统计,  [请随时告诉我们](/discuss.html).

别忘了我们的库是会随着时间而流逝的! {{site.project_title}}也会随着浏览器逐渐的以原生实现而变得好,  更强, 更快.

#### {{site.project_title}}在内容安全策略(Content Security Policy, CSP)下还能用吗? {#csp}

在某些情况下,  {{site.project_title}}毫无疑问在[CSP](http://www.html5rocks.com/tutorials/security/content-security-policy/)下是废掉的.这是因为[HTML Imports](/platform/html-imports.html)这个polyfill是通过 XHR 来实现的. HTML Import的原生支持是必需的(参看 Blink的 [crbug.com/240592](http://crbug.com/240592)).这此之前, 我们会优先考虑软件解决的方案.

#### 我怎样才能参与贡献? {#contributing}

我们很乐意听到你的评论和建议. [报bug](https://github.com/polymer/polymer/issues/new) 或者转到[邮件清单](discuss.html) 打声招呼"hi"--我们不会咬你的! 如果你想
贡献代码, 参看[贡献者的指南](https://github.com/polymer/polymer/blob/master/CONTRIBUTING.md).

#### 哪里才是报bug的最佳地方? {#filebugs}

我们有很多不同的demo, 平台, 类库的仓库. 如果你明确知道问题出在哪, 请有针对的就地报bug, 要不然就在项目通用的地方报[{{site.project_title}}](https://github.com/polymer/polymer/issues/new).

#### stable 和 master 分支之间的区别是什么? {#branches}

参看 [打分支策略](/branching-strategy.html).

#### 我怎样使用一个MDV模型来复用一个 `<option>` 或者 `<tr>`? {#mdv-option-tr}

`<option>` 和 `<tr>` 元素当他们的子节点是
`<select>` 和 `<table>`时各自有特殊的含意. 针对这两个特殊的元素, 使用
`template` 的特性来复用:

    <template bind>
      <select>
        {%raw%}<option template repeat="{{options}}">{{}}</option>{%endraw%}
      </select>
    </template>
    <script>
      var t = document.querySelector('template').model = {
        options: ['One',  'Two',  'Three']
      };
    </script>

#### 我怎样管理JavaScript的依赖关系才能防止XX库被上1000次的复用? {#loadlibs}

没有一个办法能保证是个万全之策的. 当然,  如果你有一个组件库依赖某个库, 它们是可以通过import一个
"library.html" 来加载这些库的. [HTML Imports](/platform/html-imports.html)
会根据它的完整路径把文件导入.

如果多类库之间需要共享依赖关系, 他们只能约定好一套机制.如何功能探测, 或为CDN上的一个'jauery.html'约定固定的位置等.

## Web 组件

#### 我如何将一堆Custom Elements打包到一起? {#packaging}

自定义一个构建步骤将一切合并成一个文件, 
然后通过 [HTML Imports](/platform/html-imports.html) (`<link ref="import">`) 将
文件引入你的应用里. 

类似的, 你可以再写个构建步骤将任何在你的应用里Custom Elements内联起来.此思路是我们实验过一个我们称为[Vulcanizer](https://github.com/Polymer/labs/tree/master/vulcanize)的工具而得来的.

#### 搜索引擎蜘蛛爬虫能理解这些自定义的元素吗? SEO效果如何? {#seo}

它们不理解. 不过,  搜索引擎已经处理过基于AJAX的重量级应用了.远离JS变得语义化对SEO是好事也会使事情往好的方向发展.

#### 是否有个组件的注册表我能研究研究? {#registry}

还没有, 但我们认识这是个好想法.

#### 当我在元素的定义里引入外链的CSS样式或者通过`<link rel="import">`使用外链CSS会报错 . {#externalsheets}

不幸的是,  这是HTML Import规范的一个限制让polyfill给撞上了. polyfill 通过 XHR 抓取定义在`<polymer-element>` 里的资源.外链资源如果没有启用[CORs-enabled](http://www.html5rocks.com/tutorials/cors/)是会加载失败的.

针对跨域或者没有开启CORs-enabled,  你可以在`<style>`使用 `@import`:

    <polymer-element name="x-blink">
    <style>
      @import url(http://example.com/awesome.css);
    </style>
    <template>...</template>
    </polymer-element>

*注意*: 如果你的样式文件 **是** 开启CORs-enabled 或者与你的应用同域, 那不使用`@import`是没有问题的. 例如:

    <polymer-element ...>
      <link rel="stylesheet" href="frameworkstyles.css">
      <template>...</template>
      ...
    </polymer-element>

#### 在我的Custom Elements里我如何使用web fonts 或 CSS Animations? {#fontsanimations}

根据规范,  包含 @ at-rules (包括 CSS `@keyframe` 和 `@font-face`) [不能定义](http://lists.w3.org/Archives/Public/public-whatwg-archive/2013Jan/0251.html) 在 `<style scoped>`里. 因此,  你需要在ShadowDOM外定义这些变量 (例如. 在 `<template>`外边) 使用 `<style polymer-scope="global">`. 这样之后,  你就能在你的Shadow DOM里使用 animation/font 了:

    <polymer-element name="x-blink">
      <!-- CSS Animation 要定义在style作用域外 -->
      <style polymer-scope="global">
        @import url(http://fonts.googleapis.com/css?family=Quicksand);
        @-webkit-keyframes blink {
          to { opacity: 0; }
         }
      </style>
      <template>
        <style>
          @host {
            x-blink { -webkit-animation: blink 1s cubic-bezier(1.0, 0, 0, 1.0) inifnite 1s; }
          }
        </style>
        ...
      </template>
    </polymer-element>

#### 为什么我的元素`.clientWidth/clientHeight`属性值都为0 ? {#clientDimenstions}

默认情况下, Custom Elements是 `display: inline`.解决这个的办法是通过`@host`规则给你的元素应用上默认的`display: block`样式.

    <polymer-element name="my-element">
      <template>
        <style>
          @host { * { display: block; } }
        </style>
        ...
      </template>
      ...
    </polymer-element>
    <script>
    window.addEventListener('WebComponentsReady',  function(e) {
      var element = document.querySelector('my-element');
      // element.clientWidth/clientHeight won't be 0.
    });
    </script>

#### 元素能`extend`(扩展自)多个元素或者有多重继承吗(如.`<polymer-element name="my-element" extends="foo bar">`? {#multipleextends}

没有. 但是 {{site.project_title}} 将来可能会提供一个mixins的语法.

#### 在一个 `<content>`里我如何访问DOM? {#accessContentDOM}

对于一个`<content>`来说,  你可以通过迭代`content.getDistributedNodes()`
来取得被分配在嵌入点上的节点列表.

别忘了你是可以正常取到元素的子节点的DOM的
(例如. `this.children`等). 此方式手段区别在于这是整个被*潜在*分配节点的集合;而不是实际被分配的.

#### 我能使用`constructor` 属性却不污染全局命名空间吗? {#constructorattr}

根据设计,  `constructor` 以constructor为命名空间的方式注册到了`window`下. 如果你不想这样, 这里有两个选择:

1. 不使用`constructor` 属性, 而使用 `document.createElement()`.
2. 使用 `document.register()` 并再包装constructor它是在一个命名空间里返回的.

---

*特别感谢GitHub 用户 md_5 慷慨的贡献了{{site.project_title}} 原名.*


