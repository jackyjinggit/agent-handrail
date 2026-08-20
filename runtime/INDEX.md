# 运行库索引（runtime/INDEX.md）

本文件是 `agent-handrail` 包的**自包含导航**。你不需要任何外部文件即可使用本包。它就是"运行库"——别人 clone 即用，零外部依赖。

## 文件地图

| 文件 | 作用 |
|------|------|
| `plugin.json` | WorkBuddy expert 包声明（被平台读取） |
| `README.md` | 总导航 + 安装 + 使用 |
| `ASSESSMENT.md` | 为什么做这个扶手（决策评估 + 设计 rationale，也作内测提交叙事） |
| `agents/agent-handrail.md` | 扶手 expert 角色定义 |
| `skills/handrail-core/SKILL.md` | 核心扶手行为（6 条 guardrail 操作化） |
| `skills/handrail-runtime/SKILL.md` | 轻量运行库导航 skill（本包的自索引） |
| `runtime/guardrails.md` | 最小红线集（6 条，平台无关） |
| `avatars/expert.png` | 头像占位 |

## 概念索引（去 PDSS 专有名词）

- **扶手（Handrail）**＝ 架在 harness 之上的增量安全 / 可用层，不替换原 agent。
- **不越权（No-overreach）**＝ AI 不代行终裁，只提议；终裁权归人。
- **脱敏（Desensitize）**＝ 输出前扫描并替换凭据 / PII / 敏感路径。
- **前端可见交付（Frontend-visible delivery）**＝ 产物必须到用户眼前，不只落盘。
- **压缩前置备份（Pre-compression backup）**＝ 上下文压缩 / 接管前先备份对话资产。
- **可证伪 / 有源（Falsifiable / Sourced）**＝ 每条主张标注来源，无据标未知。

## 导航顺序（包内自索引，替代外部重型导航）

1. 想装 → `README.md`「安装」
2. 想懂角色 → `agents/agent-handrail.md`
3. 想懂具体行为 → `skills/handrail-core/SKILL.md`
4. 想懂红线 → `runtime/guardrails.md`
5. 想懂为什么 → `ASSESSMENT.md`

全部自包含，无外链、无镜像、无多副本。
