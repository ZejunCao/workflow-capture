# workflow-capture

**English** | [中文](#中文)

---

## English

### What is this?

A Claude Skill that does two things at once:
1. **Executes** your task step by step, pausing to ask you when things go wrong
2. **Captures** the entire process — including errors and fixes — into a reusable `SKILL.md` workflow file

Next time you need to do the same task, load the generated Skill and Claude follows the proven steps directly. No more trial and error.

### How to trigger it

Say something like:
- _"Help me set up X, and record the steps for next time"_
- _"Do this task and save it as a reusable workflow"_
- _"Capture this process as a skill"_
- _"Help me deploy X and document it"_

It will **not** trigger on regular tasks — only when you explicitly ask to record the process.

### What you get

After each session, Claude generates a `SKILL.md` file containing:
- ✅ Complete step-by-step instructions
- ⚠️ Common pitfalls with fixes (from real errors in your session)
- 🔧 Copy-paste commands and code snippets
- 📋 A troubleshooting table for every error encountered
- 🔄 Variant notes for different environments

### Installation

**Claude.ai users:**
1. Download `workflow-capture.skill` from [Releases](../../releases)
2. Upload it at the start of a Claude.ai conversation

**Claude Code users:**
```bash
/plugin marketplace add YOUR_USERNAME/workflow-capture
```

---

## 中文

### 这是什么？

一个 Claude Skill，同时完成两件事：
1. **执行**你的任务，逐步推进，遇到问题暂停询问你
2. **记录**整个过程——包括错误和修复——生成可复用的 `SKILL.md` 工作流文件

下次做同类任务时，加载生成的 Skill，Claude 就会直接按照验证过的步骤执行，不再走弯路。

### 如何触发

说类似这样的话：
- _"帮我做 X，并把步骤记录下来下次用"_
- _"做完这件事后生成一个可复用的工作流"_
- _"边做边记录，做完生成 skill"_
- _"帮我部署 X，把流程记录下来"_

普通任务**不会**触发——只有在你明确表示要记录过程时才会激活。

### 你会得到什么

每次会话结束后，Claude 生成一个 `SKILL.md` 文件，包含：
- ✅ 完整的逐步操作说明
- ⚠️ 常见坑及修复方法（来自你本次会话的真实错误）
- 🔧 可直接复制使用的命令和代码片段
- 📋 所有遇到错误的故障排查表
- 🔄 不同环境的变体说明

### 安装方式

**Claude.ai 用户：**
1. 从 [Releases](../../releases) 下载 `workflow-capture.skill`
2. 在 Claude.ai 对话开始时上传该文件

**Claude Code 用户：**
```bash
/plugin marketplace add YOUR_USERNAME/workflow-capture
```

### 多语言支持

- 英文版：[`workflow-capture/SKILL.md`](workflow-capture/SKILL.md)
- 中文版：[`i18n/SKILL.zh.md`](i18n/SKILL.zh.md)

Claude 会根据你使用的语言，自动用对应语言生成输出的工作流 Skill。

---

## File Structure | 目录结构

```
workflow-capture/
├── README.md                        # This file | 本文件
├── workflow-capture/
│   └── SKILL.md                     # English skill (default)
├── i18n/
│   └── SKILL.zh.md                  # 中文版 skill
└── .claude-plugin/
    └── marketplace.json             # Plugin marketplace config
```

## License

MIT
