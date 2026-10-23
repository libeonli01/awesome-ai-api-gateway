<div align="center">

# Awesome AI API Gateway

**AI API 网关 / 中转 / 反代生态精选清单**

把 Claude、OpenAI、Gemini、Grok 等多家大模型聚合到统一接口的开源方案与托管服务

[![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-2ea44f?style=flat-square)](CONTRIBUTING.md)
[![License](https://img.shields.io/badge/License-CC0-lightgrey?style=flat-square)](LICENSE)

[English](#) · **简体中文**

</div>

---

## 这份清单解决什么问题

你想用 Claude Opus 写代码、用 GPT 处理文本、用 Gemini 看图 —— 但这意味着三个平台的账号、三张外币卡、三套 SDK、三份账单。

**AI API 网关**（AI Gateway / LLM Proxy / API 中转）就是为了解决这个：一个 Base URL、一个 Key、一套协议，后面接所有模型。

这份清单收录了实现这件事的各种方案 —— 从你自己部署的开源软件，到开箱即用的托管服务。

---

## 目录

- [全功能网关](#全功能网关) — 管理 + 计费 + 分发，适合搭平台
- [高性能路由层](#高性能路由层) — 专注协议转换与路由，适合嵌入现有架构
- [特定生态网关](#特定生态网关) — 针对某一家或某一场景
- [托管服务](#托管服务) — 不想自己部署
- [周边工具](#周边工具)
- [客户端](#客户端) — 配好网关之后用什么
- [选型建议](#选型建议)

---

## 全功能网关

带管理后台、用户体系、计费与令牌分发的完整方案。适合对外提供服务或团队内部分发。

### [new-api](https://github.com/QuantumNous/new-api)
![Stars](https://img.shields.io/github/stars/QuantumNous/new-api?style=flat-square&label=%E2%98%85) ![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)

统一的 AI 模型聚合分发平台，one-api 的活跃衍生版本。支持跨协议转换（OpenAI / Claude / Gemini 互转）、多渠道负载均衡、令牌分组倍率、完整的计费与用量统计。中文社区生态最活跃的一个。

### [one-api](https://github.com/songquanpeng/one-api)
![Stars](https://img.shields.io/github/stars/songquanpeng/one-api?style=flat-square&label=%E2%98%85) ![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)

LLM API 管理与分发系统的鼻祖项目。支持 OpenAI、Azure、Anthropic Claude、Google Gemini、DeepSeek 等主流供应商，单可执行文件部署，Docker 一行启动。大量衍生项目的上游。

### [coai](https://github.com/coaidev/coai)
![Stars](https://img.shields.io/github/stars/coaidev/coai?style=flat-square&label=%E2%98%85) ![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white) ![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)

多租户 AI 一站式解决方案，自带管理后台与计费系统。前后端一体，开箱即用度高，适合快速搭一个对外的 AI 服务站。

### [MIXAPI](https://github.com/aiprodcoder/MIXAPI)
![Stars](https://img.shields.io/github/stars/aiprodcoder/MIXAPI?style=flat-square&label=%E2%98%85)

大模型 API 网关，把多种模型统一成 OpenAI 兼容接口、Claude 接口、Gemini 接口三套出口。协议转换覆盖比较全。

---

## 高性能路由层

不带管理后台，专注做协议转换和路由。适合作为组件嵌入已有系统。

### [LiteLLM](https://github.com/BerriAI/litellm)
![Stars](https://img.shields.io/github/stars/BerriAI/litellm?style=flat-square&label=%E2%98%85) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Rust](https://img.shields.io/badge/Rust_core-000000?style=flat-square&logo=rust&logoColor=white)

生态最大的 LLM 网关。Rust 核心 + Python SDK，统一调用 100+ 供应商。既能当 SDK 用（`litellm.completion()`），也能起 Proxy Server 用。可观测性、重试、fallback、预算控制都有。**如果你在写 Python 且要接多家模型，先看它。**

### [Portkey Gateway](https://github.com/Portkey-AI/gateway)
![Stars](https://img.shields.io/github/stars/Portkey-AI/gateway?style=flat-square&label=%E2%98%85) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)

极快的 AI 网关，内置 Guardrails（内容护栏）。路由到 1600+ LLM，边缘部署友好，可跑在 Cloudflare Workers 上。适合对延迟敏感的场景。

### [GoModel](https://github.com/ENTERPILOT/GoModel)
![Stars](https://img.shields.io/github/stars/ENTERPILOT/GoModel?style=flat-square&label=%E2%98%85) ![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)

Go 写的轻量 AI 网关，统一 OpenAI 兼容接口。定位是 LiteLLM 的轻量替代，单二进制、低内存、自带可观测性。

### [MCP Context Forge](https://github.com/IBM/mcp-context-forge)
![Stars](https://img.shields.io/github/stars/IBM/mcp-context-forge?style=flat-square&label=%E2%98%85) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

IBM 出品，面向 MCP（Model Context Protocol）的网关、注册中心与代理。如果你在搭 MCP 工具生态而不只是转发模型请求，看这个。

---

## 特定生态网关

### [kiro-gateway](https://github.com/jwadow/kiro-gateway)
![Stars](https://img.shields.io/github/stars/jwadow/kiro-gateway?style=flat-square&label=%E2%98%85) ![Python](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)

把 Kiro IDE / CLI（Amazon Q Developer / AWS CodeWhisperer）的能力代理成标准 API 接口。

### [cc-gateway](https://github.com/motiful/cc-gateway)
![Stars](https://img.shields.io/github/stars/motiful/cc-gateway?style=flat-square&label=%E2%98%85) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)

AI API 身份网关，反代过程中规范化设备指纹与遥测数据。关注隐私和请求一致性的场景适用。

### [FastChat](https://github.com/lm-sys/FastChat)
![Stars](https://img.shields.io/github/stars/lm-sys/FastChat?style=flat-square&label=%E2%98%85)

训练、服务、评测 LLM 的开放平台。自带 OpenAI 兼容的 RESTful API 服务器，可以把本地模型包成 OpenAI 接口。

### [vLLM](https://github.com/vllm-project/vllm)
![Stars](https://img.shields.io/github/stars/vllm-project/vllm?style=flat-square&label=%E2%98%85)

高吞吐推理引擎，`--api-server` 模式直接提供 OpenAI 兼容接口。自托管开源模型的事实标准。

---

## 托管服务

不想碰服务器、不想找上游、不想处理故障切换的话。

| 服务 | 特点 |
|---|---|
| [**Leonis AI**](https://ai.svtun.cn) | Claude / OpenAI / Gemini / Grok 四家聚合共 [114 个模型](https://leonis-ai.github.io/models.html)，双协议兼容，原生支持 Claude Code 与 Codex CLI，国内直连，Prompt 缓存完整支持，用量明细可查 |
| [**Uta API**](https://api.liwenjun.shop) | 面向开发者的 OpenAI-compatible API 网关与管理服务；提供公开产品入口、账户/API 使用界面和健康检查，当前正式版本为 `V0.1.4.1`。模型目录、可用性与实时费率以站内页面为准 |
| [OpenRouter](https://openrouter.ai) | 模型覆盖面最广，统一 OpenAI 协议，按量计费 |
| [Cloudflare AI Gateway](https://developers.cloudflare.com/ai-gateway/) | 免费的网关层，提供缓存、限流、日志，但不提供模型本身 |

> 💡 **自建 vs 托管怎么选？**
> 自建适合：有稳定上游渠道、有运维能力、量大到值得自己管。
> 托管适合：只是想用、不想为了用 AI 再养一套基础设施。

---

## 周边工具

### [all-api-hub](https://github.com/qixing-jk/all-api-hub)
![Stars](https://img.shields.io/github/stars/qixing-jk/all-api-hub?style=flat-square&label=%E2%98%85)

New-API / Sub2API 账号聚合管理器。多站点余额与用量看板、自动签到、一键切换。同时管好几个网关账号的话很省事。

### [ai-client-configs](https://github.com/leonis-ai/ai-client-configs)

20+ 主流 AI 客户端的 Base URL 配置模板，复制即用。

### [ai-api-pricing](https://github.com/leonis-ai/ai-api-pricing)

成本计算与缓存经济学，附可运行的计算器脚本。

### [claude-code-guide](https://github.com/leonis-ai/claude-code-guide) · [codex-cli-guide](https://github.com/leonis-ai/codex-cli-guide) · [gemini-api-guide](https://github.com/leonis-ai/gemini-api-guide)

三大 CLI / API 的中文配置手册。

### [cc-switch-guide](https://github.com/leonis-ai/cc-switch-guide)

用 cc-switch 管理 Claude Code 与 Codex 的多套供应商配置，一键切换。

---

## 客户端

网关配好之后，用什么连上去。

| 客户端 | 平台 | 协议支持 |
|---|---|---|
| [Claude Code](https://github.com/leonis-ai/claude-code-guide) | CLI | Anthropic Messages |
| [Codex CLI](https://github.com/openai/codex) | CLI | OpenAI Responses |
| [Cline](https://github.com/cline/cline) | VS Code | Anthropic / OpenAI |
| [Roo Code](https://github.com/RooCodeInc/Roo-Code) | VS Code | Anthropic / OpenAI |
| [Cursor](https://cursor.com) | 编辑器 | OpenAI Chat |
| [Cherry Studio](https://github.com/CherryHQ/cherry-studio) | 桌面 | OpenAI Chat |
| [ChatBox](https://github.com/Bin-Huang/chatbox) | 桌面 | OpenAI Chat |
| [LobeChat](https://github.com/lobehub/lobe-chat) | Web / 桌面 | OpenAI Chat |
| [NextChat](https://github.com/ChatGPTNextWeb/NextChat) | Web / 桌面 | OpenAI Chat |
| [Open WebUI](https://github.com/open-webui/open-webui) | Web | OpenAI Chat |

---

## 选型建议

```
你要做什么？
│
├─ 只是自己想用多家模型
│  └─ 托管服务（Leonis AI / OpenRouter）
│
├─ 团队内部分发，需要额度管理
│  └─ new-api / one-api（自建，带后台和计费）
│
├─ 在代码里接多家模型，不需要后台
│  └─ LiteLLM（Python）/ Portkey（TS，边缘部署）
│
├─ 对外提供 AI 服务，要收费
│  └─ new-api / coai（完整的用户+计费体系）
│
└─ 自托管开源模型，包成 OpenAI 接口
   └─ vLLM / FastChat
```

### 三个容易踩的坑

**1. 缓存支持决定 Claude Code 的成本**
Claude Code 每轮都会重发项目上下文，长会话里缓存读取能占总 Token 量的 60%~90%。网关不支持 Prompt Caching，账单可能差好几倍。选型时一定要确认。

**2. 协议转换是有损的**
OpenAI 协议转 Anthropic 协议时，Tool Use 的部分字段、`thinking` 块、缓存控制标记可能丢失。跑 Claude Code 这类深度依赖 Anthropic 原生协议的客户端时，优先选支持 `/v1/messages` 原生透传的网关，而不是靠 `/v1/chat/completions` 转换。

**3. 单点上游 = 单点故障**
只接一个上游的网关，上游挂了你就全挂。生产环境至少配两条通道并设好优先级与自动切换。

---

## 贡献

欢迎 PR 补充遗漏的项目。请遵守：

- 项目要真实可用，有明确的仓库地址或产品页
- 一句话说清它解决什么问题，不要复制官方营销词
- 按已有分类放置，star 数用动态徽章而不是写死数字

## License

[CC0 1.0](LICENSE) — 公共领域，随意使用。

---

<sub>

**关键词** · AI 网关 · AI Gateway · API 中转 · AI 中转 · LLM Proxy · LLM Gateway · API 反代 ·
one-api · new-api · sub2api · LiteLLM · Claude 中转 · OpenAI 反代 · GPT 中转 · Gemini 中转 ·
谷歌 Gemini · Grok API · 大模型 API 聚合 · API 聚合分发

</sub>
