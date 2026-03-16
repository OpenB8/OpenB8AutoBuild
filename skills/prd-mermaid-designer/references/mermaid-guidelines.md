# Mermaid 使用规范

目标是稳定输出可以直接渲染的 Mermaid 图，而不是追求花哨语法。

## 选择规则

- `flowchart TD`：最适合业务流程、页面流、信息架构、审批流主干
- `flowchart LR`：适合模块关系、左右结构的信息流
- `sequenceDiagram`：适合角色与系统交互、接口调用、消息顺序
- `stateDiagram-v2`：适合状态流转、生命周期、任务状态管理
- `journey`：适合按阶段描述用户体验与痛点

## 通用约束

- 一个代码块只放一个 Mermaid 图。
- 节点 ID 使用 ASCII 字符，例如 `A1`、`user_submit`、`order_paid`。
- 中文文案放在节点显示文本里，不要放在节点 ID 里。
- 优先使用最基础的箭头、节点、分支语法，避免不必要的样式和 class 定义。
- 如果文案包含特殊字符，优先用带引号的写法，例如 `A["创建需求"]`。
- 不使用兼容性不稳定的图类型或主题配置。

## 输出前自检

- 图类型是否匹配问题本身
- 主流程是否闭环
- 异常路径是否至少覆盖最重要的一条
- 节点名称是否和正文术语一致
- 代码块是否以 ```mermaid 开始并正确结束

## 可复用骨架

### 业务流程

```mermaid
flowchart TD
    A["发现需求"] --> B["整理目标与约束"]
    B --> C{"是否信息充分"}
    C -->|是| D["输出需求与方案"]
    C -->|否| E["补充假设与待确认项"]
    E --> D
    D --> F["进入评审"]
```

### 页面或模块流转

```mermaid
flowchart LR
    H["首页"] --> L["列表页"]
    L --> D["详情页"]
    D --> A["执行关键动作"]
    A --> R["结果反馈"]
```

### 角色与系统交互

```mermaid
sequenceDiagram
    participant U as 用户
    participant P as 产品系统
    participant S as 服务端

    U->>P: 提交请求
    P->>S: 校验并创建任务
    S-->>P: 返回处理结果
    P-->>U: 展示结果与下一步
```

### 状态流转

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> Reviewing: 提交评审
    Reviewing --> Approved: 通过
    Reviewing --> Rejected: 驳回
    Rejected --> Draft: 修改后重提
    Approved --> [*]
```

## 建议

- 小需求通常 1 个图就够，优先画主流程。
- 中等复杂度需求优先给 2 个图：一个流程图，一个状态图或时序图。
- 如果正文已经非常长，图里只保留关键节点，避免把整份 PRD 塞进图表。
