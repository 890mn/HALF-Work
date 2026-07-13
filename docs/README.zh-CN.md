# HALF-Work 中文介绍

> English is the default language for the executable Skill and the formal
> workflow. This document provides Chinese onboarding and usage guidance.

HALF-Work 是一个面向真实软件、固件、UI、硬件和架构任务的人机协作流程。
它允许用户先用自然语言描述目标，再由 Agent 根据真实仓库补全范围、方案、
证据、风险和验收条件，最后由用户确认后进入实现。

## 文档入口

- 默认执行规范：[`skills/half-work/SKILL.md`](../skills/half-work/SKILL.md)
- 任务模板：[`templates/ACTIVE_TASK_EXAMPLE.md`](../templates/ACTIVE_TASK_EXAMPLE.md)
- English README：[`README.md`](../README.md)

中文文档只承担介绍和入门作用。遇到规则冲突时，以英文 `SKILL.md`、项目自身
的 `AGENTS.md` 和当前项目控制文件为准。

## 四个独立维度

不要把下面四项合并成一个“等级”：

| 维度 | 取值 | 用途 |
| --- | --- | --- |
| HALF-Work Task Class | `L0` / `L1` / `L2` | 描述任务规模和风险 |
| Global Orchestration Level | 项目定义的 `Level 1/2/3` | 决定规划和 Agent 调度方式 |
| Model Thinking Level | `Light` / `Standard` / `Deep` | 决定思考深度 |
| Resource Mode | `economy` / `balanced` / `maximum` | 决定任务级资源预算 |

特别注意：`L0/L1/L2` 是 HALF-Work 的任务分类，不等同于项目全局的
`Level 1/2/3`，也不等同于模型思考等级。

## 两步式任务流程

### 第一步：Human Draft

用户只需要填写：

- 任务等级和模型思考等级；
- 任务概述与自然语言说明；
- 任务偏好、约束、保留行为和已知未知项。

不要求用户预先猜测文件名、API、测试命令或 Agent 分工。

### 第二步：Agent Refinement / User Review

Agent 读取真实仓库后补全：

- 当前架构、数据流和工作树归属；
- 允许修改项、明确不做项和升级条件；
- 至少两个可行方案及其风险；
- 静态、构建、运行时和设备验收证据；
- 每一项的 `Pass`、`Fail`、`Not Run`、`Accepted Limitation` 或
  `Carried Risk` 状态。

用户在第二步选择方案或要求收窄范围，确认后才进入实现。

## 调用方式

英文是默认调用形式：

```text
Use $half-work to turn this request into a two-step task contract,
inspect the repository, propose options and evidence, then wait for my decision.
```

中文也可以直接调用：

```text
使用 $half-work 将这个请求整理成两步式任务合同，检查真实仓库，提出方案和验收证据，等待我确认后再实现。
```

已有合同时，可以这样要求执行：

```text
Use $half-work to implement the accepted task, preserve unrelated worktree
changes, verify the declared gates, record metrics, and prepare the checkpoint.
```

## 验收和过程记录

编译通过不等于设备验收通过。浏览器、服务、网络、烧录、启动、实体交互和
用户观察应分别记录。任务还应尽可能记录耗时、Agent 调用次数、返工轮数、
人工决策数、变更文件和测试结果；无法可靠还原的数据标记为 unavailable，
不要补写虚构的精确值。

Git 提交可以使用类似格式：

```text
[L1][Review] fix weekly-only quota mapping
```

并通过 trailers 记录任务等级、阶段和证据。

## 公共与私有边界

公共仓库只保留可复用流程、模板和脱敏案例。不要提交凭据、私有 URL、机器
路径、生成密钥、项目私有控制文件或未经脱敏的历史记录。
