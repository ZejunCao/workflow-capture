# workflow-capture

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
3. 会话中根据 README 的“如何触发”示例话术来调用此 skill

**Claude Code 用户：**
```bash
/plugin marketplace add YOUR_USERNAME/workflow-capture
```

---

## 目录结构

```
workflow-capture/
├── README.md                        # 本文件（中文说明）
├── workflow-capture/
│   └── SKILL.md                     # 默认中文 skill
└── .claude-plugin/
    └── marketplace.json             # 插件市场配置
```

## License

MIT
