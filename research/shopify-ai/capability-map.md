# Shopify AI 能力地图

**整理日期：** 2026-10-11  
**范围：** Shopify 官方能力及与建站 SaaS 产品设计相关的研究结论。功能状态可能变化，引用来源为官方文档或更新日志。

## 已核实的事实

| 能力层 | 事实与当前状态 | 产品关联 |
|---|---|---|
| 商品发现 | Global Catalog MCP 面向跨商家商品发现，实现 UCP Catalog 能力，并提供搜索、标识查询和商品详情工具。 | 商品中心需要支持面向 Agent 的发现、筛选、变体选择和上下文信息。 |
| 商品数据可信度 | Shopify 标记部分 Catalog 字段为 Inferred，包括描述、标准化选项、属性、技术规格和卖点；官方建议把它们视为发现/营销信号，而非商家原始内容。 | 来源、置信度和审核状态应成为商品数据模型的一部分。 |
| AI 搜索 | Shopify 帮助文档将语义搜索列为 Search & Discovery 的 AI 搜索行为，利用相关词、概念、类别和上下文扩展搜索结果。 | 需要同时考虑词面查询、意图和可解释的筛选。 |
| 应用接入 | Sidekick 扩展可提供应用数据或带范围的动作；文档要求声明意图、权限和工具，商家仍参与更新流程。 | Agent 入口可以复用成熟业务应用，动作需受权限与确认机制约束。 |
| Agent Commerce | Global Catalog MCP 使用 UCP Catalog 能力；协议与工具结构公开定义。 | 适配层应考虑协议能力发现和版本兼容。 |

## 研究推论

1. AI 电商能力正在从内容生成扩展至商品发现、数据解释和跨应用执行。
2. 建站平台的长期差异化，可能从模板数量转向生成后的业务正确性、数据可信度、应用兼容和可持续维护。
3. Agent 接口会提高商品语义、价格上下文、权限范围和版本兼容的基础设施价值。

## 行动建议

- 建立商品/变体/价格/库存/市场字段到 Agent 输出的映射表。
- 对 AI 补充内容保留来源、生成时间、审核状态和商家原始值。
- 将页面生成、业务运行时、应用扩展和发布校验作为协同设计的问题。
- 按官方更新日志维护产品状态，不将研究预览或地区限制功能描述为普遍上线。

## 待验证事项

- Shopify Magic、Horizon、Canvas 等能力在各计划、地区和主题上的当前可用范围。
- 七大建站平台及第三方应用的上线状态、套餐限制和实际交付质量。
- UCP 版本更新对各类客户端和商品字段兼容性的实际影响。

## 来源

- [Shopify Global Catalog MCP](https://shopify.dev/docs/agents/catalog/global-catalog)（访问：2026-10-11）
- [Shopify Sidekick app extensions](https://shopify.dev/docs/apps/build/sidekick)（访问：2026-10-11）
- [Shopify storefront search](https://help.shopify.com/en/manual/online-store/search-and-discovery/search)（访问：2026-10-11）
- [Shopify UCP Catalog capability](https://ucp.dev/specification/overview)（官方协议入口；具体规范以当前版本为准）
