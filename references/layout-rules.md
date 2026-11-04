# 排版与公众号兼容规则

## 模块映射

支持 HERO、TITLE_H1、TITLE_H2、TITLE_H3、PARAGRAPH、DIVIDER、LEAD、QUOTE、HIGHLIGHT、NUMBER、DATA、IMAGE、IMAGE_CAPTION、PERSON、TIMELINE、STEP、CONCLUSION、ENDING 和 FOOTER。

模板是组件库，不是单纯换色。模块保留原 DOM 和内联样式，只修改已授权 Slot。HERO、ENDING、FOOTER 默认固定并不可复制；正文、标题、引用等可按约束克隆和移动。

## 视觉层级

- 锚点层：全文不超过五处，使用深色底浅色字或主色加粗。
- 标记层：每段择取少量关键词变色、加粗或半高亮。
- 容器层：人物卡、金句、数据和中心观点使用独立卡片。
- 同一文章只使用一套主题组件；允许少量深色主题卡制造区分，但不能让所有卡片都同样突出。

## 配色

文字颜色必须显式写在最终节点上。深色或渐变背景中的文字同时设置 `color` 和 `-webkit-text-fill-color`，避免复制到公众号后由白色变黑色。正文保持高对比可读，辅助文字不得过浅。

## 安全边界

移除 script、style、link、iframe、object、embed、form、事件属性和 javascript URL。避免 position fixed/absolute/sticky、Grid、float、CSS 变量及外部字体。图片只接受 http、https、data:image 或 blob。
