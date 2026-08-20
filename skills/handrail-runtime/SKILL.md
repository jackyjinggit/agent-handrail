---
name: handrail-runtime
version: 0.1.0
description: Self-contained navigation/索引 for the agent-handrail package — replaces heavy external navigation (external INDEX / _inbox / handover / mirror copies) with one in-repo index. Load this when you need to find anything inside the package.
---

# handrail-runtime（轻量运行库导航）

> 本包自带导航，clone 即用，零外部依赖。本 skill 是包内自索引，等同"运行库"。

## 何时加载

- 想找包内某文件 / 概念
- 想确认"还缺什么文件"
- 想向他人解释包结构

## 导航（完整文件地图）

见 `runtime/INDEX.md`（自包含目录地图 + 概念索引 + 导航顺序）。本 skill 不重复内容，只指向 `runtime/INDEX.md`，防双源漂移。

## 设计纪律

- **自包含**：无外链、无镜像、无多副本。
- **增量**：只读包内，不改宿主 harness 内部。
- **轻量**：总文件数 ≤ 10，单文件适度。
- **可验证**：任何"文件不存在"结论须先在包内 glob 复核，禁止凭文件名推断。
