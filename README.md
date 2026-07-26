# Project Canon

> **让 AI 记住项目真正已经决定了什么，而不是记住上一次聊天说了什么。**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent-Skill-5B5BD6)](SKILL.md)
[![Language](https://img.shields.io/badge/docs-中文-blue.svg)](SKILL.md)

项目里可能同时存在多份“最终方案”：最新修改的文件只是 AI 候选稿，代码实现了一部分但目标尚未确认，测试曾经通过却无法证明当前工作区仍然有效。

**Project Canon** 是一个面向长期 AI 协作项目的治理 Skill。它帮助 Agent 找到项目已有的权威入口，区分候选、决定、正式变更、实现状态与验证证据，并在上下文中断后安全接续。

它不替项目创造真相，而是维护和追溯项目已经确认的事实。

## 它解决什么问题

- 多份方案同时声称自己是最新版；
- 聊天里的想法被误写成正式结论；
- “已确认”“已实现”“验证通过”被混为一谈；
- 代码现实与目标方案冲突，却被静默覆盖；
- 历史方案吸收后仍散落在工作区；
- 换会话、模型或 Agent 后重复讨论已有决定；
- AI 为了整理而制造更多目录和重复文件。

Project Canon 让项目持续回答：

```text
什么已经确认？
什么仍待讨论？
为什么这样决定？
本次准备改变什么？
实际做到哪里？
证据来自哪里？
现在应该从哪里继续？
```

## 四种工作模式

| 模式 | 示例请求 | 默认动作 |
| --- | --- | --- |
| 审计 Audit | “哪个方案当前有效？” | 只读检查权威入口、冲突、重复、链接和状态 |
| 接管 Takeover | “帮我整理这个已有项目” | 分类并输出文件级 Preview，确认后迁移 |
| 维护 Maintain | “把这个决定写回项目” | 沿用现有结构，最小更新权威位置 |
| 恢复 Resume | “继续上次工作” | 重读入口、活跃变更、工作区和新鲜验证 |

> 审计默认只读。接管先 Preview。写回必须有授权。

## 核心模型

Project Canon 不强制统一目录名称，只要求这些职责能够被可靠定位：

| 职责 | 回答的问题 | 不应混入 |
| --- | --- | --- |
| Current | 当前确认的目标是什么？ | 实施进度、临时测试、未确认候选 |
| Proposal | 哪些问题仍在讨论？ | 已生效方案正文 |
| Decision | 为什么这样选择？ | 完整方案副本、开发流水 |
| Change | 本次正式准备改变什么？ | 日常进度、未来全部路线 |
| Delivery | 实现和验证到哪里？ | 产品与架构目标正文 |
| Evidence | 结论与验收依据来自哪里？ | 自动成为正式结论 |

最重要的状态边界是：

```text
方案已确认 ≠ 代码已实现 ≠ 验证已通过 ≠ 真实使用有效
```

## 安全写回流程

```text
发现项目本地权威
→ 完整阅读材料
→ 区分确认、候选、建议、外部事实与验证证据
→ 对照当前方案和已有决定
→ 输出写入 Preview
→ 用户确认
→ 最小写回权威位置
→ 更新来源映射
→ 按所选方案处理原始材料
→ 复核链接、状态和唯一权威
```

Preview 会分别列出：

1. **内容写回**：哪些结论进入哪个文件和章节；
2. **文件处置**：选择保守整理还是迁移归档，以及具体操作范围。

### 两种文件处置方案

**保守整理**

- 建立当前方案、Decision、Change、Delivery 和来源映射；
- 原材料留在原路径，不移动、不复制、不删除；
- 适合只想建立权威入口或项目仍在频繁开发的情况。

**迁移归档**

- 内容吸收和映射完成后，将已处理材料移入项目归档位置；
- 适合“整理并归档”以及希望清理散落旧方案的任务；
- 可以逐文件移动，也可以整体归档经过确认的历史来源包。

历史静态原型、设计交付目录或验证附件包可以包含 HTML、CSS、脚本、JSON、图片和字体。Project Canon 不按扩展名判断其性质，而会检查生命周期、运行入口、当前引用和替代关系。整体移动的范围必须与来源登记范围一致。

默认不删除原始材料。

## 本地规则优先

Project Canon 遵循：

> **先服从项目已有规则；没有规则时，才提出最小必要结构。**

它会优先读取项目中的 `AGENTS.md`、入口 README、文档规则、当前执行入口和版本控制状态。只有长期、多阶段并确有正式变更和证据追溯需求时，才建议结构化治理，例如：

```text
<canon-root>/
├─ README.md
├─ current/
├─ changes/
├─ delivery/
├─ decisions/
└─ evidence/
```

这只是参考结构，不是安装 Skill 后必须执行的迁移目标。

## 快速开始

将仓库放入支持 `SKILL.md` 的 Agent Skills 目录：

```bash
git clone https://github.com/gloria2creator/project-canon.git \
  <your-agent-skills-directory>/project-canon
```

然后显式调用：

```text
使用 $project-canon 审计这个项目。
找出当前权威方案、活跃工作、冲突和重复内容。
只输出 Preview，不修改文件。
```

或者：

```text
使用 $project-canon 接管这个项目的方案文档。
采用迁移归档方案，先列出内容写回与文件移动范围，
等待我确认后再执行。
```

## 常用提示词

### 找出当前有效方案

```text
使用 $project-canon 判断哪个方案当前有效。
验证文件声明、链接、本地术语和采用依据，不要只看修改时间。
只读审计，不要修复。
```

### 吸收会议记录或历史方案

```text
使用 $project-canon 审阅这份材料。
区分已确认、候选、冲突、需核验和无长期价值内容，
输出具体目标文件与章节的写入 Preview。
```

### 整理并迁移归档

```text
使用 $project-canon 整理并归档这些材料。
检查每份材料是否完成提取和映射；
整体来源包需要说明当前引用、替代关系和归档范围。
不要删除。
```

### 上下文中断后继续

```text
使用 $project-canon 恢复当前项目状态。
重新读取项目规则、当前方案、活跃 Change、Delivery、
Git 状态和新鲜验证，不要根据聊天印象继续。
```

### 对账文档与代码

```text
使用 $project-canon 对账当前方案、实施记录和代码现实。
分别报告权威冲突、状态滞后、追溯缺口、格式漂移和快照不稳定。
不要静默选择代码或文档为正确答案。
```

## 设计原则

1. **本地规则优先**：沿用项目已有目录、命名、编号和状态。
2. **只读优先**：审计、诊断和报告默认不修改文件。
3. **Preview 优先**：写回、移动、归档和删除先说明范围。
4. **授权分离**：采用规则、确认内容、确认 Gate 和文件处置不能互相替代。
5. **唯一权威**：同一结论只有一个主位置，其余位置链接引用。
6. **新鲜证据**：历史测试不能证明当前工作区仍然通过。
7. **可重复执行**：重复整理不产生重复 Decision、Change 或归档副本。
8. **最小治理**：不为未来可能出现的需求预建完整体系。

## 不适合什么场景

Project Canon 不是：

- Markdown 美化工具；
- 一次性批量总结数百份历史文件的清理器；
- 项目管理系统、需求系统或版本控制的替代品；
- 强制所有项目采用固定目录的脚本；
- 根据修改时间自动宣布最新版的工具；
- 在没有确认时替项目决定正式方案的自治 Agent。

面对大规模历史文件集中清理，应先使用专门的文档清理流程，再把稳定结论接入 Project Canon。

## 仓库结构

```text
project-canon/
├─ README.md
├─ SKILL.md
├─ agents/
│  └─ openai.yaml
├─ references/
│  ├─ adoption-and-migration.md
│  ├─ authority-and-routing.md
│  ├─ source-intake-and-archive.md
│  ├─ audit-and-continuation.md
│  └─ structured-governance-profile.md
└─ assets/
   └─ templates/
      ├─ intake-preview.md
      ├─ decision.md
      ├─ change.md
      └─ delivery.md
```

- [`SKILL.md`](SKILL.md)：Agent 使用的核心执行流程；
- [`references/adoption-and-migration.md`](references/adoption-and-migration.md)：授权分层、处置方案与迁移闸门；
- [`references/authority-and-routing.md`](references/authority-and-routing.md)：权威职责、冲突裁决与确认凭证；
- [`references/source-intake-and-archive.md`](references/source-intake-and-archive.md)：来源吸收、整体来源包和安全归档；
- [`references/audit-and-continuation.md`](references/audit-and-continuation.md)：审计、状态对账和恢复；
- [`references/structured-governance-profile.md`](references/structured-governance-profile.md)：复杂项目按需采用的参考结构；
- [`assets/templates/`](assets/templates/)：项目没有现成模板时使用的最小模板。

## 适合谁

- 长期使用 Codex、Claude Code、Cursor 等编码 Agent 的个人开发者；
- 同时维护产品、体验、架构和实现方案的小团队；
- 经常跨会话、模型或 Agent 协作的项目；
- 已积累多份历史方案，需要安全吸收和归档的仓库；
- 不想引入重型流程，但需要可靠“项目事实层”的团队。

## 贡献

欢迎通过 Issue 或 Pull Request 分享真实的权威冲突案例、不同项目结构下的适配经验，以及更轻量安全的治理方式。

贡献时请继续遵守 Project Canon 自己的原则：**解决真实问题，不为“以后可能需要”增加复杂度。**

## License

[MIT](LICENSE)

---

<p align="center">
  <strong>Project Canon</strong><br>
  One project. One traceable truth. Many agents.
</p>
