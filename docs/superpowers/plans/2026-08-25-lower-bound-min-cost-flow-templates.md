# Lower-Bound Min-Cost Flow Templates Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use `executing-plans` to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the four unverified lower-bound min-cost flow snippets in `笔记本.md` with four independently copyable, contest-ready templates that optimize negative cycles correctly.

**Architecture:** Each public class keeps the existing notebook interface: constructor, `add_edge`, `solve`, and `get_flow`, and embeds its own Dinic feasibility construction plus negative-cycle cancellation logic. The four classes intentionally duplicate this implementation so copying any single class from the notebook has no hidden dependency. The source/sink variants add a temporary `t -> s` edge only while constructing a feasible flow; the max/min variants remove it before changing the flow value.

**Tech Stack:** C++17, GCC syntax checks, exhaustive small-graph verification.

**Spec:** `C:\Users\32654\Desktop\acm_template\笔记本.md`

## Global Constraints

- Preserve the four existing section headings and their public class names.
- Each of the four C++ code blocks must be self-contained: it cannot inherit from, include, or otherwise depend on another code block in the notebook.
- Keep node numbering `0..n-1`, `add_edge(u, v, low, high, cost)`, and the returned forward-edge index used by `get_flow`.
- Assume the notebook preamble contains `#define int long long`; do not add duplicate overflow-only guards.
- A solver object is single-use: one construction, all edges, one `solve` call.
- Cost optimization must include negative cycles; no snippet may contain a “draft” or “do not submit” warning.

---

### Task 1: Define the common algorithm and regression cases

**Files:**
- Read: `C:\Users\32654\Desktop\acm_template\笔记本.md:12387-13073`
- Test: temporary C++17 verification harness

**Interfaces:**
- Consumes: `BoundCost*::add_edge(int u, int v, int low, int high, int cost)`.
- Produces: minimum-cost circulation, feasible `s -> t` flow, lexicographic minimum-cost maximum flow, and lexicographic minimum-cost minimum nonnegative flow.

- [x] **Step 1: Establish the residual-flow construction**

Use `in[v] += low; in[u] -= low`. Add `S -> i` for positive `in[i]` and `i -> T` for negative `in[i]`; Dinic must saturate their total capacity. For an `s -> t` flow, add `t -> s` with capacity `INF` while testing feasibility. The flow on that edge is the initial `s -> t` value.

- [x] **Step 2: Add the cost-optimality operation**

Run Bellman-Ford with all original vertices initially at distance zero. If relaxation happens on the `n`-th pass, trace predecessors `n` times to enter a negative residual cycle, push its bottleneck capacity, and repeat until no negative cycle exists.

- [x] **Step 3: Specify regression instances**

Compile and run cases covering: a negative-cost circulation with no lower-bound demand; a feasible circulation that needs lower-bound balancing; an `s -> t` feasible flow whose cheapest value differs from the initial feasible value; equal-value paths with different costs; and a lower-bound instance with no solution.

### Task 2: Replace the four notebook snippets

**Files:**
- Modify: `C:\Users\32654\Desktop\acm_template\笔记本.md:12387-13073`

**Interfaces:**
- `BoundCostCircuitFeasible::solve() -> pair<bool, int>`.
- `BoundCostFlowFeasible::solve(int s, int t) -> pair<bool, int>`.
- `BoundCostMaxFlow::solve(int s, int t) -> pair<int, int>` with `{-1, -1}` for infeasible input.
- `BoundCostMinFlow::solve(int s, int t) -> pair<int, int>` with `{-1, -1}` for infeasible input.

- [x] **Step 1: Implement feasible min-cost circulation**

After satisfying lower-bound demand, disable the super-source and super-sink residual edges. Cancel all negative cycles among original vertices. Return `sum(get_flow(u, idx) * cost)` across original edges.

- [x] **Step 2: Implement feasible min-cost `s -> t` flow**

Keep the temporary zero-cost `t -> s` edge during cycle cancellation so cycles can change the nonnegative `s -> t` value. Return the globally minimum-cost feasible flow.

- [x] **Step 3: Implement min-cost maximum and minimum `s -> t` flow**

Disable the temporary `t -> s` edge after feasibility. For maximum flow, Dinic-augment `s -> t`; for minimum flow, Dinic-augment `t -> s` with limit equal to the initial value. In both cases, cancel negative cycles afterward to choose the least-cost solution at the fixed extremal value.

- [x] **Step 4: Align prose and examples**

Remove all draft warnings; document the single-use rule, the negative-cycle optimization, result semantics, and the cost-cycle-canceling complexity caveat. Keep the existing class names and usage shape.

### Task 3: Validate the final notebook blocks

**Files:**
- Read: `C:\Users\32654\Desktop\acm_template\笔记本.md`
- Test: extracted C++17 blocks and temporary regression harness

- [x] **Step 1: Verify Markdown boundaries**

Check that the four headings occur once, none contains `推导草稿` or `勿直接提交`, and all four C++ fences close before their usage examples.

- [ ] **Step 2: Verify compilation**

For each of the four snippets, prepend `#include <bits/stdc++.h>`, `#define int long long`, and `using namespace std;`, then run `g++ -std=c++17 -fsyntax-only`.

Status: attempted on 2026-08-25; this workspace has no `g++`, `clang++`, or MSVC compiler on PATH, so this exact check cannot run locally.

- [x] **Step 3: Verify behavior**

Run the regression harness from Task 1 and compare every returned feasibility flag, flow value, cost, and queried edge flow with the expected result.

- [x] **Step 4: Inspect the scoped diff**

Run `git diff --check -- 笔记本.md` and inspect the exact diff around the four affected headings; leave unrelated notebook changes untouched.
