<div align="right">

[English](README.md) · [中文](README.zh-CN.md)

</div>

# Agent Skills

**面向 AI 编码智能体的生产级工程技能库。**

本技能库将资深工程师在软件交付全生命周期中所遵循的工作流、质量门禁与最佳实践，封装为结构化指令，使 AI 智能体能够在各阶段一致、可复现地执行专业级工程实践。

![Addy's Agent Skills](https://addyosmani.com/assets/images/addys-agent-skills.jpg)

```
  DEFINE          PLAN           BUILD          VERIFY         REVIEW          SHIP
 ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐
 │ Idea │ ───▶ │ Spec │ ───▶ │ Code │ ───▶ │ Test │ ───▶ │  QA  │ ───▶ │  Go  │
 │Refine│      │  PRD │      │ Impl │      │Debug │      │ Gate │      │ Live │
 └──────┘      └──────┘      └──────┘      └──────┘      └──────┘      └──────┘
  /spec          /plan          /build        /test         /review       /ship
```

---

## 斜杠命令（Slash Commands）

7 条斜杠命令映射完整研发生命周期；每条命令会自动激活对应技能组合。

| 场景 | 命令 | 核心原则 |
|------|------|----------|
| 定义交付范围 | `/spec` | 先规格、后编码 |
| 拆解实施方案 | `/plan` | 小粒度、原子化任务 |
| 增量式实现 | `/build` | 单次仅交付一个切片 |
| 验证行为正确性 | `/test` | 测试即证据 |
| 合并前质量审查 | `/review` | 持续改善代码健康度 |
| 简化实现复杂度 | `/code-simplify` | 清晰优先于炫技 |
| 生产环境发布 | `/ship` | 更快即更安全 |

规格就绪后希望减少人工编排？使用 **`/build auto`**：在一次审批通过后自动生成计划并自主执行全部任务。它消除的是任务间的人工接力，而非验证环节——每个任务仍遵循测试驱动开发、独立提交，并在失败或高风险步骤处暂停等待人工介入。

技能亦可根据意图自动激活：设计 API 触发 `api-and-interface-design`，构建 UI 触发 `frontend-ui-engineering`，以此类推。

---

## 快速开始

<details>
<summary><b>Claude Code（推荐）</b></summary>

**Marketplace 安装：**

```
/plugin marketplace add addyosmani/agent-skills
/plugin install agent-skills@addy-agent-skills
```

> **SSH 报错？** Marketplace 默认通过 SSH 克隆仓库。若尚未配置 GitHub SSH 密钥，可[添加 SSH 密钥](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)，或使用完整 HTTPS URL 强制 HTTPS 克隆：
> ```bash
> /plugin marketplace add https://github.com/addyosmani/agent-skills.git
> /plugin install agent-skills@addy-agent-skills
> ```

**本地 / 开发环境：**

```bash
git clone https://github.com/addyosmani/agent-skills.git
claude --plugin-dir /path/to/agent-skills
```

</details>

<details>
<summary><b>Cursor</b></summary>

将任意 `SKILL.md` 复制到 `.cursor/rules/`，或直接引用完整 `skills/` 目录。详见 [docs/cursor-setup.md](docs/cursor-setup.md)。

</details>

<details>
<summary><b>Antigravity CLI</b></summary>

以原生插件形式安装，集成技能、子智能体与斜杠命令。详见 [docs/antigravity-setup.md](docs/antigravity-setup.md)。

**从仓库安装：**

```bash
agy plugin install https://github.com/addyosmani/agent-skills.git
```

**从本地克隆安装：**

```bash
git clone https://github.com/addyosmani/agent-skills.git
agy plugin install ./agent-skills
```

</details>

<details>
<summary><b>Gemini CLI</b></summary>

以原生技能形式安装以支持自动发现，或写入 `GEMINI.md` 作为持久上下文。详见 [docs/gemini-cli-setup.md](docs/gemini-cli-setup.md)。

**从仓库安装：**

```bash
gemini skills install https://github.com/addyosmani/agent-skills.git --path skills
```

**从本地克隆安装：**

```bash
gemini skills install ./agent-skills/skills/
```

</details>

<details>
<summary><b>Windsurf</b></summary>

将技能内容纳入 Windsurf 规则配置。详见 [docs/windsurf-setup.md](docs/windsurf-setup.md)。

</details>

<details>
<summary><b>OpenCode</b></summary>

通过 AGENTS.md 与 `skill` 工具实现智能体驱动的技能执行。

详见 [docs/opencode-setup.md](docs/opencode-setup.md)。

</details>

<details>
<summary><b>GitHub Copilot</b></summary>

将 `agents/` 中的智能体定义用作 Copilot 角色画像，技能内容写入 `.github/copilot-instructions.md`。详见 [docs/copilot-setup.md](docs/copilot-setup.md)。

</details>

<details>
  <summary><b>Kiro IDE & CLI</b></summary>
  Kiro 技能位于 `.kiro/skills/`，可配置为项目级或全局级；同时支持 Agents.md。文档：https://kiro.dev/docs/skills/
</details>

<details>
<summary><b>Codex / 其他智能体</b></summary>

技能为纯 Markdown 格式，适用于任何接受系统提示词或指令文件的智能体。详见 [docs/getting-started.md](docs/getting-started.md)。

</details>

---

## 全部 24 项技能

上述命令为编排入口；本技能包共含 24 项技能——23 项生命周期技能加 1 项元技能 `using-agent-skills`。每项技能均为结构化工作流，包含执行步骤、验证门禁与反合理化对照表；亦可直接按名称引用。

### 元技能 — 技能路由与发现

| 技能 | 职责 | 触发场景 |
|------|------|----------|
| [using-agent-skills](skills/using-agent-skills/SKILL.md) | 将 incoming 工作映射至对应技能工作流，并定义共享运行规则 | 会话启动或需判定适用技能时 |

### Define — 需求澄清与规格定义

| 技能 | 职责 | 触发场景 |
|------|------|----------|
| [interview-me](skills/interview-me/SKILL.md) | 逐题访谈，提取用户真实意图（而非其自认为的意图），直至置信度约 95% | 需求欠明确，或用户触发「interview me」/「grill me」 |
| [idea-refine](skills/idea-refine/SKILL.md) | 结构化发散/收敛思维，将模糊概念收敛为可执行方案 | 仅有粗略构想、需系统性探索时 |
| [spec-driven-development](skills/spec-driven-development/SKILL.md) | 在编码前撰写 PRD，覆盖目标、命令、结构、代码风格、测试策略与边界约束 | 新项目、新特性或重大变更启动时 |

### Plan — 任务拆解与排期

| 技能 | 职责 | 触发场景 |
|------|------|----------|
| [planning-and-task-breakdown](skills/planning-and-task-breakdown/SKILL.md) | 将规格拆解为可验证、带验收标准的小粒度任务，并处理依赖排序 | 已有规格、需生成可实施工作单元时 |

### Build — 增量实现

| 技能 | 职责 | 触发场景 |
|------|------|----------|
| [incremental-implementation](skills/incremental-implementation/SKILL.md) | 薄垂直切片：实现 → 测试 → 验证 → 提交；支持特性开关、安全默认值与可回滚变更 | 变更涉及多个文件时 |
| [test-driven-development](skills/test-driven-development/SKILL.md) | 红-绿-重构循环、测试金字塔（80/15/5）、测试粒度、DAMP 优于 DRY、Beyoncé 法则、浏览器测试 | 实现逻辑、修复缺陷或变更行为时 |
| [context-engineering](skills/context-engineering/SKILL.md) | 在正确时机注入正确上下文——规则文件、上下文打包、MCP 集成 | 会话启动、任务切换或输出质量下降时 |
| [source-driven-development](skills/source-driven-development/SKILL.md) | 每项框架决策均锚定官方文档——验证、引用来源、标注未核实内容 | 需产出有权威来源支撑的实现时 |
| [doubt-driven-development](skills/doubt-driven-development/SKILL.md) | 对抗式全新上下文审查：CLAIM → EXTRACT → DOUBT → RECONCILE → STOP；支持经用户授权的跨模型升级 | 生产/安全/不可逆等高利害场景、陌生代码库，或「现在验证」成本低于「事后排障」时 |
| [frontend-ui-engineering](skills/frontend-ui-engineering/SKILL.md) | 组件架构、设计系统、状态管理、响应式布局、WCAG 2.1 AA 无障碍合规 | 构建或修改用户界面时 |
| [api-and-interface-design](skills/api-and-interface-design/SKILL.md) | 契约优先设计、Hyrum 定律、单版本规则、错误语义、边界校验 | 设计 API、模块边界或公共接口时 |

### Verify — 行为验证与故障恢复

| 技能 | 职责 | 触发场景 |
|------|------|----------|
| [browser-testing-with-devtools](skills/browser-testing-with-devtools/SKILL.md) | 通过 Chrome DevTools MCP 获取运行时数据——DOM 检查、控制台日志、网络追踪、性能剖析 | 构建或调试浏览器端应用时 |
| [debugging-and-error-recovery](skills/debugging-and-error-recovery/SKILL.md) | 五步分诊：复现 → 定位 → 缩减 → 修复 → 防护；停线规则与安全降级 | 测试失败、构建中断或行为异常时 |

### Review — 合并前质量门禁

| 技能 | 职责 | 触发场景 |
|------|------|----------|
| [code-review-and-quality](skills/code-review-and-quality/SKILL.md) | 五维审查、变更粒度（约 100 行）、严重级别标签（Nit/Optional/FYI）、审查时效规范、拆分策略 | 任何变更合并前 |
| [code-simplification](skills/code-simplification/SKILL.md) | Chesterton 栅栏、500 行规则；在保持行为不变前提下降低认知复杂度 | 功能正确但可读性/可维护性不足时 |
| [security-and-hardening](skills/security-and-hardening/SKILL.md) | OWASP Top 10 防护、认证模式、密钥管理、依赖审计、三层边界体系 | 处理用户输入、认证、数据存储或外部集成时 |
| [performance-optimization](skills/performance-optimization/SKILL.md) | 先度量后优化——Core Web Vitals 目标、性能剖析工作流、Bundle 分析、反模式识别 | 存在性能 SLA 或怀疑性能回归时 |

### Ship — 可置信发布

| 技能 | 职责 | 触发场景 |
|------|------|----------|
| [git-workflow-and-versioning](skills/git-workflow-and-versioning/SKILL.md) | 主干开发（Trunk-based）、原子提交、变更粒度（约 100 行）、提交即存档点模式 | 任何代码变更（始终适用） |
| [ci-cd-and-automation](skills/ci-cd-and-automation/SKILL.md) | 左移（Shift Left）、更快即更安全、特性开关、质量门禁流水线、失败反馈闭环 | 搭建或修改构建/部署流水线时 |
| [deprecation-and-migration](skills/deprecation-and-migration/SKILL.md) | 代码即负债思维、强制 vs 建议弃用、迁移模式、僵尸代码清理 | 下线旧系统、迁移用户或退役特性时 |
| [documentation-and-adrs](skills/documentation-and-adrs/SKILL.md) | 架构决策记录（ADR）、API 文档、内联文档规范——记录「为何」而非仅「如何」 | 架构决策、API 变更或特性发布时 |
| [observability-and-instrumentation](skills/observability-and-instrumentation/SKILL.md) | 结构化日志、RED 指标、OpenTelemetry 链路追踪、基于症状的告警——构建即埋点 | 添加遥测或发布生产运行时 |
| [shipping-and-launch](skills/shipping-and-launch/SKILL.md) | 发布前检查清单、特性开关生命周期、分阶段灰度、回滚预案、监控配置 | 准备生产环境部署时 |

---

## 智能体角色画像（Agent Personas）

预配置专家角色，用于定向审查与专项评估：

| 智能体 | 角色 | 审查视角 |
|--------|------|----------|
| [code-reviewer](agents/code-reviewer.md) | 资深 Staff Engineer | 五维代码审查，以「Staff Engineer 是否会批准」为基准 |
| [test-engineer](agents/test-engineer.md) | QA 专家 | 测试策略、覆盖率分析与 Prove-It 模式 |
| [security-auditor](agents/security-auditor.md) | 安全工程师 | 漏洞检测、威胁建模、OWASP 评估 |
| [web-performance-auditor](agents/web-performance-auditor.md) | Web 性能工程师 | Core Web Vitals 审计（Quick/Deep 模式）与指标诚实性规则；通过 `/webperf` 触发 |

---

## 参考检查清单

技能在需要时按需引用的速查材料：

| 参考文档 | 覆盖范围 |
|----------|----------|
| [testing-patterns.md](references/testing-patterns.md) | 测试结构、命名、Mock、React/API/E2E 示例、反模式 |
| [security-checklist.md](references/security-checklist.md) | 提交前检查、认证、输入校验、安全头、CORS、OWASP Top 10 |
| [performance-checklist.md](references/performance-checklist.md) | Core Web Vitals 目标、前后端检查项、度量命令 |
| [accessibility-checklist.md](references/accessibility-checklist.md) | 键盘导航、屏幕阅读器、视觉设计、ARIA、测试工具 |

---

## 技能运行机制

每项技能遵循统一结构规范（Skill Anatomy）：

```
┌─────────────────────────────────────────────────┐
│  SKILL.md                                       │
│                                                 │
│  ┌─ Frontmatter ─────────────────────────────┐  │
│  │ name: lowercase-hyphen-name               │  │
│  │ description: Guides agents through [task].│  │
│  │              Use when…                    │  │
│  └───────────────────────────────────────────┘  │
│  Overview         → 技能职责说明                │
│  When to Use      → 触发条件                    │
│  Process          → 分步工作流                  │
│  Rationalizations → 借口与反驳对照表            │
│  Red Flags        → 风险信号                    │
│  Verification     → 证据要求                    │
└─────────────────────────────────────────────────┘
```

**核心设计原则：**

- **流程驱动，而非文档堆砌。** 技能是可执行工作流，含步骤、检查点与退出准则，而非供浏览的参考手册。
- **反合理化（Anti-rationalization）。** 每项技能均收录智能体跳过步骤的常见借口（如「测试稍后补」）及对应反驳，降低流程逃逸概率。
- **验证不可协商。** 每项技能以证据要求收尾——测试通过、构建输出、运行时数据。「看起来对」永远不够。
- **渐进式披露（Progressive disclosure）。** `SKILL.md` 为入口；支撑材料按需加载，控制 Token 消耗。

---

## 项目结构

```
agent-skills/
├── skills/                            # 24 项技能（23 生命周期 + 1 元技能）
│   ├── interview-me/                  #   Define
│   ├── idea-refine/                   #   Define
│   ├── spec-driven-development/       #   Define
│   ├── planning-and-task-breakdown/   #   Plan
│   ├── incremental-implementation/    #   Build
│   ├── context-engineering/           #   Build
│   ├── source-driven-development/     #   Build
│   ├── doubt-driven-development/      #   Build
│   ├── frontend-ui-engineering/       #   Build
│   ├── test-driven-development/       #   Build
│   ├── api-and-interface-design/      #   Build
│   ├── browser-testing-with-devtools/ #   Verify
│   ├── debugging-and-error-recovery/  #   Verify
│   ├── code-review-and-quality/       #   Review
│   ├── code-simplification/          #   Review
│   ├── security-and-hardening/        #   Review
│   ├── performance-optimization/      #   Review
│   ├── git-workflow-and-versioning/   #   Ship
│   ├── ci-cd-and-automation/          #   Ship
│   ├── deprecation-and-migration/     #   Ship
│   ├── documentation-and-adrs/        #   Ship
│   ├── observability-and-instrumentation/ # Ship
│   ├── shipping-and-launch/           #   Ship
│   └── using-agent-skills/            #   Meta：技能包使用指南
├── agents/                            # 4 个专家角色画像
├── references/                        # 4 份补充检查清单
├── hooks/                             # 会话生命周期钩子
├── .claude/commands/                  # 7 条斜杠命令（Claude Code）
├── .gemini/commands/                  # 7 条斜杠命令（Gemini CLI）
├── commands/                          # 8 条斜杠命令（Antigravity CLI）
├── plugin.json                        # Antigravity 插件清单
└── docs/                              # 各工具安装指南
```

---

## 为何需要 Agent Skills？

AI 编码智能体默认走最短路径——往往跳过规格、测试、安全审查等保障软件可靠性的工程实践。Agent Skills 以结构化工作流约束智能体，使其具备与资深工程师相当的生产级交付纪律。

每项技能编码的是经过实战检验的工程判断：*何时*写规格、*测什么*、*如何*审查、*何时*发布。它们不是泛化提示词，而是区分生产级交付与原型级产出的、有立场、流程化的工作流。

技能内嵌 Google 工程文化最佳实践——涵盖 [Software Engineering at Google](https://abseil.io/resources/swe-book) 与 [Google 工程实践指南](https://google.github.io/eng-practices/) 中的核心概念：API 设计中的 Hyrum 定律、测试中的 Beyoncé 法则与测试金字塔、代码审查中的变更粒度与时效规范、简化中的 Chesterton 栅栏、Git 工作流中的主干开发、CI/CD 中的左移与特性开关，以及将代码视为负债的专用弃用技能。这些不是抽象口号，而是嵌入智能体逐步执行流程中的可操作约束。

---

## 贡献指南

技能应具备以下特质：**具体**（可执行步骤，非空泛建议）、**可验证**（明确退出准则与证据要求）、**经实战检验**（源于真实工作流）、**精简**（仅保留引导智能体所需内容）。

格式规范见 [docs/skill-anatomy.md](docs/skill-anatomy.md)，贡献流程见 [CONTRIBUTING.md](CONTRIBUTING.md)。

---

## 许可证

MIT — 可在项目、团队与工具中自由使用本技能库。
