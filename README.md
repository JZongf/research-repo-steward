# 研究项目库管家

`research-repo-steward` 是一个用中文工作的 Codex 技能，帮你理清科研仓库：代码从哪里运行，数据、实验记录和结果放在哪里，以及怎样从结果追溯到对应的代码、配置和输入。它根据你的研究流程定规则，不套固定的目录模板。

## 什么时候用

| 场景 | 技能会做什么 |
| --- | --- |
| **建立规范**：新项目刚起步，或已有项目缺少统一约定 | 先检查仓库，再通过几轮中文问答明确工作流程、目录职责和命名规则。你确认方案后，才写入规范并整理文件。 |
| **整理项目**：已有规则，但脚本、数据、旧实验和正式结果混放 | 按现有规范整理归属明确的文件，并更新受影响的路径引用。用途或版本有疑问的内容先保留原位。 |
| **更新规范**：研究流程变了，旧规则或目录不再合用 | 找出哪些规则需要改，列出受影响的目录和迁移方案，确认后一起更新。 |

项目规范以根目录的 `AGENTS.md` 为入口。删除研究材料或判废结果需要你单独确认。日常开发、修 Bug、改算法或重写研究结论不属于这项技能的范围。

## 安装到 Codex

在终端运行以下命令，安装后可在本机的各个项目中使用：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/JZongf/research-repo-steward.git ~/.agents/skills/research-repo-steward
```

如果只想在一个项目中使用，把 `SKILL.md` 和 `agents/` 放到该项目根目录的 `.agents/skills/research-repo-steward/` 下即可。安装后如果找不到技能，重启 Codex。目录规则见 [Codex 技能文档](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills)。

## 怎么用

用 Codex 打开**你要整理的科研项目**，在对话中输入 `$` 并选择 `research-repo-steward`，然后说明你要做什么。例如：

```text
$research-repo-steward 帮我建立这个项目的目录和实验记录规范。先看看现状，有需要我决定的地方再问我。
```

```text
$research-repo-steward 按现有 AGENTS.md 整理这个仓库，把散落的实验结果放回对应位置。归属不明的先留在原处。
```

```text
$research-repo-steward 我们现在用统一入口运行实验。请找出需要更新的规则和路径，先给我迁移方案，暂时别改文件。
```

完整工作流程见 [SKILL.md](SKILL.md)。
