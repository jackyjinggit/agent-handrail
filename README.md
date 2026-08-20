# Agent Handrail（扶手·智能体安全可用层）

> 一个架在任意 agent harness 之上的**增量安全/可用扶手层**。不替换原 agent，只加护栏。
> 源自蒋平 PDSS 的 thesis《能力够了，扶手呢？》——能力够了，缺的是让人放心用的"扶手"。

English version below ↓

## 这是什么

`agent-handrail` 是一个 WorkBuddy expert 包（含 1 个 expert + 2 个 skill），把"安全/可用"做成一层可插拔的扶手：

- 动作前：风险分级 + 越权检查
- 输出后：脱敏 + 前端可见交付
- 全程：主张可证伪有源、压缩前备份

它**平台无关**——提炼自 PDSS 综合skill 红线但去掉专有名词，可套 DeepSeek Harness / Claude Code / 任何 agent 工具。

## 为什么轻量自包含（重点）

PDSS 本体是重型本地 vault（数千文件 + 多副本 + 索引导航）。本包**反其道**：自带 README + `runtime/INDEX.md` + `runtime/guardrails.md`，**clone 即用，零外部依赖**。你不需要 PDSS 的任何文件，也不需要外部 INDEX、`_inbox/`、handover、镜像副本。

## 安装

1. 把 `agent-handrail/` 目录放到 expert 插件目录（如 WorkBuddy 的 `plugins/marketplaces/my-experts/plugins/agent-handrail/`）。
2. 平台会自动发现该 expert 包；若未出现，在插件/专家管理里重载一次即可（包内自带 `plugin.json` 声明，无需额外注册脚本）。
3. 在会话里选「Agent Handrail」expert 即可。

## 文件地图（自包含导航 = 运行库）

| 文件 | 作用 |
|------|------|
| `plugin.json` | expert 包声明（平台读取） |
| `README.md` | 本文件：总导航 |
| `ASSESSMENT.md` | 决策评估 + 设计 rationale（设计取舍与边界说明） |
| `agents/agent-handrail.md` | 扶手 expert 角色 |
| `skills/handrail-core/SKILL.md` | 核心扶手行为（G1–G6 操作化） |
| `skills/handrail-runtime/SKILL.md` | 轻量运行库导航 skill（包内自索引） |
| `runtime/INDEX.md` | 自包含目录地图 + 概念索引 |
| `runtime/guardrails.md` | 最小红线集（G1–G6，平台无关） |
| `avatars/expert.png` | 头像占位 |

## 使用

加载后，expert 会在每一步动作前按 `runtime/guardrails.md` 自检。你也可直接问它：

- "执行前先给下一步做风险分级"
- "发出前先审输出有没有泄漏凭据"
- "这条主张有来源吗，没有标未知"

## 设计原则

- **增量**：架上去，不替换，可卸下。
- **轻量**：文件数 ≤ 10，无外部依赖。
- **自包含导航**：本包自己就是运行库，不需要外部 INDEX / `_inbox` / handover / 镜像副本。
- **平台无关**：去 PDSS 专有名词，保留行为本身。

---

## What is this (English)

`agent-handrail` is a WorkBuddy **expert package** (1 expert + 2 skills) that adds a pluggable *handrail* — a safety/usability layer — on top of any agent harness. It does **not** replace the agent; it only adds guardrails before actions and after outputs.

Born from the thesis *"Capability is enough — where's the handrail?"*: models are capable; what's missing is the layer that makes them safe and usable by real people.

### Install

Copy `agent-handrail/` into your expert plugins directory. The platform auto-discovers the package (its `plugin.json` declares it) — reload the expert list if it doesn't appear. Then pick the "Agent Handrail" expert in a session.

### Why self-contained & lightweight

The upstream PDSS system is a heavy local vault (thousands of files, mirrors, indexes). This package goes the opposite way: it ships its own `README.md` + `runtime/INDEX.md` + `runtime/guardrails.md`, so you `git clone` and use it with **zero external dependencies**. No PDSS files required.

### Files (self-contained navigation = the "runtime library")

See the table above. Everything you need to navigate the package lives inside it.

### Design principles

- **Incremental**: bolt on, don't replace, removable.
- **Lightweight**: ≤10 files, no external deps.
- **Self-contained navigation**: the package *is* its own runtime library — no external INDEX / inbox / handover / mirror copies.
- **Platform-agnostic**: PDSS-specific terms stripped.

---

## 配套 PDSS 脱敏快照（snapshot/，可选背景）

`snapshot/` 附一份 **PDSS 脱敏公开快照**（HAI 白皮书 / 执意对齐协议 IAAP / 术语表 / 馋臣效应说明等），用于佐证本扶手的方法论来源与对齐哲学。**全部脱敏**，不含任何内部敏感内容。

- 它是**可选背景材料，非运行依赖**——本包 clone 即用，无需 PDSS vault。
- 仅供公开分发，**不回灌** PDSS 真源；完整性哈希见 `snapshot/快照清单_manifest.md`。

详见 `snapshot/README_个人DSS快照包.md`。
