# Mermaid 规则映射

本 skill 的 Mermaid 语法与图表能力，统一以以下目录为准：

- `/Users/allen/Downloads/project/项目/OpenB8AutoBuild/.codex/skills/mermaid-diagrams/SKILL.md`
- `/Users/allen/Downloads/project/项目/OpenB8AutoBuild/.codex/skills/mermaid-diagrams/references/`

不要再以本文件自带示例作为主规则源；本文件只负责告诉你在产品设计场景下应读取哪个 Mermaid 参考文件。

## 读取顺序

1. 先读取 `.codex/skills/mermaid-diagrams/SKILL.md`
2. 再按图类型读取对应 reference 文件
3. 仅在外部技能没有覆盖该图型时，回退到 Mermaid 基础语法，并保持最小可渲染写法

## 产品设计场景到规则文件的映射

- `业务流程`、`页面流`、`功能结构`、`审批流`
  - 读取 `.codex/skills/mermaid-diagrams/references/flowcharts.md`
- `多角色协作`、`前后端交互`、`接口时序`
  - 读取 `.codex/skills/mermaid-diagrams/references/sequence-diagrams.md`
- `数据对象`、`表结构`、`核心实体关系`
  - 读取 `.codex/skills/mermaid-diagrams/references/erd-diagrams.md`
- `系统上下文`、`容器边界`、`组件级架构`
  - 读取 `.codex/skills/mermaid-diagrams/references/c4-diagrams.md`
- `主题`、`样式`、`布局`、`look`
  - 读取 `.codex/skills/mermaid-diagrams/references/advanced-features.md`

## 本 skill 的补充约束

- 默认优先使用 `flowchart TD`、`flowchart LR`、`sequenceDiagram`
- 只有在用户明确需要数据建模或架构视图时，才输出 `erDiagram` 或 `C4*`
- `stateDiagram-v2` 和 `journey` 若需要使用，保持基础语法，不引入复杂样式
- 图中术语必须与正文一致，不能一套中文一套英文概念
- 每个代码块只放一个 Mermaid 图
- 复杂需求拆成多张图，不把整份 PRD 塞进一张图

## 出图前自检

- 是否先读了 `.codex/skills/mermaid-diagrams/SKILL.md`
- 是否读了与当前图型匹配的 reference 文件
- 图型是否服务于当前需求，而不是为了“多画一张图”
- 节点、关系、消息、实体名称是否与正文一一对应
- Mermaid 代码是否保持可直接渲染
