# WeChat Layout Studio

[English](README.en.md) | 中文

用于微信公众号文章结构整理与 HTML 排版的 Skill 和浏览器编辑组件。维护者：**Jackie0310**。项目沿用原包中文名称“公众号智排工作室”。

## 当前包含什么

- `SKILL.md`、agent 元数据及结构、排版规则，供支持此类 Skill 的助手参考。
- 原生 JavaScript / CSS 编辑组件：Markdown 与纯文本结构识别、六组预设主题、文章块编辑及排序、标题编号、模板采集、HTML 预览与导出。
- 富文本复制实现和 HTML 兼容性检查；真实粘贴效果需在微信公众号编辑器内复核。
- 可选的兼容聊天补全接口调用和本地规则回退。**本地规则排版不等于 AI 校对或联网事实核查**。

这不是完整后端服务，也不会替你登录或发布公众号文章。代码不会自行抓取输入 URL 的网页内容。标题、人物、结尾等识别结果需要人工确认。

## 本地试用（不需要 API Key）

环境：现代桌面浏览器；以下静态预览命令需要 Python 3。源码没有 npm / pip 运行依赖、依赖锁文件或构建步骤。

1. 下载并解压本仓库，进入仓库根目录。
2. 运行：

   ```sh
   python -m http.server 8000 --bind 127.0.0.1
   ```

3. 打开 `http://127.0.0.1:8000/examples/`，输入自己的文章，选择预设后点击“一键识别并排版”。不填写 API Key 时使用本地规则。
4. 编辑块内容，检查预览，再使用复制或 HTML 下载。示例宿主页面仅提供挂载所需的基础样式及弹窗容器。

Skill 的导入方式由宿主产品决定，本仓库不提供已经验证的 WorkBuddy 一键安装命令；`agents/openai.yaml` 的存在也不代表所有宿主均支持它。接入现有网页见 [integration.md](references/integration.md)。

## AI 接入限制与数据去向

- 代码在 **HTTP localhost / 127.0.0.1** 下向 `/api/chat-completions` 发送 `{endpoint, apiKey, payload}`。上面的 Python 静态服务器不实现这个接口；本仓库没有代理后端。
- 其他页面来源会尝试直接请求所配置 Endpoint；是否可用取决于服务接口、模型、跨域策略及浏览器环境。原有默认 Endpoint 和模型名仅是配置值，不代表服务可用承诺。实测未调用付费或外部 AI 接口。
- API 调用会把本阶段输入的文章／中间数据发送到配置的服务；localhost 代理路径还会接收 API Key。只使用自己信任的宿主和服务，不要把长期密钥放进公开网页。
- API Key 存于当前来源的 `sessionStorage`；文章、模板、设置和渲染结果存于 `localStorage`。它们不是加密存储，同源脚本可读取；调试导出包含文章与模板内容，公开前需要检查。
- 导入 HTML 的清理属于基础过滤，**不是面向不可信 HTML 的安全隔离**。不要导入不可信模板；远程图片、链接或样式可能向外部发起请求。只在可信本地环境或经过加固的宿主使用。

## 验证与已知边界

```sh
node --check assets/editor/wechat-editor.js
```

静态服务运行时，访问 `http://127.0.0.1:8000/assets/editor/wechat-editor-tests.html` 可运行原有 A–G 七项验收检查。具体已执行结果与覆盖范围见 [验证记录](docs/VERIFICATION.md)。这些检查不能证明微信所有客户端的显示一致，也不能证明模板来源授权或 AI 输出准确。

本次整理不改动排版核心；仅清理内置示例的未证实效果数字，并纠正指向包内不存在启动脚本的提示。未附带真实用户文章、客户数据、密钥、图片或字体文件；源码包含验收测试用的合成文字和明确标注的演示文字。

## 目录

```text
SKILL.md                    Skill 定义
agents/openai.yaml          agent 展示元数据
assets/editor/              JS / CSS 组件和原有验收页
references/                 结构、排版与宿主接入说明
examples/index.html         最小静态宿主示例
docs/VERIFICATION.md        实际验证记录与限制
PROVENANCE.md               来源、许可和素材核查范围
CONTRIBUTING.md             贡献指南
CHANGELOG.md                版本整理记录
LICENSE                    MIT 许可
```

## 许可与贡献

采用 [MIT License](LICENSE)，署名 `Copyright (c) 2026 Jackie0310`。维护者于 2026-11-04 确认有权重新许可并同意公开发布。原包带有限制分发的商业许可；该确认不等于独立证明全部创作权链，来源和核查范围见 [PROVENANCE.md](PROVENANCE.md)。导入内容及平台商标不因本项目许可而获得授权。

欢迎提交问题和改进建议，见 [CONTRIBUTING.md](CONTRIBUTING.md)。本项目不代表微信、腾讯或其他平台的官方产品或背书。
