# 应用生态与 Agent 接口

**整理日期：** 2026-10-11；扩展限额于 2026-10-12 按开发文档复核。  
**范围：** Shopify 应用扩展与建站 SaaS 的产品设计参考。

## 已核实的事实

Shopify Sidekick app extensions 允许应用提供数据源和动作，让 Sidekick 能在管理流程中检索应用数据或导航到相应的应用界面。开发文档列出扩展类型、意图、工具、输入 schema、权限和运行时约束。应用动作由商家通过对应界面完成或参与；平台会对扩展进行策略检查。

官方文档当前说明每个应用最多 5 个 intents、20 个 tools，并有描述长度和响应时间等限制。限制可能更新，设计时应复查文档。

2026-10-12 打开的 Sidekick app extensions 页进一步写明：每个用户在一家店最多集成 20 个应用。扩展描述和 `extensions_summary` 各 256 token；instructions 2048 token；tool 名称 64 字符，描述 512 字符。查询字符串 500 字符。返回 4000 token。应用数据响应 1 秒，应用动作 3 秒。Discount intents 计入该应用的 intent 上限。

## 研究推论

1. Agent 生态不必要求每个应用一开始都开放任意写操作。搜索/解释、导航到应用、经商家确认后完成操作，可以逐级开放。
2. 工具说明、意图 schema、权限和目标界面共同影响 Agent 能否正确调用能力。
3. 建站 SaaS 可将应用能力作为受治理的扩展，而不是让 AI 生成代码绕过已有权限和业务流程。

## 行动建议

- 盘点应用能力时分为读取、建议、导航和写入，并分别定义授权与确认要求。
- 用结构化 schema 限制输入，校验实体和权限，再调用既有业务服务。
- 为工具说明保持短而具体；针对“找数据”“打开正确界面”“执行变更”分别设计任务测试。
- 评估协议适配时比较 MCP 工具、平台内扩展和普通深链各自的调用边界。
- 记录错误处理、幂等性、审计日志和撤销策略。

## 待验证事项

- Shopify Sidekick 扩展在不同商家套餐、地区及应用类别中的实际覆盖。
- Sidekick 工具调用中商家确认、权限和审计的具体运行时行为，需用开发店铺验证。
- 其他建站平台应用生态的 Agent 协议和生产可用性。

## 来源

- [Shopify Sidekick app extensions](https://shopify.dev/docs/apps/build/sidekick)（访问：2026-10-11；限额复核：2026-10-12）
- [Expose app actions to Sidekick](https://shopify.dev/docs/apps/build/sidekick/build-app-actions)（访问：2026-10-11）
