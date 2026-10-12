# Shopify AI 能力地图

**整理日期：** 2026-10-11；Sidekick 与文案入口于 2026-10-12 补入。  
**范围：** Shopify 官方能力及与建站 SaaS 产品设计相关的研究结论。功能状态可能变化，引用来源为官方文档或更新日志。

## 已核实的事实

| 能力层 | 事实与当前状态 | 产品关联 |
|---|---|---|
| 商品发现 | Global Catalog MCP 面向跨商家商品发现，实现 UCP Catalog 能力，并提供搜索、标识查询和商品详情工具。 | 商品中心需要支持面向 Agent 的发现、筛选、变体选择和上下文信息。 |
| 商品数据可信度 | Shopify 标记部分 Catalog 字段为 Inferred，包括描述、标准化选项、属性、技术规格和卖点；官方建议把它们视为发现/营销信号，而非商家原始内容。 | 来源、置信度和审核状态应成为商品数据模型的一部分。 |
| AI 搜索 | Shopify 帮助文档将语义搜索列为 Search & Discovery 的 AI 搜索行为，利用相关词、概念、类别和上下文扩展搜索结果。 | 需要同时考虑词面查询、意图和可解释的筛选。 |
| 应用接入 | Sidekick 扩展可提供应用数据或带范围的动作；文档要求声明意图、权限和工具，商家仍参与更新流程。 | Agent 入口可以复用成熟业务应用，动作需受权限与确认机制约束。 |
| Agent Commerce | Global Catalog MCP 使用 UCP Catalog 能力；协议与工具结构公开定义。 | 适配层应考虑协议能力发现和版本兼容。 |

### Sidekick 与文案入口（2026-10-12）

帮助中心将 Sidekick 写成 Shopify 后台里的 AI 商业助手。页面如此写：包含在套餐内，功能和用量随套餐变化。两种用法：对话完成任务，或在 Home 上由 Sidekick Pulse 给出建议。它使用当前页面作为上下文，权限与登录员工一致；变更先展示，商家确认后才应用到店铺。

帮助中心列出的任务包括：分析数据、管理订单、编辑商品；生成博客、商品描述和图片；生成自定义应用。较长任务可以在离开对话后继续，完成后再通知审核。重复提示可以存成 skill。桌面、Shopify App 和平板可用文字、语音和屏幕共享。Apple Watch 可以用语音提问。

帮助中心列出的边界：

- 不能代替客服与顾客对话，也不能分享其他商家的数据。
- 不能在未经批准时修改店铺。
- 不能编辑主题内的图片，也不能编辑商品列表中的图片。
- 手机浏览器中的 Shopify 后台没有 Sidekick。手机和平板需在 Shopify App 中打开。
- Shopify App 内，弹层盖住主屏时不可用；帮助中心举例包括 Discounts，以及 Products、Collections 上的部分任务。手机上，Online Store Editor 里的 Sidekick 布局和选项与其他页面不同。平板的 Online Store Editor 中没有 Sidekick。
- Apple Watch 可以回答未发货订单、当日销售和低库存。它不能修改店铺，也不能在后台中导航。
- 桌面可以在 Sidekick 尚未回复完时排队下一条消息。该选项在 Shopify App 和部分店铺不可用。页面如此写。

Shopify Magic 帮助页把另一组 AI 与 Sidekick 分开。页面如此写：部分功能没有针对移动设备优化。商家可以把店铺接到 ChatGPT、Claude、Gemini、Grok、Muse 或 Perplexity，并控制访问范围。同一页列出的其他入口包括：Inbox 回复建议、文件编辑器替换图片背景、按业务描述生成免费主题、商品类目建议、Search & Discovery 的筛选值排序、客户分群说明、客户 cohort 的消费预测、App Store 部分应用的评价摘要。Tinker 在该页被写成免费移动应用，用于图片、视频和品牌素材。

应用商店「Shopify Magic for product descriptions」页（2026-10-12）页面如此写：支持商品描述、博客、AI 生成、语气和 Blog SEO。不支持标题、SEO 描述、SEO 标题、alt、图片、视频、标签、变体、产品系列描述、FAQ、社交帖、评价、结构化数据、提示词模板、多语言、翻译、批量编辑、导入导出、自动更新和排期。这与 Sidekick 帮助中心「可以生成商品描述、博客、页面、邮件、主题编辑器文字和图片」是两页各自的范围，不合并成一条「原生文案覆盖哪些字段」。

## 研究推论

1. AI 电商能力正在从内容生成扩展至商品发现、数据解释和跨应用执行。
2. 建站平台的长期差异化，可能从模板数量转向生成后的业务正确性、数据可信度、应用兼容和可持续维护。
3. Agent 接口会提高商品语义、价格上下文、权限范围和版本兼容的基础设施价值。
4. 对标 Shopify 文案能力时，应按入口拆开：内联 Magic 商品描述页和 Sidekick 对话页写的字段范围不同。把它们说成同一种「Shopify AI 文案」会漏掉不支持的字段。

## 行动建议

- 建立商品/变体/价格/库存/市场字段到 Agent 输出的映射表。
- 对 AI 补充内容保留来源、生成时间、审核状态和商家原始值。
- 将页面生成、业务运行时、应用扩展和发布校验作为协同设计的问题。
- 按官方更新日志维护产品状态，不将研究预览或地区限制功能描述为普遍上线。
- 文案能力按入口列字段：描述正文、SEO、图片、批量和翻译分开验收，不按「能写商品描述」一次通过。

## 待验证事项

- Sidekick 帮助中心写了可生成商品描述和图片，Magic 商品描述应用页写了不支持 SEO 标题、图片和批量。Sidekick 实际写入哪些字段，两页没有对上，不能合成一句。
- Canvas 的首发限制见主题边界文档。各店后台是否已经出现 Canvas 入口，changelog 写的是逐步开放，本次没有在店铺里核对。
- 批量文案类三方应用本次没有逐页打开，不记入事实。
- 七大建站平台及第三方应用的上线状态、套餐限制和实际交付质量。
- UCP 版本更新对各类客户端和商品字段兼容性的实际影响。

## 来源

- [Shopify Global Catalog MCP](https://shopify.dev/docs/agents/catalog/global-catalog)（访问：2026-10-11）
- [Shopify Sidekick app extensions](https://shopify.dev/docs/apps/build/sidekick)（访问：2026-10-11）
- [Shopify storefront search](https://help.shopify.com/en/manual/online-store/search-and-discovery/search)（访问：2026-10-11）
- [Shopify UCP Catalog capability](https://ucp.dev/specification/overview)（官方协议入口；具体规范以当前版本为准）
- [Shopify Help Center | Sidekick](https://help.shopify.com/en/manual/ai-powered-tools/sidekick)（访问：2026-10-12）
- [Getting started with Sidekick](https://help.shopify.com/en/manual/ai-powered-tools/sidekick/set-up)（访问：2026-10-12）
- [AI-powered tools](https://help.shopify.com/en/manual/ai-powered-tools/shopify-magic)（访问：2026-10-12）
- [Shopify Magic for product descriptions](https://apps.shopify.com/built-in-features/magic-product-descriptions)（访问：2026-10-12）
