---
name: generate-prd-mermaid
description: 把模糊项目想法、业务需求、功能请求或立项信息整理为结构化需求文档、产品设计方案和 Mermaid 图表。用于生成 PRD、需求分析、功能拆解、页面结构、业务流程、状态流转、用户旅程或系统交互图；也适用于信息不完整时先输出带假设与待确认项的可评审初稿。
---

# Generate Prd Mermaid

把一句话想法、零散业务描述或半成型需求，整理成可继续评审、拆解和汇报的文档，并同步生成 Mermaid 图表。

## 执行流程

1. 先读取 `references/input-schema.md`，把输入归一化为项目名称、类型、背景、用户、问题、目标、范围和约束。
2. 输入不完整时，先按 `references/input-schema.md` 输出 `输入缺口提醒`，说明缺什么、影响什么、默认怎么处理；只有缺口会改变核心流程、角色边界或合规判断时才优先追问。
3. 再读取 `references/output-schema.md`，按需求复杂度选择 `精简版` 或 `完整版`。
4. 把 `问题`、`目标`、`范围` 与 `方案` 分开写，避免把解决方案直接伪装成需求。
5. 先读取 `/Users/allen/Downloads/project/项目/OpenB8AutoBuild/.codex/skills/mermaid-diagrams/SKILL.md`，再按图类型读取其中对应的 `references/*.md`；`references/mermaid-guidelines.md` 只负责把产品设计场景映射到该技能的规则文件。
6. 输出前读取 `references/quality-checklist.md`，检查正文、图表、假设和异常场景是否闭合。

## 输出规则

- 默认使用中文输出，保留必要英文产品术语。
- 开头先给 `需求摘要`，让用户快速判断方向是否正确。
- 输入缺失时，先给 `输入缺口提醒`，再继续正文；不要静默补全。
- 小需求至少输出 1 个 Mermaid 图；中等及以上复杂度优先输出 2 到 3 个图。
- 每个 Mermaid 图都放在独立的 `mermaid` 代码块中，一个代码块只放一个图。
- 文档必须显式区分 `本期范围`、`非本期范围`、`MVP 建议`、`待确认项`。
- 输入缺失时明确标注 `基于默认假设生成，请人工确认`，并把默认处理写清楚。
- 对已有系统迭代，标明 `新增`、`修改`、`保持不变`。
- 避免空泛措辞，例如“提升体验”“赋能业务”；改写成可执行目标、规则或验收条件。

## 图表选择

- 业务流程、页面流、信息架构：优先 `flowchart TD` 或 `flowchart LR`
- 用户与系统、多角色协作、接口交互：优先 `sequenceDiagram`
- 状态迁移、审批流、生命周期：优先 `stateDiagram-v2`
- 用户分阶段体验、痛点梳理：优先 `journey`

## 资源

- `references/input-schema.md`：输入字段、缺省策略、信息不足处理
- `references/prompt-template.md`：直接可复用的提示词模板
- `references/output-schema.md`：交付结构、章节要求、输出深度选择
- `references/mermaid-guidelines.md`：产品设计场景到 `.codex/skills/mermaid-diagrams` 的规则映射
- `references/quality-checklist.md`：正文与 Mermaid 自检清单

仅在用户明确要求正式 PRD、需求文档、产品方案或 Mermaid 图时展开完整版；否则优先输出可评审的第一版，并把缺口留给 `待确认项`。
