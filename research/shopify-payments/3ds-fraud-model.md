# Shopify Payments：3DS 与欺诈处理

**整理日期：** 2026-10-12  
**范围：** Shopify 官方支付与订单风控页面，以及当天打开的两家三方应用商店页。效果数字均标明「页面如此写」。

## 已核实的事实

Shopify 文档把持卡人认证、成单后的风险建议、拒付报销和商家规则分成不同页面，没有写成一个模型。

### 动态 3DS

PSD2 帮助页（2026-10-12）页面如此写：

- PSD2 于 2019-09-14 在欧洲经济区和英国实施。使用 Shopify Payments 的集成 3D Secure 结账即符合 PSD2。该页另写有 18 个月过渡期。
- 3D Secure 在结账时把用户转到发卡行域名，再回到店铺完成支付。认证成功后，欺诈拒付责任从商家转到发卡行。发卡行政策可以取消这种保护。页面举例：Visa 规定商家单月欺诈拒付超过 7500 美元后，不能再把责任转给发卡行。
- 使用 Shopify Payments 或 Stripe 时自动走 3D Secure 结账。Shopify Payments 会尽量少用 3D Secure，只在发卡行为了完成授权而要求时使用。
- 使用其他网关且需要 3D Secure 时，可以使用 Cardinal。

工程博客《How Shopify Payments Uses Machine Learning…》（作者 Frans van Coller，页面日期 2025-05-21，于 2026-10-12 打开）写的触发方式与上面并列，不合并：

- 2025 年 1 月实验用预授权模型决定何时发起 3DS。页面如此写：支付成功率提高 26 个基点；被发卡行标为欺诈的拒付下降 20%（在 41 个基点的基数上减少 8 个基点）。
- 页面如此写：若该模型在 2024 年已生效，会多出 4.71 亿美元年度支付总额，并为商家省下 6200 万美元拒付相关成本。这是该页的外推。
- 页面如此写：基于该结果，已对全部 Shopify Payments 商家实施。模型查看从进站、浏览、加购到结账的路径，把高风险交易送进 3DS。发卡行可以免验通过，或要求持卡人再认证。
- 同一页另写：放开僵硬的 AVS 控制后，Shopify 商家多处理 0.33% 的交易。

Preventing fraud（2026-10-12）把 Dynamic 3DS 写成：使用 Shopify Payments 的店铺可用。该表对 PSD2 地区的描述是：位于 PSD2 地区且使用 Shopify Payments 时自动使用 3DS，并且只在发卡行要求时使用。这与 PSD2 帮助页一致，与 2025-05-21 工程博客的「模型把高风险交易送进 3DS」仍然并列。

### 订单欺诈分析

Fraud analysis 帮助页（2026-10-12）页面如此写：这是成单后的检查。信用卡机构在发货后仍可撤销被盗卡资金。撤销由发卡行决定，不是 Shopify。Shopify 不承担银行的资金撤销。

- 欺诈指标，以及对三方防欺诈应用的支持：Basic 及以上。
- 欺诈建议：Grow 及以上，或使用 Shopify Payments。
- 适用于 Shopify 能够核验的在线信用卡订单。
- 没有欺诈建议的订单包括：测试单、免费单、礼品卡全额支付、POS、B2B、订阅续费。
- 建议分为 low / medium / high。下一步可以是可以发货、发货前与顾客确认，或考虑取消。
- 指标可以包括 AVS、CVV、顾客位置与支付方式是否一致、异常设备或网络、是否尝试了不止一张卡。单个指标不等于整单风险。
- 模型用全部 Shopify 店铺的历史交易训练，并持续更新。页面如此写。
- Shopify Payments 可以在订单创建前拦住部分高风险结账。被拦的尝试出现在 Orders > Abandoned checkouts 的 Blocked 视图，没有订单级欺诈建议。
- 三方应用的指标和建议可以与 Shopify 的欺诈分析一起显示在订单上。

Preventing fraud 同一页还列出、且与 3DS 分开的工具：Shopify Flow（Basic、Grow、Advanced、Plus，或使用 Shopify Fulfillment Network）、卡测试防护、拒付处理、代理检测、Plus 上的授权率优化、非 Shopify Payments 店铺的收款时机控制。

### Shopify Protect 与 Fraud Control

这两页都没有把自身写成 3DS 评分模型。

Shopify Protect 帮助页（2026-10-12）页面如此写：符合条件且受保护的订单发生欺诈拒付时，报销拒付金额和拒付费，争议由 Shopify 处理。只保护全部为需配送实物的订单；含数字商品，或线上购买、到店自提的订单不受保护。订阅只覆盖首单，后续续费不受保护。所有未退款行项目须为 Fulfilled。只适用于经 Shop Pay 处理的订单，包括 Facebook、Instagram、Google 上的 Shop Pay；Shop Pay Installments 不符合。经 Shopify Payments 处理的 Managed Markets 订单自动受保护。店铺须在美国，并使用美国的 Shopify Payments 账户。须在下单后 7 天内用支持的承运商提供有效物流号，且承运商在下单后 10 天内标为在途。结账后修改收货地址会使该单失去保护。支持的承运商包括 SFN、USPS、UPS、Canada Post、DHL Express、FedEx 等，该页有完整名单。

Fraud Control 帮助页（2026-10-12）页面如此写：不保证覆盖拒付。它提供潜在欺诈的信息，不主动保护，拒付成本由商家承担。在 Shopify Payments 可用的地区，所有套餐可安装；部分数据只有使用 Shopify Payments 才有。结账规则仅 Shopify Payments 可用，可按邮箱、地址属性和 IP 拦截，拦截后结账不会成为订单。页面写明规则不能保证不再收到欺诈订单。

### 三方应用页

Signifyd 应用页（2026-10-12）页面如此写：结账时即时批准或拒绝，并对已批准订单的欺诈拒付提供财务担保。同一页的要点又写「对欺诈和非欺诈拒付提供全面保护」。另有退货保护。页面列出的协作对象包括 Shop Pay、PayPal、Stripe Early Fraud Warnings。安装免费，可能另有费用。该页没有写它是否发起或替代 3DS。

Riskified 应用页（2026-10-12）页面如此写：实时欺诈决定，并提供拒付保证。要点中写「每笔交易享有完整拒付保护」。另有退货滥用识别和拒付管理。安装免费，可能另有费用。该页没有写它是否发起或替代 3DS。

## 研究推论

1. 产品里应把三层分开：3DS 决定这笔授权要不要做持卡人认证；欺诈分析决定成单后发不发货，且官方写明不赔付；Shopify Protect 是资格规则下的报销，不是评分。
2. 帮助中心的「只在发卡行要求时使用 3DS」和工程博客的「模型把高风险交易送进 3DS」不能收成一条触发规则。在官方把两页对齐之前，对外应并列引用。
3. Signifyd 与 Riskified 的应用页把财务担保写在自己的批准结果上。订单帮助页写的是三方评估与 Shopify 欺诈分析并列显示。由此推出：它们补的是批准和拒付责任，不是帮助页里的 3DS 结账流程。两家应用页没有写是否替代 3DS，所以这句不是「它们不处理 3DS」的官方结论。

## 行动建议

- 支付方案按层验收：认证触发、成单后建议、报销资格、商家规则。不要用一个「欺诈模型」开关覆盖四层。
- 对 3DS，同时保留两份官方说法，直到 Shopify 自己写成同一条规则。效果数字只引用带来源的页面，并保留「页面如此写」。
- 若接入担保类应用，合同范围和订单页上的并列评估分开记录。应用商店文案里的「每笔交易」不直接写成已替代 Shopify Protect 或 3DS。

## 待验证事项

- 工程博客的预授权模型，与帮助中心「只在发卡行要求时使用 3DS」，在同一笔交易上如何同时成立。两页冲突，本次不合成。
- Signifyd 页同时写「已批准订单的欺诈拒付担保」和「欺诈与非欺诈拒付的全面保护」。担保到底覆盖哪些争议类型，应用页没有对齐，需看合同。
- Riskified 页写「每笔交易的完整拒付保护」。是否包含非欺诈争议、以及未批准订单，该页没有写清。
- 这两家应用是否会自己发起 3DS：应用页没有写。NoFraud / Wyllo 本次没有打开页面，不记入事实。
- Shopify Protect 营销页 https://www.shopify.com/protect 本次没有单独打开；资格以帮助中心页为准。

## 来源

- [Understanding PSD2 and 3D Secure Checkout](https://help.shopify.com/en/manual/payments/shopify-payments/transactions/psd2-and-3d-secure-checkout)（访问：2026-10-12）
- [How Shopify Payments Uses Machine Learning to Boost Payment Success Rates by 0.26% and Cut Fraud Chargebacks by 20%](https://www.shopify.com/enterprise/blog/shopify-payments-pre-authorization)（页面日期 2025-05-21；访问：2026-10-12）
- [Preventing fraud](https://help.shopify.com/en/manual/payments/fraud-prevention/preventing-fraud)（访问：2026-10-12）
- [Reviewing orders with fraud analysis](https://help.shopify.com/en/manual/fulfillment/managing-orders/protecting-orders/fraud-analysis)（访问：2026-10-12）
- [Protecting an order with Shopify Protect](https://help.shopify.com/en/manual/payments/shop-pay/shopify-protect/protect-order-with-shopify-protect)（访问：2026-10-12）
- [Fraud Control app](https://help.shopify.com/en/manual/payments/fraud-prevention/fraud-control-app)（访问：2026-10-12）
- [Signifyd](https://apps.shopify.com/signifyd)（访问：2026-10-12）
- [Riskified](https://apps.shopify.com/riskified)（访问：2026-10-12）
