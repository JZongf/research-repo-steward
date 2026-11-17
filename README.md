# 研究项目库管家

`research-repo-steward` 是一个用中文工作的 Agent Skill，支持 Codex、Claude Code 和 Google Antigravity。它帮你理清科研仓库：代码从哪里运行，数据、实验记录和结果放在哪里，以及怎样从结果追溯到对应的代码、配置和输入。它根据你的研究流程定规则，不套固定的目录模板。

## 什么时候用

| 场景 | 技能会做什么 |
| --- | --- |
| **建立规范**：新项目刚起步，或已有项目缺少统一约定 | 先检查仓库，再通过几轮中文问答明确工作流程、目录职责和命名规则。你确认方案后，才写入规范并整理文件。 |
| **整理项目**：已有规则，但脚本、数据、旧实验和正式结果混放 | 按现有规范整理归属明确的文件，并更新受影响的路径引用。用途或版本有疑问的内容先保留原位。 |
| **更新规范**：研究流程变了，旧规则或目录不再合用 | 找出哪些规则需要改，列出受影响的目录和迁移方案，确认后一起更新。 |

项目规范以根目录的 `AGENTS.md` 为入口。删除研究材料或判废结果需要你单独确认。日常开发、修 Bug、改算法或重写研究结论不属于这项技能的范围。

## 安装

三个客户端共用同一份 [SKILL.md](SKILL.md)，无需额外脚本或 MCP 服务。在终端运行对应的一行，即可在本机的各个项目中使用：

```bash
# Codex
git clone https://github.com/JZongf/research-repo-steward.git ~/.agents/skills/research-repo-steward

# Claude Code
git clone https://github.com/JZongf/research-repo-steward.git ~/.claude/skills/research-repo-steward

# Google Antigravity（App、CLI 和 IDE）
git clone https://github.com/JZongf/research-repo-steward.git ~/.gemini/config/skills/research-repo-steward
```

已用 Git 安装的，在对应的技能目录运行 `git pull --ff-only` 即可更新。

**只在单个项目中使用：** 把 `SKILL.md` 放到下表所列的目录（相对于科研项目根目录）。Codex 可同时复制 `agents/openai.yaml`，用于显示中文技能名。

| 客户端 | 项目内的技能目录 |
| --- | --- |
| [Codex](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills) | `.agents/skills/research-repo-steward/` |
| [Claude Code](https://code.claude.com/docs/en/skills) | `.claude/skills/research-repo-steward/` |
| [Google Antigravity](https://antigravity.google/docs/skills) | `.agents/skills/research-repo-steward/` |

## 怎么用

用客户端打开**你要整理的科研项目**，然后调用技能：

| 客户端 | 调用方式 |
| --- | --- |
| Codex | 输入 `$`，选择 `research-repo-steward`。 |
| Claude Code | 输入 `/research-repo-steward`。 |
| Antigravity App / CLI | 输入 `/research-repo-steward`。CLI 可用 `/skills` 查看技能，安装后可用 `/skills reload` 刷新。 |
| Antigravity IDE | 在对话中说「使用 research-repo-steward 技能」，可在代理面板的 Customizations 确认技能已加载。 |

在调用时带上你的需求，例如：

- **建立规范**：帮我建立这个项目的目录和实验记录规范。先看看现状，有需要我决定的地方再问我。
- **整理项目**：按现有 AGENTS.md 整理这个仓库，把散落的实验结果放回对应位置。归属不明的先留在原处。
- **更新规范**：我们现在用统一入口运行实验。请找出需要更新的规则和路径，先给我迁移方案，暂时别改文件。

技能运行时会检查项目的 `AGENTS.md`。如果你的 Claude Code 会话平时没有自动加载它（例如项目已有 `CLAUDE.md`），可在与 `AGENTS.md` 同目录的 `CLAUDE.md` 中加一行 `@AGENTS.md`，让日常对话也能读到同一份规范。详见 [Claude Code 项目指令文档](https://code.claude.com/docs/en/memory#share-one-file-with-other-coding-tools)。
