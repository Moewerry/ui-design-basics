# UI 基础设计规范

`ui-design-basics` 是面向 Codex 和 Claude Code 的 UI 基础规范 Skill，用于优化现有界面，也可在新建页面时统一基础设计。

规范覆盖文案分隔、必要说明、文案质量、Radix Colors 配色、对齐与嵌套圆角、细边框、克制动效、字号层级、信息组织，以及圆角和阴影。完整规则见 [SKILL.md](./SKILL.md)。

默认保留业务功能，优先使用 shadcn/ui 和 Tailwind CSS；不适合时说明限制并询问替代方案。Skill 默认不启动项目、不执行构建、编译、测试或语法检测，只提供从项目配置确认的命令。

## 安装到 Codex

将下面这句话发给 Codex，由它使用 skill-installer 安装仓库根目录的 Skill：

```text
请使用 skill-installer 安装 https://github.com/Moewerry/ui-design-basics 仓库根目录的 Skill，名称为 ui-design-basics。
```

也可手动克隆。以下是 Windows PowerShell 命令；如果设置了 CODEX_HOME，请使用该目录下的 skills 文件夹：

```powershell
New-Item -ItemType Directory -Path "$env:USERPROFILE/.codex/skills" -Force | Out-Null
git clone https://github.com/Moewerry/ui-design-basics.git "$env:USERPROFILE/.codex/skills/ui-design-basics"
```

macOS / Linux：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/Moewerry/ui-design-basics.git "${CODEX_HOME:-$HOME/.codex}/skills/ui-design-basics"
```

安装后在下一轮对话中调用：

```text
$ui-design-basics 优化当前页面的 UI，保留业务功能。
```

## 安装到 Claude Code

克隆到个人 Skills 目录，供所有项目使用。Windows PowerShell：

```powershell
New-Item -ItemType Directory -Path "$env:USERPROFILE/.claude/skills" -Force | Out-Null
git clone https://github.com/Moewerry/ui-design-basics.git "$env:USERPROFILE/.claude/skills/ui-design-basics"
```

macOS / Linux：

```bash
mkdir -p "$HOME/.claude/skills"
git clone https://github.com/Moewerry/ui-design-basics.git "$HOME/.claude/skills/ui-design-basics"
```

在 Claude Code 中调用：

```text
/ui-design-basics 优化当前页面的 UI，保留业务功能。
```

目录规则和调用方式见 [Claude Code 官方 Skills 文档](https://code.claude.com/docs/en/skills)。如只希望当前项目使用，可将此仓库克隆到项目的 `.claude/skills/ui-design-basics`。

安装目标目录已存在时，不要覆盖本地改动；如该目录已是本仓库的克隆，可先检查 `git status`，确认没有改动后执行 `git pull --ff-only` 更新。

## 仓库结构

```text
ui-design-basics/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── .gitignore
└── README.md
```

仓库仅分发 UI 基础设计规范，不包含 `Moewerry/skills` 仓库的 `git-commit`、`git-push` 或本地安装目录。使用本 Skill 不需要安装这两个 Git Skill。
