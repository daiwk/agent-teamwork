# agent-teamwork

一个面向 **OpenClaw + coding-agent + 多角色协作** 的最小模板仓库。

目标不是让多个 bot 在群里开会，而是让**一个项目 PM agent**负责：
- 读项目文档
- 拆任务
- 分配 frontend / backend / algo 归属
- 在任务清楚后，再调用 `coding-agent` 或 `eng-executor` 做实现

## Recommended Structure

- `AGENTS.md`: 项目主规则。默认主入口是 PM / orchestrator
- `docs/`: 项目文档与 contract
- `tasks/`: 任务单
- `.openclaw/skills/project-pm/`: 默认 PM skill
- `.openclaw/skills/eng-executor/`: 实现执行 skill
- `.openclaw/skills/frontend-lead|backend-lead|algo-lead/`: 角色分析 skill

## Recommended Usage

### 1. 项目群里只和 PM agent 说话
不要让 frontend / backend / algo 角色变成群里独立发言的 bot。

### 2. 默认先走 PM 模式
推荐先让主 agent：
1. 读取 `AGENTS.md` 和 `docs/project-brief.md`
2. 更新 `docs/*`
3. 生成或更新 `tasks/*`
4. 再决定是否调用执行器

### 3. 执行阶段再调用 eng-executor / coding-agent
实现类工作尽量基于任务单执行，而不是直接根据群消息裸奔。

## Suggested Prompts

```text
先按 project-pm 模式处理。读取 AGENTS.md、docs/project-brief.md 和现有 tasks。先不要直接改代码，先拆任务、定归属、补验收标准。
```

```text
从 PM / tech lead 视角分析这个问题：影响哪些模块、该分给谁、要补哪些任务单。先不要直接修代码。
```

```text
任务单已经准备好，现在可以调用 eng-executor 或 coding-agent 实现。
```

## Why this repo exists

这个模板主要用来解决一个常见问题：
**主 agent 很容易从项目经理坍缩成直接修代码的执行器。**

这里的结构和 skill 设计，就是为了把“规划/分派”和“实现/验证”拆开。
