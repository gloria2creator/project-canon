# GitHub 仓库设置速查

> 下面这些需要在 GitHub 仓库页面手动填写（Settings / About / Social preview / Releases）。
> README 已上传，此处不再涉及 README 内容修改。

---

## 1. Description（About 描述）

建议替换为：

```text
Agent Skill for long-running AI coding projects: maintain one source of truth, reconcile docs with code, track decisions, archive stale plans, and resume after context loss.
```

覆盖关键词：`agent skill`、`ai coding`、`source of truth`、`docs`、`code`、`decisions`、`archive`、`context loss`。

---

## 2. Topics（最多 20 个，建议先加 10 个）

```text
agent-skills
codex-skills
ai-coding
coding-agents
ai-workflows
context-engineering
project-documentation
knowledge-management
source-of-truth
developer-tools
```

可选补充（再挑 2～3 个）：

```text
decision-records
project-governance
documentation
markdown
```

策略：大词带流量 + 小词抓精准需求，不要只堆 `ai-agents` 这种超级大词。

---

## 3. Social Preview

文件：`assets/social-preview.jpg`

- 尺寸：1280 × 640
- 大小：163.8 KB（小于 1 MB 限制）
- 上传路径：Repository → Settings → Social preview → Edit

---

## 4. Release v1.0.0

### Tag

```text
v1.0.0
```

### Title

```text
Project Canon v1.0.0 — Agent Skill for canonical truth in long-running AI coding projects
```

### Release Notes

```markdown
## 初始发布

Project Canon 是一个面向长期 AI 协作项目的 Agent Skill，用于维护项目唯一有效的事实、决策、实施状态与接续入口。

### 包含内容

- `SKILL.md`：Agent 核心执行流程
- `references/`：授权分层、权威职责、来源吸收、审计恢复、结构化治理参考
- `assets/templates/`：决策、变更、交付、来源预览的最小模板
- `agents/openai.yaml`：OpenAI Agent 配置示例
- 中英双语 README

### 适用场景

- 多份方案同时声称自己是最新版
- 聊天想法被误写为正式结论
- 已确认 / 已实现 / 验证通过 被混为一谈
- 换会话、模型或 Agent 后重复讨论已有决定
- 历史方案需要安全吸收和归档

### 快速开始

```bash
git clone https://github.com/gloria2creator/project-canon.git \
  <your-agent-skills-directory>/project-canon
```

然后调用：

```text
使用 $project-canon 审计这个项目。
```

### 后续计划

- 收集真实冲突案例
- 适配更多 Agent 平台
- 根据反馈迭代模板和流程
```

---

## 5. 分享配图

- 横版（GitHub / X / 即刻）：`assets/social-preview.jpg`（1280 × 640）
- 方版（小红书 / 微信朋友圈）：`assets/share-card-square.jpg`（1080 × 1080）
