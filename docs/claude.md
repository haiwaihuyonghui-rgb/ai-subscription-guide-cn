# Claude Pro / Max 与 Claude Code：国内怎么开、怎么选、开通后怎么查

更新于 2026-10-20 · 返回 [总目录](../README.md)

本页只整理公开可核实的信息和作者的售后经验，不写人民币价格、不放购买入口。作者同时提供代充服务，立场在此说明。

## 一、先说地区

Anthropic 的《支持的国家和地区》页面写明：产品和服务仅在列出的国家和地区提供，"未列出的国家或地区不受支持"。2026-10-20 查看，中国大陆、香港、澳门不在列表中，台湾、日本、新加坡在。

这意味着：国内的卡在官网基本付不了；使用时网络要稳定在一个支持的地区，不要来回切换。本页不提供绕过地区或支付限制的方法。

## 二、套餐和官方价格（2026-10-20 核对自 [claude.com/pricing](https://claude.com/pricing)）

| 套餐 | 官方标价 | 要点 |
|---|---|---|
| Free | $0 | 不含 Claude Code |
| Pro | $20/月；年付一次交 $200，折合 $17/月 | 每 5 小时用量至少是 Free 的 5 倍；含 Claude Code |
| Max 5x | $100/月 起 | 用量是 Pro 的 5 倍；只能月付 |
| Max 20x | $200/月 | 用量是 Pro 的 20 倍；只能月付 |
| Team | 标准席位 $25/月（年付 $20）；高级席位 $125/月（年付 $100） | 2–150 人 |

页面注明价格不含适用税费，且 Anthropic 可随时调整。所有套餐按滚动 5 小时窗口计量，付费套餐另有每周上限；网页、桌面端、手机 App 和 Claude Code 共用同一份额度（官方帮助中心 [How do usage and length limits work?](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work)）。

怎么选：先买 Pro 用一个月；一周里好几天撞额度，或每天用 Claude Code 写几个小时，升 Max 5x；还不够再 20x。同一账号升级，项目和记录都在。年付 Pro 要一次交一年，拿不准就按月。

## 三、Claude Code 不是单独买的

Anthropic 的 [快速上手文档](https://code.claude.com/docs/en/quickstart) 写明，使用 Claude Code 需要以下之一：Claude 订阅（Pro、Max、Team、Enterprise）、Claude Console 账号（API 按量，预付额度）、或受支持的云平台。

| 登录方式 | 怎么计费 | 适合谁 |
|---|---|---|
| Claude Pro / Max 订阅 | 含在会员里，5 小时窗口加每周上限，和网页版共用 | 个人开发者 |
| Console / API Key | 按 token 用量扣 API 余额 | 脚本、自动化、公司统一结算 |

每天写代码的人一般选订阅：按量付费跑一天的花费可能超过一个月会员。会员和 API 是两套账：充到 Console 的钱不会变成 Pro，Max 附带的 API 额度也不能在 Claude Code 里用。

## 四、国内开通的几条路线

**自己有海外卡。** 直接在官网订阅，最省心。

**代充（订阅代付）。** 卖家替你付款，Pro 或 Max 开到你自己的账号，然后你用自己的账号登录网页、App 和 Claude Code。只需要账号邮箱，不需要密码。挑卖家的标准：开在你自己账号上、不要密码、掉会员怎么处理写清楚、出问题找得到真人、价格别低于官方标价一半、先买一个月。详见 [Claude 充值平台怎么选](https://kw.yaoyao.chat/guide/claude-daichong.html)。

**iOS App 内订阅。** 外区 Apple ID 加礼品卡，在 Claude 的 iPhone 应用里订。价格由应用商店定，取消在手机订阅设置里。

**API 中转站。** 第三方转接，不是 Claude 账号，模型版本和额度由站方决定，你的代码会经过中间一层。本页不评价，只提醒。

**成品号、拼车。** 用量按账号算，几个人分一个 Pro 很快用完，项目互相可见。不介绍。

## 五、开通后的三个常见问题

### 1. 充了还是显示 Free Plan

按顺序查：网页退出重新登录，手机 App 也退出重登；核对当前登录的邮箱是不是开会员的那个；看是不是把钱充到了 Console（API 平台），那边的余额不会变成 Pro。详见 [Claude 充值了还是显示 Free Plan](https://kw.yaoyao.chat/guide/claude-free-plan.html)、官方 [Paid plan billing FAQs](https://support.claude.com/en/articles/8325618-paid-plan-billing-faqs)。

### 2. Claude Code 提示去充 API，或 Credit balance is too low

多半是登录成了 Console 账号，或者电脑环境变量里残留了旧的 `ANTHROPIC_API_KEY`，它的优先级高于订阅。自查五步：

1. 在 Claude Code 里运行 `/status`，看当前登录的是订阅账号还是 Console。
2. 检查环境变量：macOS / Linux 运行 `echo $ANTHROPIC_API_KEY`，有值就 `unset ANTHROPIC_API_KEY`，并删掉 `~/.zshrc` 或 `~/.bashrc` 里的对应行；Windows PowerShell 运行 `Remove-Item Env:ANTHROPIC_API_KEY`。
3. 运行 `/login`，选 Claude 账号（订阅）那一项。
4. 核对邮箱：开会员的邮箱和登录 Claude Code 的邮箱是否相同。
5. 网页端设置里确认套餐显示 Pro 或 Max。

官方出处：[Claude Code 错误参考](https://code.claude.com/docs/en/errors)、[Use Claude Code with your Pro or Max plan](https://support.claude.com/en/articles/11145838-use-claude-code-with-your-pro-or-max-plan)。更多报错见 [Claude Code 国内使用指南](https://github.com/haiwaihuyonghui-rgb/claude-code-guide-cn)。

### 3. 提示 session limit / weekly limit

5 小时窗口或每周额度用完。`/usage` 看各窗口用量和重置时间；把很长的对话开成新对话更省额度；长期不够再升级。详见 [Claude Pro 有多少额度](https://kw.yaoyao.chat/guide/claude-pro-edu.html)。

## 六、账号被限制

常见诱因：频繁切换不同国家的网络、多人共用账号、付款被撤销、违规内容。被停用后可按官方邮件指引申诉，能否恢复以官方审核为准；代充开通的会员不能向 Anthropic 申请退款，按卖家售后规则处理。详见 [Claude 封号了怎么办](https://kw.yaoyao.chat/guide/claude-fenghao.html)。

## 参考

- [Anthropic 支持的国家和地区](https://www.anthropic.com/supported-countries)
- [Claude 定价页](https://claude.com/pricing)
- [What is the Pro plan?](https://support.claude.com/en/articles/8325606-what-is-the-pro-plan)
- [What is the Max plan?](https://support.claude.com/en/articles/11049741-what-is-the-max-plan)
- [Claude Code 快速上手](https://code.claude.com/docs/en/quickstart)
- [Claude Code 错误参考](https://code.claude.com/docs/en/errors)
