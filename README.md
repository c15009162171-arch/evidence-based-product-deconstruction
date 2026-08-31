# 证据驱动产品拆解

基于截图、可访问网站或原始代码等一手证据，从用户层、技术层、模型层和数据层拆解产品，并交付一份可离线打开的 HTML 报告。

没有可访问的一手证据时，不要启动实质拆解；只输出证据就绪度与缺口。

## 做什么

- 先判断产品类型，再按证据门槛决定完整拆解还是局部拆解
- 用统一编号记录证据：`E01` 起连续递增，冲突用 `C01`
- 每条结论标明【页面/代码事实】【合理推断】【尚未确认】【产品建议】
- 复制 `assets/report-template.html` 填入当前产品内容，输出自包含 HTML

报告必须写当前产品的真实名称、流程、字段和结论。不要套用其他产品，也不要把某次拆解写回本仓库的 skill 文件。

## 安装

把本目录放到对应运行时的 skills 路径，目录名保持 `evidence-based-product-deconstruction`：

| 运行时 | 个人技能目录 |
|---|---|
| OpenAI Codex | `~/.codex/skills/` |
| Cursor | `~/.cursor/skills/` |
| Claude Code | `~/.claude/skills/` |

```bash
git clone https://github.com/Zkeery/evidence-based-product-deconstruction.git \
  ~/.codex/skills/evidence-based-product-deconstruction
```

Cursor 或 Claude Code 把目标路径换成上表对应目录即可。项目级安装则放到仓库内的 `.agents/skills/`、`.cursor/skills/` 或 `.claude/skills/`。

Codex 也可显式调用：`$evidence-based-product-deconstruction`。

## 使用

向 Agent 提供至少一种一手证据：

- 覆盖目标流程的连续截图或视频关键帧
- 可只读检查的网站或应用
- 能支撑问题的原始代码、接口或数据结构
- 真实运行日志、导出记录或错误记录

只有首页、宣传页、转述或不可访问链接时，Agent 应停止实质拆解并列出最小补证。

默认只读。发送消息、生成、发布、删除、购买或覆盖资产需要你明确授权。不要让 Agent 读取或输出 Cookie、Token、密码或其他凭证。

## 报告

交付文件默认名为 `{产品短名}-deconstruction.html`。章节以 `references/html-output-spec.md` 为准，共 14 章。图形使用模板里的 HTML/CSS/SVG，不引用外部 CDN，也不使用 Mermaid 代码块。截图默认嵌入为 `data:` URI。

## 目录

```
SKILL.md                      主指令
agents/openai.yaml            Codex / ChatGPT 界面元数据
assets/report-template.html   离线 HTML 报告模板
references/product-archetypes.md
references/evidence-method.md
references/html-output-spec.md
```
