# 接入已有工作台 / Integration

将 `assets/editor/wechat-editor.js` 和 `wechat-editor.css` 复制到目标项目目录。宿主需要编辑容器、`#modalHost` 弹窗容器及通用按钮／表单／弹窗样式；可参考仓库 `examples/index.html` 的最小宿主。

```html
<link rel="stylesheet" href="/features/wechat-editor/wechat-editor.css">
<div id="myWechatEditor"></div>
<div id="modalHost"></div>
<script src="/features/wechat-editor/wechat-editor.js"></script>
<script>
  WechatEditor.mount('#myWechatEditor', {
    storageKey: 'my-workbench-wechat-editor'
  });
</script>
```

页面销毁时调用 `WechatEditor.unmount()`；组件使用共享状态，不是多实例隔离组件。通过 `WechatEditor.getState()` 获取 Article AST、Template AST、Layout Plan 和渲染结果；`provenance()` 是历史来源声明，`palette()` 是基础配色。

HTTP localhost / 127.0.0.1 下 AI 请求发往 `/api/chat-completions`，请求体为 `{endpoint, apiKey, payload}`；本仓库没有实现该代理。静态服务器只能用于本地规则排版。其他来源直接请求 Endpoint，需要服务支持相应请求和跨域策略。不要为不可信调用者开放可任意转发的代理。

API Key 存于 sessionStorage；文章／模板／设置存于 localStorage。同源脚本可访问这些数据；使用受信任宿主。自定义模板需可信且有权使用，现有过滤不能当作安全隔离。平台内粘贴效果必须实际复核。详见中英文 README。

The host must provide the mount node, `#modalHost` and basic control/modal styles. State is shared, not isolated per mounted instance. No AI proxy backend is included; the local static preview supports local formatting. Use trusted hosts and authorized templates only.
