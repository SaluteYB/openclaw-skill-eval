# OpenClaw 的 skill-eval

[![Release](https://img.shields.io/github/v/release/SaluteYB/openclaw-skill-eval)](https://github.com/SaluteYB/openclaw-skill-eval/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![CI](https://img.shields.io/github/actions/workflow/status/SaluteYB/openclaw-skill-eval/package-skill.yml?branch=main&label=package)](https://github.com/SaluteYB/openclaw-skill-eval/actions/workflows/package-skill.yml)

一个用于**评估其他技能**的小型开源 AgentSkill。

`skill-eval` 的目标，是把“这个 skill 看起来还行”变成一套**轻量、可重复、可回归**的评估流程：

- 应触发样本
- 不应触发样本
- 边界案例
- 执行质量检查
- 简短回归日志

它面向 OpenClaw / Codex 风格的 skill 工作流设计，但整体结构也可以迁移到别的 AgentSkill 体系里。

English version: [README.md](./README.md)

## 为什么要做这个

大多数 skill 出问题，通常就两类：

1. **触发问题**：该触发时没触发，不该触发时乱触发。
2. **执行问题**：触发是对的，但工作流太虚、太脆、太不稳定。

这个 skill 的意义，就是把这两类问题拆开检查。

## 仓库结构

```text
openclaw-skill-eval/
├── skill-eval/
│   ├── SKILL.md
│   ├── references/
│   │   └── evaluation-patterns.md
│   └── assets/
│       └── examples/
│           ├── should-trigger.md
│           ├── should-not-trigger.md
│           ├── boundary-cases.md
│           ├── execution-checklist.md
│           └── evaluation-log.md
├── .github/workflows/
├── README.md
├── README.zh-CN.md
├── LICENSE
└── .gitignore
```

## 这个 skill 适合什么时候用

当你在创建或优化另一个 skill，并且希望：

- 收紧触发描述
- 审计相邻 skill 的冲突
- 定义最低执行质量标准
- 给每轮优化留下简短评估记录

就用它。

## 推荐用法

1. 先读目标 skill 的 `SKILL.md`
2. 在目标 skill 内部或旁边新建一个 `eval/` 目录
3. 复制 `skill-eval/assets/examples/` 里的示例文件
4. 填写真实用户风格的：
   - 应触发
   - 不应触发
   - 边界案例
5. 补执行检查项
6. 修改目标 skill
7. 回测一小组代表样本
8. 记录这一轮改了什么

## 快速示例

假设你正在优化一个 `video-subtitle` skill。

### 应触发

- “把这个 SRT 整体提前 1.2 秒。”
- “清理这个字幕文件，把断开的句子合并一下。”
- “把这个 VTT 转成干净的 SRT。”

### 不应触发

- “把这个 MP4 压到 50MB 以内。”
- “把这批素材按相机和日期整理文件夹。”
- “给这个视频写 3 个 YouTube 标题。”

### 边界案例

- “把这个采访视频提取音频并准备成可做字幕的格式。”
  - 预期技能：`video-subtitle`
  - 原因：核心产物是字幕/转录准备，而不是通用导出。

## 安装方式

### 方案 A：下载 `.skill` 包

直接从 [Releases](https://github.com/SaluteYB/openclaw-skill-eval/releases) 页面下载最新的 `skill-eval.skill`。

### 方案 B：直接使用仓库目录

把 `skill-eval/` 目录复制到你的 skills 目录或本地 skills 集合里。

## 本地打包

如果当前环境里有 OpenClaw 自带的 `skill-creator` 打包脚本，可以这样打包：

```bash
python3 /usr/local/lib/node_modules/openclaw/skills/skill-creator/scripts/package_skill.py ./skill-eval ./dist
```

正常会在 `dist/` 下生成一个 `.skill` 包。

## 示例

- [`examples/video-subtitle-eval/`](./examples/video-subtitle-eval/) —— 一个真实示例，展示应触发、不应触发、边界案例和一轮评估日志。

## 自动化

仓库现在包含两条 GitHub Actions 工作流：

- `package-skill.yml` —— 在 push / PR 时自动校验并打包 skill
- `release-skill.yml` —— 当你推送 `v*` tag 时，自动构建并发布 `skill-eval.skill`

## 路线图

- 补更多常见 skill 类型的示例评估集
- 增加可选评分表 / 通过标准
- 给真实 skill 提供评估示例目录

## 许可证

MIT
