# PRD Writing Skill

一个面向中文产品经理的 Agent Skill，用于把**已经基本确认的需求、评审结论、原型或产品图**整理为结构清晰、可评审、可验收的 PRD。

它会根据需求复杂度选择最接近的参考案例，并严格区分“已确认事实”和“待确认事项”：不为追求文档完整而补造业务规则。

## 能力与适用范围

适合：

- 将需求讨论、评审结论整理成正式 PRD；
- 基于原型、产品图或现有文档补充产品逻辑；
- 完善简单、中等或复杂需求的状态、权限、异常和验收口径；
- 检查 PRD 中的逻辑冲突、遗漏与未经确认的规则。

不适合：

- 在缺少依据时替用户决定业务规则；
- 将推测、行业惯例或示例内容写成已确认需求；
- 代替产品评审、技术评估或最终业务决策。

## 输出结构

生成的 PRD 默认包含：

1. 变更记录；
2. 需求背景；
3. 产品需求；
4. 产品方案：固定使用“模块｜图｜产品逻辑描述”三列表格；
5. 验收要点。

未确认的信息会标记为“待确认”。具体规则以 [`SKILL.md`](SKILL.md) 为准。

## 安装与使用

安装前建议先阅读仓库内容。请保留整个目录结构，不要只复制 `SKILL.md`，否则参考案例和示例图片无法正常使用。

### Codex

安装到当前用户：

```bash
git clone https://github.com/JessieSun-vibe/prd-writing.git ~/.codex/skills/prd-writing
```

也可以安装到单个项目：

```bash
git clone https://github.com/JessieSun-vibe/prd-writing.git .codex/skills/prd-writing
```

重新开始一个 Codex 会话后，可直接描述需求；需要明确指定时，可以说：

```text
请使用 prd-writing skill，把下面已经确认的方案整理成 PRD；存疑内容标注为待确认。
```

参考：[OpenAI Agent Skills 说明](https://developers.openai.com/api/docs/guides/tools-skills)。

### Claude Code

安装到当前用户：

```bash
git clone https://github.com/JessieSun-vibe/prd-writing.git ~/.claude/skills/prd-writing
```

也可以安装到单个项目：

```bash
git clone https://github.com/JessieSun-vibe/prd-writing.git .claude/skills/prd-writing
```

重新开始一个 Claude Code 会话后，可让 Claude 自动匹配该 Skill，或输入 `/prd-writing` 主动调用。

参考：[Claude Code Skills 说明](https://code.claude.com/docs/en/skills)。

### 普通 ChatGPT 对话

把本仓库链接粘贴到普通 ChatGPT 对话中，最多代表让 ChatGPT 在**当前对话中尝试读取并参考**公开内容；这不等于安装 Skill，也不会自动在后续对话中持续生效。实际能否读取，还取决于当前产品是否支持联网访问该链接。

本仓库目前是独立的 Skill 目录，未打包为可从 ChatGPT Plugin 目录安装的插件。如果只在普通 ChatGPT 中使用，建议同时说明目标，并要求先阅读 `SKILL.md` 与相关参考案例。

示例：

```text
请阅读这个 PRD Writing Skill，并仅把它作为本次对话的写作规范：
https://github.com/JessieSun-vibe/prd-writing

下面是已经确认的需求材料。请先指出冲突和待确认项；我确认后再生成 PRD。
```

## 示例指令

```text
请使用 prd-writing skill，把以下评审结论整理成正式 PRD。不要补造规则，缺失信息标注为待确认。
```

```text
先使用 prd-writing skill 检查这份方案的状态、权限、异常和验收口径；现在只分析，不修改原文。
```

```text
结合这组原型图和已确认结论生成 PRD。图片放在产品方案表格的“图”列，每个模块只占一行。
```

## 目录结构

```text
prd-writing/
├── SKILL.md              # Skill 入口与核心规则
├── agents/
│   └── openai.yaml       # Codex 展示信息与默认提示
├── references/           # 简单、中等、复杂需求的参考案例
├── assets/               # 参考案例使用的虚构界面图片
├── .gitignore
└── README.md
```

## 贡献

欢迎通过 Issue 提交问题或建议，也欢迎发起 Pull Request。贡献时请遵守以下原则：

- 不改变“只使用已确认材料、存疑内容标注待确认”的核心边界；
- 公开案例不得包含真实公司、项目、用户或内部业务数据；
- 新增参考案例时，需同步检查文档链接、图片路径和目录结构；
- 不要把某个项目的临时做法扩展为所有 PRD 的通用规则。

## 许可证

本仓库暂未提供开源许可证，授权范围仍待仓库维护者确定。在许可证明确前，请勿默认复制、修改、分发或商用本仓库内容；如需使用，请先联系仓库维护者取得授权。
