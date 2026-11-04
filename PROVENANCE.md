# 来源、素材与许可核查 / Provenance

## 可确认的输入

- 本次实际读取的是本机同名原包 `wechat-layout-studio-workbuddy-skill-v1.0.1.zip`，10 个文件，SHA-256：`a132ce889f7e20235879d5109c6c11cb0d36d4cf12678ba8d784a15e08d578e1`。
- 无法读取前一聊天 `/mnt/data` 附件；此前清理版未取回，未完成两个压缩包的逐文件对比。本次发布内容不是此前清理版的已验证副本。
- 原包 `LICENSE.txt` 署名“Copyright (c) 2026 上古中天. All rights reserved.”，限制公开分发、转售及再许可。原件完整保留于本次本地审查资料，不随公开仓库分发。
- 按维护者指示采用 MIT `LICENSE`，署名 Jackie0310。维护者于 2026-11-04 在审阅文件范围和 MIT 权限后，明确确认拥有重新许可权并授权公开发布。此确认不是独立的第三方权利证明；删除商业声明本身也不构成第三方授权证据。

## 包内代码与素材

- 原包只含 Markdown、YAML、HTML、JavaScript、CSS；未打包图片、字体、第三方库、客户文件或浏览器存储。没有 package.json、requirements.txt、锁文件或安装脚本。
- JS/CSS 使用浏览器原生能力。CSS 未发现 `@import`、`url(...)`；字体是系统字体栈，没有字体文件。预设以代码内 HTML/CSS 和颜色值组成。
- 原包来源文档及代码中的 `design: original`、`commercial-clean-1.0` 是原作者声明／历史标识，本次审查未独立证明完整创作链，不将其当作第三方权利已清除的结论。
- 未发现已打包的第三方依赖，不等于已证明所有代码、文案和模板均可重新许可。若后续发现上游代码，必须核实其许可并保留应有署名；不可只移除项目名称和链接。
- 原代码的验收测试含合成文字；示例新闻中的内部试用数字缺乏证据，已替换为明确标注的演示文字。没有将示例当作真实用户或产品效果资料。

## 本次改动范围

保留 `SKILL.md`、agent YAML、结构规则、排版规则、CSS、验收页原样。JS 只更改内置示例文字和缺失启动脚本的错误提示，保留原核心流程、API 路由及历史版本字段。接入文档补充实际需要的弹窗容器与 API 限制。新增首发文档和最小宿主示例。实际检查见 `docs/VERIFICATION.md`。

## 外部输入与名称

用户导入的文章、模板、图片、字体、肖像、标识与远程资源，其权利需单独核实，不因本项目 MIT 许可而获得授权。不得预装无权分发的模板或用户数据。

“微信公众号”“WorkBuddy”和接口名称只用于说明用途或兼容背景，不表示获得相关平台授权、合作或背书。

## Publication authorization / 发布授权记录

1. 维护者确认有权以 Jackie0310 署名，并将本次 17 个文件按 MIT 公开。第三方内容如有仍应提供相应许可与署名。
2. 已展示候选文件清单、实际修改及 MIT 权限范围，并取得最终公开提交确认。
3. 已核对 GitHub 所有者 Jackie0310，发布目标为 Public 仓库 `Jackie0310/wechat-layout-studio`。

This is a bounded engineering review, not proof of independent authorship or complete rights clearance. The earlier cleaned archive was unavailable. The original restricted redistribution; the maintainer confirmed the right to relicense and authorized this MIT publication on 2026-11-04. Imported materials and trademarks retain their own rights.
