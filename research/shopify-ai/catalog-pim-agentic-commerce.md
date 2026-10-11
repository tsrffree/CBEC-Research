# Catalog、PIM 与 Agent Commerce

**整理日期：** 2026-10-11  
**资料类型：** 官方事实与产品推论分列。Shopify 接口和日期应以更新日志为准。

## 已核实的事实

### Global Catalog MCP 与 UCP

Shopify Global Catalog MCP 用于跨多个 Shopify 商家的商品发现，实现 UCP Catalog 能力。官方文档列出 `search_catalog`、`lookup_catalog` 和 `get_product` 等工具。单店 Agent 应区分使用 Storefront Catalog，而非把 Global Catalog 当成唯一入口。

### 推断数据与商家原始数据

官方将部分全局 Catalog 字段标记为 `Inferred`，例如商品描述、标准化选项、属性、技术规格和卖点。这些字段可能缺失或精度不一，应视为发现和营销信号，而不是商家撰写的原始事实。

建议数据分层：

- **Merchant source**：商家提交并维护的原始数据。
- **AI enrichment**：系统生成或标准化的补充数据，附来源和时间。
- **Verified data**：经过商家或规则审核的数据，可用于高风险展示或交易决策。

### 迁移与价格字段

- Shopify 公告称 Global Catalog REST API 于 **2026-11-02** 停止服务，旧请求将失败；官方将 Global Catalog MCP 作为替代方向。
- Shopify Catalog 更新说明增加 compare-at price 对应的 `list_price`。输出受商家共享设置、价格关系及买家地区规则限制；不能假设所有商品或地区均返回此字段。

## 研究推论

1. Agent-ready 商品数据不只是标题、图片和售价，还需要变体、可售性、地区/币种、发货范围、条件和可信来源。
2. 把 AI 推断值混入商家原始字段会带来误导、质量回溯和责任归属风险。
3. 商业协议适配宜放在独立映射层，避免为单一平台私有接口重构核心 PIM。

## 行动建议

- 做商品、变体、价格、库存、市场、税费/配送条件到 Agent schema 的映射盘点。
- 输出价格时保留币种、买家上下文和“原价/比较价”语义，禁止 Agent 自行推断真实折扣。
- 为 AI 补充数据提供置信度、来源、审核和过期策略。
- 先做只读搜索与详情能力验证，再根据需求评估购物车和交易动作。
- 设计协议发现、能力协商、版本兼容和未知字段容错。

## 待验证事项

- 2026-11-02 停服计划之后实际迁移情况及可能的公告变更。
- 不同市场下 `list_price` 的完整资格条件及显示法律要求。
- UCP 规范的后续版本与 Shopify 扩展字段差异。
- 自有商品中心现状和字段覆盖率；本文未访问内部系统，建议由产品团队补充。

## 官方来源

- [Global Catalog MCP 文档](https://shopify.dev/docs/agents/catalog/global-catalog)（访问：2026-10-11）
- [Global Catalog REST API 停服公告](https://shopify.dev/changelog/posts/global-catalog-rest-api-stops-serving-traffic-on-november-2-2026)（访问：2026-10-11）
- [Catalog API 返回 compare-at price 为 list_price](https://shopify.dev/changelog/posts/catalog-api-now-returns-compare-at-prices-as-list_price)（访问：2026-10-11）
- [Universal Commerce Protocol](https://ucp.dev/)（协议主页；访问：2026-10-11）
