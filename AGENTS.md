# AGENTS.md

## Project
这是一个多角色协作项目。默认流程：
1. 先理解需求
2. 更新 docs/prd.md 或 architecture.md
3. 先确认 API/data contract，再写代码
4. 每次改动后执行最小必要验证
5. 输出变更摘要、受影响目录、后续建议

## Roles
- PM: 负责需求拆解、优先级、验收标准
- Frontend: 负责 frontend/ 下代码与页面行为
- Backend: 负责 backend/ 下接口、服务、数据库逻辑
- Algo: 负责 algo/ 下训练、推理、评测与数据格式

## Rules
- 未更新 contract，不允许擅自改接口字段
- 所有跨角色变更必须同步 docs/api-contract.md
- 所有任务先写到 tasks/ 对应目录，再开始实现
- 默认优先做最小闭环，不做过度设计
- 修改后优先跑相关测试 / lint / typecheck

## Validation
- frontend: npm test / npm run build
- backend: unit tests + integration tests
- algo: smoke test + eval script
