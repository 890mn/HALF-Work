# HALF-Work 中文介绍

> English is the default language for the executable Skill and the formal
> workflow. This document provides Chinese onboarding and usage guidance.

HALF-Work 是一个面向真实软件、固件、UI、硬件和架构任务的人机协作流程。
它允许用户先用自然语言描述目标，再由 Agent 根据真实仓库补全范围、方案、
证据、风险和验收条件；只有存在实质决策或缺少执行权限时才等待用户确认。

## 文档入口

- 默认执行规范：[`skills/half-work/SKILL.md`](../skills/half-work/SKILL.md)
- 任务模板：[`templates/ACTIVE_TASK_EXAMPLE.md`](../templates/ACTIVE_TASK_EXAMPLE.md)
- English README：[`README.md`](../README.md)

中文文档只承担介绍和入门作用。遇到规则冲突时，以英文 `SKILL.md`、项目自身
的 `AGENTS.md` 和当前项目控制文件为准。

## v0.2 状态

v0.2 是一次兼容性修订。它保留两步式任务合同和分层证据，但 Agent 会直接从
当前对话提取 Human Draft，不再要求用户重复填写已知信息；只有方案会实质改变
产品结果、风险、成本或外部副作用时才暂停等待决定。它仍是 Personal Pilot，
不是通用治理标准，也不会自动采集全部过程指标。

## 四个独立维度

不要把下面四项合并成一个“等级”：

| 维度 | 取值 | 用途 |
| --- | --- | --- |
| HALF-Work Task Class | `L0` / `L1` / `L2` | 描述任务规模和风险 |
| Global Orchestration Level | host-defined / `Not Defined` | 决定规划和 Agent 调度方式 |
| Model Thinking Level | `Light` / `Standard` / `Deep` / `Not Defined` | 决定思考深度 |
| Resource Mode | `economy` / `balanced` / `maximum` | 决定任务级资源预算 |

特别注意：`L0/L1/L2` 是 HALF-Work 的任务分类，不等同于项目全局的
`Level 1/2/3`，也不等同于模型思考等级。

## 两步式任务流程

### 第一步：Human Draft

用户只需要自然表达：

- 任务概述与自然语言说明；
- 任务偏好、约束、保留行为和已知未知项。

Agent 可以推断任务等级和本地支持的协调维度；不要求用户预先猜测文件名、
API、测试命令、Agent 分工，也不要求把对话内容再复制进模板。

### 第二步：Agent Refinement / User Review

Agent 读取真实仓库后补全：

- 当前架构、数据流和工作树归属；
- 允许修改项、明确不做项和升级条件；
- 选定方向；只有存在实质差异时才列出多个方案；
- 静态、构建、运行时和设备验收证据；
- 每一项的 `Pass`、`Fail`、`Not Run`、`Accepted Limitation` 或
  `Carried Risk` 状态。

当用户已明确要求“修复、实现、更新”等 bounded change，且不存在会改变结果的
实质分叉时，可以在说明方向和验收门后直接实现。缺少权限、需要扩展范围、存在
不可逆操作或验收取舍时，必须停下等待用户决定。

## 四种运行轨道

- `Refine`：把新请求收敛为最小任务合同；
- `Execute`：执行明确请求或已接受合同；
- `Review`：只读诊断或验证，不自动改实现；
- `Close`：核对证据、风险、指标和任务状态。

每个任务选择一个主轨道，也可以增加辅助轨道。例如“review 当前缺陷并改进”
可将 `Execute` 设为主轨道、`Review` 设为辅助轨道。

## 调用方式

英文是默认调用形式：

```text
Use $half-work to inspect this repository, infer a minimal contract from my
request, pause only for material decisions, then implement and verify it.
```

中文也可以直接调用：

```text
使用 $half-work 检查真实仓库，从当前对话推断最小任务合同，仅在存在实质决策时暂停，然后在范围内实现并验证。
```

如果 Skill 只存在于本仓库、尚未安装或链接到 Codex 的 Skill 目录，新对话可能
无法自动发现 `$half-work`。此时应先安装/链接 Skill，或在提示词中明确提供
`skills/half-work/SKILL.md` 的本地路径；README 链接本身不会触发 Skill。

已有合同时，可以这样要求执行：

```text
Use $half-work to implement the accepted task, preserve unrelated worktree
changes, verify the declared gates, record metrics, and prepare the checkpoint.
```

## 验收和过程记录

编译通过不等于设备验收通过。静态、Host/build、运行时和外部/设备证据应分别
记录。每一行还要注明是否为必需门；必需门处于 `Fail` 或 `Not Run` 时不能关闭。
变更文件、检查结果、遗留风险和实质人工决策是核心记录。耗时、Agent 调用次数
和返工轮数只在项目确实需要且能稳定计量时记录；无法可靠还原的数据标记为
`unavailable`，不要补写虚构的精确值。

Git 提交可以使用类似格式：

```text
[L1][Review] fix weekly-only quota mapping
```

并通过 trailers 记录任务等级、阶段和证据。

## 公共与私有边界

公共仓库只保留可复用流程、模板和脱敏案例。不要提交凭据、私有 URL、机器
路径、生成密钥、项目私有控制文件、`templates/ACTIVE_TASK.md` 或未经脱敏的
历史记录。
