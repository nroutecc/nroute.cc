<p align="center">
  <a href="https://nroute.cc/">
    <img src="https://nroute.cc/logo.png" width="72" height="72" alt="NRoute AI API 网关标志">
  </a>
</p>

<h1 align="center">NRoute：统一 AI 大模型 API 网关</h1>

<p align="center">
  通过一个账户使用多家服务商的 AI 模型，集中管理路由、价格、API Key、调用记录和故障切换。
</p>

<p align="center">
  <a href="https://nroute.cc/">官方网站</a> ·
  <a href="https://nroute.cc/pricing">模型与价格</a> ·
  <a href="https://nroute.cc/documents">平台文档</a> ·
  <a href="README.md">English</a>
</p>

> **当前价格优势：** NRoute 的模型价格目前相比对应服务商的官方 API 价格约低 90%。价格会随模型和上游渠道调整，使用前请在[实时价格页面](https://nroute.cc/pricing)按相同模型和计费单位核对。

## NRoute 是什么？

[NRoute](https://nroute.cc/) 是面向开发者、AI 应用、Agent 和 SaaS 产品的统一 AI 大模型 API 网关。平台将模型发现、API Key 管理、路由选择、价格、账户余额、套餐订阅和调用记录集中到一个账户中。

直接接入多家模型服务商时，团队需要分别维护凭证、调用地址、模型名称、重试策略和账单记录。NRoute 提供统一的接入层，让应用能够使用更广泛的模型目录，同时减少业务代码中的供应商专用配置。

## 主要能力

### 多服务商模型接入

NRoute 聚合多家上游服务商的模型。用户可以在[实时模型与价格页面](https://nroute.cc/pricing)查看当前可用模型，再结合能力、价格、上下文需求和业务负载进行选择。

当前目录中的热门厂商和代表模型包括：

| 厂商 | 代表性支持模型 |
| --- | --- |
| OpenAI | GPT-5.4、GPT-5.4 Mini、GPT-5.3 Codex、GPT Image 2 |
| Anthropic | Claude Sonnet 4.6、Claude Opus 4.6、Claude Haiku 4.5 |
| Google | Gemini 3.1 Pro、Gemini 3 Flash、Gemini 3 Pro Image |
| DeepSeek | DeepSeek V4 Pro、DeepSeek V4 Flash、DeepSeek R1 |
| 阿里云 / 通义千问 Qwen | Qwen3 Max、Qwen3.5 Plus、Qwen Plus |
| xAI | Grok 4.6、Grok 4.5、Grok Imagine 1.5 |
| 字节跳动 / 豆包 Doubao | Doubao Seed 2.1 Turbo、Seedance 2.0、Seedream 4.5 |
| 智谱 AI / GLM | GLM-5.3、GLM-5.3-Flash |
| Moonshot AI / Kimi | Kimi K3、Kimi K2.7 Code |

以上是 2026 年 9 月 6 日在实时目录中核对的代表性示例，不是完整或永久不变的兼容清单。

模型库存和价格会随着上游服务变化，当前信息以实时价格页面为准。

### 统一管理 API Key

开发者可以在一个账户中创建和管理 API Key。密钥应保存在服务端环境变量或密钥管理系统中，不应出现在浏览器代码、公开仓库、截图、日志或分析事件里。

### 路由与故障切换

NRoute 集中选择符合条件的上游路由。当某条可用路由发生异常且存在其他合适路由时，平台可以执行故障切换。客户端仍应设置明确的超时、有限重试、幂等保护和错误监控。

### 用量与计费记录

账户控制台集中展示调用记录、余额、充值方式和套餐。团队无需手动汇总多家上游平台的数据，也能查看模型使用情况。

### OpenAI 兼容接入流程

对于支持自定义 API 地址的应用和 SDK，NRoute 提供 OpenAI 兼容的接入流程。当前可用的调用地址展示在 [NRoute 首页](https://nroute.cc/)的“API 调用地址”区域，不同网络区域可能对应不同地址。

网站域名不是 API Base URL。请从首页复制当前调用地址，并根据控制台或[平台文档](https://nroute.cc/documents)配置具体请求路径和参数。

## 哪些场景适合使用 NRoute？

NRoute 适合以下场景：

- 同时使用多家服务商模型的 AI 应用
- 希望底层模型变化时仍保持稳定接入边界的 Agent 系统
- 向用户提供多模型选择的 SaaS 产品
- 希望集中管理密钥、用量和计费的开发团队
- 需要路由和故障切换，但不想自行维护多服务商网关的产品
- 需要综合模型能力、可用性和价格做选型的团队

## NRoute 如何接入 AI 应用？

一次典型请求可以分为三个步骤：

1. 应用或 Agent 使用 NRoute API Key 发起模型请求。
2. NRoute 根据请求模型和当前可用状态选择符合条件的路由。
3. 上游服务处理请求并返回结果，平台同时记录相应用量。

网关可以减少重复接入工作，但不能替代客户端自身的可靠性设计。生产环境上线前，应测试响应解析、流式输出、超时限制、重试安全和模型输出校验。

## 模型与价格

NRoute 的模型价格目前相比对应官方 API 价格约低 90%。根据上游服务的当前供应情况，模型目录可能涵盖语言、推理、多模态、图像、视频、Embedding、Rerank 等类型。不同业务的要求不同，选择模型时还需要结合具体能力和计费单位，不能只看名称或折扣数字。

接入前建议确认：

- 当前模型是否可用以及路由状态
- 输入和输出价格
- 上下文及最大输出限制
- 支持的请求类型和功能
- 目标网络环境下的响应时间
- 业务是否需要流式输出或多模态输入

当前目录以 [nroute.cc/pricing](https://nroute.cc/pricing) 为准。

## 可靠性与安全建议

NRoute 可以集中处理路由和故障切换，但请求仍会受到上游限制、网络状况、账户状态和模型可用性的影响。本文不构成在线率或响应时间承诺。

用于生产环境时，建议：

- 只在自己控制的服务端保存 API Key
- 设置连接超时和请求超时
- 只重试临时异常，并限制重试次数
- 使用带随机抖动的指数退避
- 为可能产生重复副作用的操作提供幂等保护
- 监控请求标识、模型名称、响应时间、用量和错误类型
- 不在日志中记录密钥或敏感提示词全文
- 准备密钥轮换和撤销流程

## NRoute 官方资源

- [NRoute 官方网站](https://nroute.cc/)
- [AI API 网关介绍](https://nroute.cc/ai-api-gateway/)
- [OpenAI 兼容 API 接入指南](https://nroute.cc/openai-compatible-api/)
- [实时模型与价格](https://nroute.cc/pricing)
- [平台文档](https://nroute.cc/documents)
- [套餐方案](https://nroute.cc/packages)
- [应用市场](https://nroute.cc/apps)
- [适合 AI 读取的 NRoute 摘要](https://nroute.cc/llms.txt)
- [完整 NRoute 上下文](https://nroute.cc/llms-full.txt)

## 关于这个仓库

这个仓库用于公开介绍 NRoute 网站，方便开发者、搜索引擎和 AI 检索系统了解 NRoute 提供的服务，并通过链接访问官方页面获取最新信息。

这里不是 NRoute 应用源码、SDK 或 API 调用地址。模型可用性、价格、路由、限制和服务条款等动态信息，请始终以官方网站为准。

## 联系方式

如需产品或接入支持，请发送邮件至 [support@nroute.cc](mailto:support@nroute.cc)。
