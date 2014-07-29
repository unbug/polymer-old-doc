---
layout: default-zh
title: 运行时配置
---

## 切换配置

{{site.project_title}} 支持运行时配置,可在加载`platform.js`的`<script>`标签上作为属性一样设置, 或者通过URL传参.

### 调试

带条件的加载一个debug版的 `platform.js`.

**例子**

    <script src="platform/platform.js" debug></script>

或,等效于:

    http://localhost/polymer/toolkit-ui/getting_started/?debug

默认是加载了(`platform.min.js`).使用 `debug` 会加载 `platform.debug.js`.

### 日志

控制控制台的日志输出.

**例子**

    <script src="platform/platform.js" log="bind,ready"></script>

或,等效于:

    http://localhost/polymer/toolkit-ui/getting_started/?log=bind,ready

可用值:

<table class="table">
  <tr>
    <th>值</th><th>描述</th>
  </tr>
  <tr>
    <td>bind</td><td>数据绑定引擎执行的操作.</td>
  </tr>
  <tr>
    <td>data</td><td>来自所绑定的数据运行时变换的结果</td>
  </tr>
  <tr>
    <td>watch</td><td>数据变更通知</td>
  </tr>
  <tr>
    <td>events</td><td>自定义绑定的事件和事件的传播</td>
  </tr>
  <tr>
    <td>ready</td><td>Custom element 状态就绪时</td>
  </tr>
</table>

### shadow

选择Shadow DOM 的实现方式: `native` 给原生支持的浏览器 或者 `polyfill`
给非原生支持的浏览器.

**例子**

    <script src="platform/platform.js" debug shadow="polyfill"></script>

或,等效于:

    http://localhost/polymer/toolkit-ui/getting_started/?debug&shadow=polyfill


可用的属性值:

<table class="table">
  <tr>
    <th>值</th><th>描述</th>
  </tr>
  <tr>
    <td>native</td><td>如果浏览器原生支持用原生实现. 默认为支持Shadow DOM的浏览器开启.</td>
  </tr>
  <tr>
    <td>polyfill</td><td>强制加载 <code>platform.poly.min.js</code> 使用Shadow DOM polyfill. 默认为不原生支持 Shadow DOM 的浏览器开启.</td>
  </tr>
</table>

<!--
### eval

当值为 `true` 时, 组件脚本将使用`eval`执行而不是script标签注入的方式. 默认为 `false`.

例子:

    <script src="platform/platform.js" eval="true"></script>

  或

    http://localhost/polymer/toolkit-ui/getting_started/?eval

-->