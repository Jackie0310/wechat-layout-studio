# 实际验证记录 / Verification

日期：2026-11-04。环境：Windows、本次会话内置浏览器；静态服务绑定 127.0.0.1。只使用合成文字，不提供真实用户效果数据。

## 已执行

- 原包和候选包分别运行 `node --check assets/editor/wechat-editor.js`，退出码均为 0。
- 分别打开原包和候选包的原有 `assets/editor/wechat-editor-tests.html`，两次页面均显示 PASS，A–G 全部通过：普通新闻结构 4 块、5 个二级标题实例、8 个时间轴节点、长标题风险提示、短文保持 1 块、长文采用 2 种正文模块、唯一引用位于第 2 块。
- 候选包 `examples/` 输入合成 Markdown，通过“一键识别并排版”得到 4 个块（导语、章节标题、正文、结语）、01 章节序号及“兼容检查通过”；页面明确显示“本地规则校对／未调用 API”。
- 在上述页面点击“+ 导入模板”，弹窗正常显示富文本、HTML 文件、HTML 源码三个入口。未以此声称完整测试所有模板采集分支。
- 对照原包文件：Skill、agent YAML、结构规则、排版规则、CSS、原有验收 HTML 保持字节一致；JS 差异仅两处字符串；接入说明和来源说明更新；限制分发的旧许可没有与 MIT 同时放入候选仓库。
- 对候选文本进行常见密钥格式、私钥头和敏感文件名扫描，并复查命中项；未发现实际凭据。`sk-…` 是原 UI 占位符。没有打包 .env、浏览器存储、真实用户文章、图片、字体或第三方依赖库。
- 核对本地 Markdown 文档链接、示例资产路径与原有验收页脚本路径。

## 未执行或无法证明

- 未取得此前清理版，无法完成两个 ZIP 的逐文件差异比较。
- 未独立验证全部代码、模板及文案的创作权链；原包带商业限制，MIT 重新许可需要权利人确认。
- 未调用外部 AI、未测试代理服务（包内没有）、未测试模型服务可用性。
- 未在微信公众号实际粘贴发布、未验证剪贴板在各浏览器的兼容性、未覆盖移动端或微信暗色模式矩阵。
- 未执行完整安全审计；HTML 基础过滤不是安全隔离。未声称所有导入模板均安全或合规。
- 本地验证结果不包含 GitHub 发布验证；实际提交、tag 与 Release 状态以 GitHub 页面为准。

Both the original and candidate passed syntax checks and the seven existing browser acceptance checks. The minimal host was exercised with synthetic Markdown and the template modal opened. External AI, real WeChat paste/publishing, exhaustive security, authorship clearance and comparison with the unavailable earlier cleaned ZIP were not verified.
