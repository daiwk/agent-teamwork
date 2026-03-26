# Operating Model

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

### 3. Use `project-pm-guarded` for planning and triage
当你希望它保持 PM 身份时，优先触发这个 skill。

### 4. Use `eng-executor` only after a task is ready
实现类工作应该基于任务单执行，而不是直接根据群消息裸奔。

## Suggested Prompts
- 先按 `project-pm-guarded` 模式处理，先不要写代码。
- 从 PM / tech lead 视角分析这个问题，更新任务单和验收标准。
- 任务单已准备好，现在可以调用 `eng-executor` 或 coding-agent 实现。

## Why this helps
这样可以避免主 agent 从 orchestrator 坍缩成直接修代码的执行器。
