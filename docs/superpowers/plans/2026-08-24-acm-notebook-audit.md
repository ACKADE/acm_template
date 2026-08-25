# ACM Notebook Audit Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 先对 `笔记本.md` 做全量、只读的 ICPC 实战审核；随后将每个已确认的改动单独提交给用户审核，通过一项才修改一项。

**Architecture:** 将 236 个围栏块按“可直接提交、需补题目变量、仅作推导/速查、不可安全使用”分级。审核阶段不改动代码；交付一份按章节和风险排序的变更队列。实施阶段每次只展示一个原文片段、拟议替换、原因、前置条件和验证方式，等待用户明确批准后才写入。

**Tech Stack:** C++17、GCC 编译检查、PowerShell、Markdown。

**Spec:** `C:\Users\32654\Desktop\acm_template\笔记本.md`

## Global Constraints

- 审核阶段不得修改 `笔记本.md`；实施阶段仅在用户逐项批准后修改对应的单个条目。
- 保持原章节排序、中文命名和 `#define int long long` 使用习惯。
- 不以仅由 `int` 宽度造成的溢出风险作为修复理由。
- 未完成模板可重写为可靠的竞赛模板，但必须先获用户逐条批准。
- 只有经代码级复核、必要时对拍并确认的错误才能进入变更队列。
- 用户每次审核一个变更；未批准的条目保持不动。

---

### Task 1: 全量盘点并建立可审查索引

**Files:**
- Read: `C:\Users\32654\Desktop\acm_template\笔记本.md`
- Output: 按章节、代码块和风险等级排列的审核清单

- [ ] 逐章读取全部代码块，记录入口、依赖、假设、可编译性和算法风险。
- [ ] 区分确定性错误、题意相关缺口、稳定性问题和纯格式问题。
- [ ] 对关键算法建立独立小规模对拍或边界样例，记录结果与置信度。

### Task 2: 输出全量审核报告与变更队列

**Files:**
- Output: 可按编号逐条审核的变更列表

- [ ] 每项包含精确位置、原有风险、建议改法、使用前提、验证方案和置信度。
- [ ] 将“禁止直接带上场”的模板单列，并给出替换建议。
- [ ] 不在报告阶段写入 `笔记本.md`。

### Task 3: 逐项审批与修改

**Files:**
- Modify: `C:\Users\32654\Desktop\acm_template\笔记本.md`（每次仅一个已批准条目）
- Test: 该条目对应的语法检查、样例或对拍

- [ ] 展示条目 N 的原片段与拟议替换，等待用户审核。
- [ ] 收到批准后，仅应用条目 N，并完成该条目验证。
- [ ] 记录批准、拒绝或延后的结论，再处理条目 N+1。

### Task 4: 最终赛场可用性复核

**Files:**
- Read: `C:\Users\32654\Desktop\acm_template\笔记本.md`
- Test: 围栏配对、各已批准条目的独立验证、`git diff --check`

- [ ] 复读全文，确认所有已批准修改都保留原有章节可查性。
- [ ] 复核每个“可直接提交”模板的依赖、边界、复杂度和调用接口。
- [ ] 交付已通过、保留风险和未批准改动的最终状态。
