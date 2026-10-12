# AI 建站与主题模板的替代边界

**整理日期：** 2026-10-11；主题生成入口于 2026-10-12 补入。  
**性质：** 产品研究判断；不是 Shopify 对未来的承诺或行业定量预测。

## 核心判断

AI 会降低静态视觉内容和常规页面搭建的制作成本，但页面可生成不代表业务可安全运行。产品架构应把生成、编辑、交易执行、应用扩展和发布校验连成可持续流程。

## 已核实的事实

帮助中心 Adding themes（2026-10-12）把「用自己的话描述业务，生成免费个性化主题」列为添加主题的一种方式。页面如此写：一次最多生成 3 套；选中后进入 Draft themes。店面语言为英文时，新生成只在免费试用或 Basic、Grow、Advanced 上可用。Starter 只能使用 Spotlight，不能生成。Plus 没有出现在这句资格说明里，该页没有另写 Plus 可以或不可以。违反 Shopify 政策的主题不能用于生成。该页另写：不支持、也不认可从网上上传图片或侵犯版权。

同一页对已有店铺的新生成写明：使用 Shopify App 进入 Online Store，或用手机浏览器打开后台。原文：You can no longer generate one from the desktop Shopify admin。以前生成的免费个性化主题仍留在 Themes 页，可以在桌面浏览器中预览并加入店铺。该页没有写撤下桌面入口的原因。

Sidekick 生成 theme block 的帮助页（2026-10-12）页面如此写：在主题编辑器中按描述生成 block。试用、Basic、Growth、Advanced、Plus 可用；Starter 不可用。Theme Store 上的主题可用；兼容的三方主题须先购买，试用版不支持；vintage 主题不可用。店主、组织所有者、管理员，或带 Edit Code 权限的店铺角色可以生成。提示至少 5 个词。保留后，新的 Liquid 文件进入主题的 blocks 目录。Shopify Support 和三方主题开发者不支持排查这段生成代码的问题。

Changelog「Online Store Editor with Sidekick on mobile」页面日期 2026-06-17：手机在线商店编辑器重建，Sidekick 进入该编辑器。可选中区块后出现已带上下文的 Sidekick 输入。

Changelog「Design a fully bespoke store with Canvas」页面日期 2026-10-01：Canvas 是新的设计面，可直接编辑元素，或让 Sidekick 在对话中修改，变更实时出现。页面如此写：对已有店铺在接下来数天内逐步开放；入口是 Online Store > Themes，可新建 Canvas 主题，或把 Shopify 主题、自定义主题复制进 Canvas；原主题仍留在现有主题编辑器。首发不支持 Theme Store 的三方主题、Markets、rollouts、翻译、app blocks 和 app embeds。在 Canvas 中编辑过的主题不接收主题更新。

Introducing Canvas 新闻稿页面日期 2026-10-01，于 2026-10-12 打开。页面如此写：Sidekick 在 2026 年上半年对主题做了超过 2500 万次编辑；Canvas 尚未替换现有编辑器。这是新闻稿数字和产品表述，不是帮助中心的能力边界。

Adding themes 页的套餐用词是 Grow。生成 block 的帮助页用词是 Growth。两页没有对成同一个套餐名。

## 能力边界

| 页面/能力类型 | 当前研究判断 | 主要验证点 |
|---|---|---|
| Banner、品牌展示、静态内容区块、活动落地页 | 适合作为 AI 生成和快速迭代的优先场景。 | 品牌一致性、响应式表现、可编辑性、无障碍和加载表现。 |
| 商品详情交互、复杂导航、筛选与搜索 | AI 可辅助创建，但应依赖经过验证的标准组件或受约束的生成方式。 | 变体选择、库存与价格同步、可访问性、移动端交互。 |
| 第三方应用、多市场、结账与交易 | 需要平台运行时、权限和扩展协议保障。 | 应用兼容、市场上下文、错误恢复、数据权限和版本迁移。 |
| 商品语义、数据绑定、交易执行、版本发布 | 应保留标准化底座；AI 可以调用和配置，但不应由每个店铺重复重造关键逻辑。 | 可追溯、可测试、可回滚、向后兼容。 |

## 研究推论

竞争焦点可能从“提供多少模板”转向“AI 生成后能否继续编辑，并保证业务正确、应用兼容和长期维护”。这是基于已观察到的 AI 生成、Agent 商品发现和应用扩展方向的产品推论。

2026-10-12 的页面同时存在三条生成路径：手机或手机浏览器上的整站主题生成、主题编辑器里的 block 生成、以及逐步开放的桌面 Canvas。由此推出的判断是：被限制在手机端的是「用一段业务描述生成最多 3 套免费整站主题」这一条，不是 Shopify 所有主题生成。Shopify 没有发布这条限制的原因，上面这句不是官方解释。

## 行动建议

1. 用 Banner、品牌区块和活动落地页做生成质量与编辑连续性的试点。
2. 用真实商品详情场景验证 AI 修改是否保留数据绑定、变体逻辑和应用区块。
3. 把预览、校验、发布、版本记录和回滚纳入生成流程。
4. 为生成结果建立质量检查：响应式、无障碍、性能、SEO 元数据和关键交易路径。
5. 产品若提供「描述生成整站」，桌面和手机分开设计入口。不要把 Shopify 的手机端整站生成，理解成桌面不能做主题编辑。

## 待验证事项

- “AI 已强力替代某类模板”需要结合具体产品、编辑器、用户和维护周期实测，当前没有跨平台量化证据。
- “未来 1–2 年”一类时间判断不作为事实记录，应以持续竞品追踪和用户研究更新。
- Shopify 为什么把整站主题生成从桌面后台撤下：Adding themes 页没有写原因。
- Grow 与 Growth 是否为同一套餐：两页用词不同，本次不合成。
- Plus 能否使用「描述生成整站主题」：资格句没有列入 Plus，也没有写明排除。
- Canvas 在具体店铺是否已经可见：changelog 写逐步开放，本次没有登录店铺核对。
- Shopify Horizon 家族、Wix Harmony、Webflow AI Builder 的当前能力范围仍须逐项查证。2026-10-11 曾引用、后因未核实而删除的 AI blocks 开发文档链接，本次不补回。
- PageFly、GemPages、Atlas 等页面搭建应用本次没有逐页打开，不记入事实。

## 来源与参考

- [Shopify themes: architecture versions and sources](https://help.shopify.com/en/manual/online-store/themes/themes-by-shopify/about-themes)（主题兼容性与 Horizon 家族主题说明；访问：2026-10-11）
- [Shopify Sidekick app extensions](https://shopify.dev/docs/apps/build/sidekick)（说明应用扩展与受控动作的产品边界；访问：2026-10-11）
- [Adding, previewing, and buying themes](https://help.shopify.com/en/manual/online-store/themes/adding-themes)（访问：2026-10-12）
- [Automatically generating theme blocks in the theme editor](https://help.shopify.com/en/manual/online-store/themes/customizing-themes/theme-editor/sidekick/generate-blocks)（访问：2026-10-12）
- [Online Store Editor with Sidekick on mobile](https://changelog.shopify.com/posts/online-store-editor-with-sidekick-on-mobile)（页面日期 2026-06-17；访问：2026-10-12）
- [Design a fully bespoke store with Canvas](https://changelog.shopify.com/posts/design-a-fully-bespoke-store-with-canvas)（页面日期 2026-10-01；访问：2026-10-12）
- [Introducing Canvas](https://www.shopify.com/news/introducing-canvas)（页面日期 2026-10-01；访问：2026-10-12）
