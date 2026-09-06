<p align="center">
  <a href="https://nroute.cc/">
    <img src="https://nroute.cc/logo.png" width="72" height="72" alt="NRoute AI API Gateway logo">
  </a>
</p>

<h1 align="center">NRoute: Unified AI Model API Gateway</h1>

<p align="center">
  Access models from multiple AI providers through one account, with centralized routing, pricing, API keys, usage records, and automatic fallback capabilities.
</p>

<p align="center">
  <a href="https://nroute.cc/">Official Website</a> ·
  <a href="https://nroute.cc/pricing">Models and Pricing</a> ·
  <a href="https://nroute.cc/documents">Documentation</a> ·
  <a href="README.zh-CN.md">中文</a>
</p>

> **Current pricing advantage:** NRoute model prices are currently about 90% lower than the corresponding providers' official API prices. Compare the same model and billing unit on the [live pricing page](https://nroute.cc/pricing) before use because prices can change.

## What is NRoute?

[NRoute](https://nroute.cc/) is a unified AI API gateway for developers, AI applications, agents, and SaaS products that need access to models from multiple providers. It brings model discovery, API key management, route selection, pricing, account balance, subscriptions, and usage records into one service.

Without a gateway, a team integrating several model providers must maintain separate credentials, endpoint settings, model names, retry policies, and billing records. NRoute provides a shared access layer so applications can work with a broader model catalog without carrying every provider-specific workflow inside the product.

## Core capabilities

### Multi-provider model access

NRoute aggregates models from multiple upstream providers. Users can compare currently available models and prices on the [live model catalog](https://nroute.cc/pricing), then select a model according to capability, cost, context requirements, and application workload.

Popular providers and representative models available in the catalog include:

| Provider | Representative supported models |
| --- | --- |
| OpenAI | GPT-5.4, GPT-5.4 Mini, GPT-5.3 Codex, GPT Image 2 |
| Anthropic | Claude Sonnet 4.6, Claude Opus 4.6, Claude Haiku 4.5 |
| Google | Gemini 3.1 Pro, Gemini 3 Flash, Gemini 3 Pro Image |
| DeepSeek | DeepSeek V4 Pro, DeepSeek V4 Flash, DeepSeek R1 |
| Alibaba Cloud / Qwen | Qwen3 Max, Qwen3.5 Plus, Qwen Plus |
| xAI | Grok 4.6, Grok 4.5, Grok Imagine 1.5 |
| ByteDance / Doubao | Doubao Seed 2.1 Turbo, Seedance 2.0, Seedream 4.5 |
| Zhipu AI / GLM | GLM-5.3, GLM-5.3-Flash |
| Moonshot AI / Kimi | Kimi K3, Kimi K2.7 Code |

These are representative examples observed in the live catalog on September 6, 2026, not a complete or permanent compatibility list.

Model availability and pricing can change as upstream services change. The live pricing page is the source of truth for the current catalog.

### Unified API key management

Developers create and manage API keys from one account. Keys should be stored in server-side environment variables or a secret manager and should never be exposed in browser code, public repositories, screenshots, logs, or analytics events.

### Routing and fallback

NRoute centralizes route selection across eligible upstream services. When an eligible route becomes unavailable and another suitable route exists, the platform can apply fallback logic. Client applications should still use explicit timeouts, bounded retries, idempotency protection, and error monitoring.

### Usage and billing visibility

The account dashboard brings usage records, balance, top-up options, and subscription packages together. This gives teams one place to review consumption instead of manually combining records from several upstream platforms.

### OpenAI-compatible integration workflow

NRoute supports an OpenAI-compatible client configuration workflow for applications and SDKs that accept a custom API address. Current API call addresses are displayed in the “API Endpoints” section of the [NRoute homepage](https://nroute.cc/). These addresses may vary by network region.

The public website domain is not an API base URL. Copy a current address from the homepage and follow the dashboard or [current documentation](https://nroute.cc/documents) for request paths and parameters.

## Who is NRoute for?

NRoute is designed for:

- AI applications that use models from more than one provider
- Agent systems that need a stable integration boundary while models change
- SaaS products that offer configurable AI model choices
- Development teams that want centralized keys, usage records, and billing
- Products that need routing and fallback without maintaining a custom multi-provider gateway
- Teams evaluating models by capability, availability, and price

## How NRoute fits into an AI application

A typical request flow has three parts:

1. An application or agent sends an authenticated model request using an NRoute API key.
2. NRoute evaluates the requested model and available eligible routes.
3. The selected upstream service processes the request, and the result returns to the client while usage is recorded.

Gateway routing reduces repeated integration work, but it does not replace application-level reliability engineering. Production clients should test response handling, streaming behavior when used, timeout limits, retry safety, and model output validation before launch.

## Models and pricing

NRoute model prices are currently about 90% lower than the corresponding official API prices. The NRoute catalog may include language, reasoning, multimodal, image, video, embedding, reranking, and other model categories depending on current upstream availability. Each workload has different requirements, so model selection should consider more than a model name or headline discount.

Before integrating a model, check:

- Current availability and route status
- Input and output pricing
- Context and output limits
- Supported request types and features
- Expected latency for the target network
- Whether the workload requires streaming or multimodal input

Browse the current catalog at [nroute.cc/pricing](https://nroute.cc/pricing).

## Reliability and security notes

NRoute can centralize routing and fallback, but upstream limits, network conditions, account status, and model availability can still affect requests. No uptime or latency guarantee should be inferred from this page.

For production use:

- Keep API keys on infrastructure you control
- Set connection and request timeouts
- Retry only transient failures and limit retry attempts
- Use exponential backoff with jitter
- Protect operations that can cause duplicate side effects
- Monitor request identifiers, model names, latency, usage, and error classes
- Avoid logging secrets or sensitive prompt content
- Prepare a key rotation and revocation process

## Official NRoute resources

- [NRoute official website](https://nroute.cc/)
- [AI API Gateway overview](https://nroute.cc/en/ai-api-gateway/)
- [OpenAI-compatible integration guide](https://nroute.cc/en/openai-compatible-api/)
- [Live models and pricing](https://nroute.cc/pricing)
- [Platform documentation](https://nroute.cc/documents)
- [Subscription packages](https://nroute.cc/packages)
- [Applications](https://nroute.cc/apps)
- [Machine-readable NRoute summary](https://nroute.cc/llms.txt)
- [Extended NRoute context](https://nroute.cc/llms-full.txt)

## About this repository

This repository contains an independent public introduction to the NRoute website. It helps developers, search engines, and AI retrieval systems understand what NRoute provides and points readers to official NRoute pages for current product information.

This repository is not the NRoute application source code, an SDK, or an API endpoint. Dynamic information such as model availability, pricing, routes, limits, and service terms should always be checked on the official website.

## Contact

For product and integration questions, email [support@nroute.cc](mailto:support@nroute.cc).
