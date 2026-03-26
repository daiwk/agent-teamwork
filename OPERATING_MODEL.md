# Operating Model

## Default Rule
这个仓库的**默认主入口就是 `project-pm`**。
也就是说，默认先做：
- 分析
- 拆任务
- 补文档
- 做归属判断
- 再决定是否进入实现

而不是一上来就直接修代码。

## Recommended Setup

### 1. Group chat only talks to the PM agent
项目群里只放一个 PM / orchestrator agent。
不要让 frontend / backend / algo 这些角色变成群里独立说话的 bot。

### 2. PM first, executor second
推荐顺序：
1. 读取 AGENTS.md 和 docs/project-brief.md
2. 更新 docs/*
3. 生成 tasks/*
4. 再调用 coding-agent 或 eng-executor 执行

### 3. `project-pm` is now the guarded default
如果你只是想让它保持 PM 身份，直接用默认主入口即可。
只有在任务清楚后，再进入执行模式。

### 4. Use `eng-executor` only after a task is ready
实现类工作应该基于任务单执行，而不是直接根据群消息裸奔。

## Suggested Prompts
- 先按 `project-pm` 模式处理，先不要写代码。
- 从 PM / tech lead 视角分析这个问题，更新任务单和验收标准。
- 任务单已准备好，现在可以调用 `eng-executor` 或 coding-agent 实现。

## Why this helps
这样可以避免主 agent 从 orchestrator 坍缩成直接修代码的执行器。
