<div align="center">

# 🚀 MiMo Copilot Chat: BYOK Xiaomi AI in VS Code

### Use Xiaomi MiMo models (1M token context) in GitHub Copilot Chat. No Copilot Pro needed.

**BYOK (Bring Your Own Key). Pay only for what you use.**

[![Version](https://img.shields.io/badge/version-0.1.4-blue)](https://github.com/ltmoerdani/xiaomi-mimo-copilot-chat/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![VS Code](https://img.shields.io/badge/VS%20Code-1.125%2B-blue)](https://code.visualstudio.com/)
[![MiMo](https://img.shields.io/badge/MiMo-V2.5-orange)](https://xiaomimimo.com)
[![CI](https://github.com/ltmoerdani/xiaomi-mimo-copilot-chat/actions/workflows/ci.yml/badge.svg)](https://github.com/ltmoerdani/xiaomi-mimo-copilot-chat/actions/workflows/ci.yml)

[Why bother](#-why-bother) · [Quick Start](#-quick-start-60-sec) · [Models](#-models) · [Compare](#-copilot-vs-mimo-copilot-chat) · [FAQ](#-faq) · [Settings](#-settings)

</div>

---

> ### The pitch
>
> GitHub Copilot Free gives you 2,000 completions/month. Pro costs $10/month. Pro+ costs $39/month.
>
> **MiMo Copilot Chat** lets you plug Xiaomi MiMo into Copilot Chat using your own API key. You pay only for the tokens you use. MiMo V2.5 has a 1,000,000 token context window and costs a fraction of GPT-4 or Claude.
>
> Trade-off: you need a MiMo API key and pay per token. No subscription, no lock-in.

---

## 🔥 Why bother

If you already use Copilot Chat but want a cheaper, longer-context model for big files or long conversations, this extension drops MiMo straight into the model picker. No separate chat window. No new workflow.

| | What you get |
|---|---|
| 💸 **Cost** | Pay per token on MiMo's plan. No monthly subscription. |
| 🌍 **Context** | Up to 1,048,576 tokens. Fits entire repos and long docs. |
| 🧠 **Reasoning** | MiMo V2.5 supports chain-of-thought reasoning output. |
| 🔌 **Native transport** | OpenAI-compatible `/chat/completions`. Tool-calling supported. |
| 🔒 **Key storage** | Stored in VS Code SecretStorage. Never leaves your machine. |
| 🧩 **Seamless** | Appears in the Copilot Chat model picker next to GPT and Claude. |

---

## ⚡ Quick Start (60 sec)

```bash
1. Install this extension
2. Open Copilot Chat (Cmd+Shift+I)
3. Click model picker → Manage Models
4. Pick "MiMo" → paste your API key
5. Select mimo-v2.5 → start chatting
```

Get a MiMo API key at [xiaomimimo.com](https://xiaomimimo.com).

<details>
<summary><b>Detailed step-by-step</b></summary>

1. Install **GitHub Copilot Chat** from the [marketplace](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) (required).
2. Install this extension.
3. Open **GitHub Copilot Chat** (Copilot icon in sidebar or `Cmd+Shift+I` / `Ctrl+Shift+I`).
4. Click the **model picker** (current model name) then **Manage Models**.
5. Select **MiMo**.
6. Press `Enter` to accept the default **Group Name**.
7. Enter your MiMo **API Key** when prompted. VS Code stores it as a secret.
8. Choose the models you want available.
9. Select any MiMo model from the picker and start chatting.

**Tip:** If a model shows in the **Language Models** view but not the chat picker, hover its row and click the eye icon to enable it.

</details>

---

## 📊 Copilot vs MiMo Copilot Chat

| | Copilot Free | Copilot Pro | Copilot Pro+ | **MiMo Copilot Chat** |
|---|---|---|---|---|
| **Price** | $0 | $10/mo | $39/mo | Pay per token |
| **Monthly limit** | 2,000 completions | 300 chats | Unlimited (fair use) | None (you control spend) |
| **Max context** | Varies | Varies | Varies | **1,048,576 tokens** |
| **Models** | GPT-4o, Claude 3.5 | + o3, Claude 3.7 | + GPT-4.1, o3-pro | **MiMo V2.5 / Pro** |
| **Key ownership** | GitHub | GitHub | GitHub | **You** |

> Not a replacement for Copilot. This extension adds MiMo models *into* the existing Copilot Chat interface.

---

## 🧠 Models

The extension fetches the live model list from:

```
https://token-plan-sgp.xiaomimimo.com/v1/models
```

### Bundled model limits

| Model | Context window | Max output tokens |
|---|---:|---:|
| `mimo-v2.5` | 1,000,000 | 128,000 |
| `mimo-v2.5-pro` | 1,048,576 | 128,000 |

### Endpoint routing

All models use the OpenAI-compatible chat completions endpoint:

```
https://token-plan-sgp.xiaomimimo.com/v1/chat/completions
```

---

## ⚙️ Settings

| Setting | Default | Description |
|---|---|---|
| `xiaomi-mimo.temperature` | `0.2` | Sampling temperature (`0` to `2`) |
| `xiaomi-mimo.maxTokens` | `0` | Max output token override (`0` = per-model default) |
| `xiaomi-mimo.maxInputTokens` | `0` | Context window override (`0` = per-model default) |
| `xiaomi-mimo.requestTimeoutSeconds` | `300` | Total request timeout |
| `xiaomi-mimo.streamIdleTimeoutSeconds` | `90` | Cancels if stream goes silent too long |
| `xiaomi-mimo.showUsageStatusBar` | `true` | Show token usage in status bar |
| `xiaomi-mimo.debugLogging` | `false` | Verbose diagnostics to output channel |
| `xiaomi-mimo.freeOnly` | `false` | Show only free MiMo models in picker |

---

## Commands

| Command | What it does |
|---|---|
| `MiMo: Manage Provider` | Manage API key, refresh models, test connection |
| `MiMo: Set API Key` | Store or update your MiMo API key |
| `MiMo: Diagnostics` | Show registered models and recent request summaries |

---

## ❓ FAQ

**Do I need Copilot Pro?**

No. A free GitHub account is enough. You sign in to Copilot Chat with your GitHub account, then select a MiMo model from the picker.

**How much does MiMo cost?**

MiMo runs on a token-based plan. You pay for what you use. Check [xiaomimimo.com](https://xiaomimimo.com) for current pricing. It is significantly cheaper than GPT-4 or Claude for large context tasks.

**Is my API key safe?**

Yes. The key is stored in VS Code's SecretStorage, encrypted by the OS keychain. It never gets sent anywhere except directly to the MiMo API.

**Can I use this without Copilot Chat?**

No. This extension adds models *into* Copilot Chat. You need the GitHub Copilot Chat extension installed and signed in.

**Does it support tool calling / agent mode?**

Yes. Tool schemas are forwarded using the OpenAI-compatible request format.

**What if MiMo API is down?**

The extension keeps a bundled fallback model catalog so the picker stays usable. Requests will fail until the API recovers, with clear error messages.

**Can I use this offline?**

You need internet to send chat requests. The model picker works offline thanks to the bundled catalog.

---

## 🛠️ Development

```bash
npm install
npm run compile      # build
npm run watch        # watch mode
npm run package      # create .vsix
```

Press `F5` in VS Code to launch an Extension Development Host.

---

## 💬 Community

Found a bug or want a feature? [Open an issue](https://github.com/ltmoerdani/xiaomi-mimo-copilot-chat/issues).

Found this useful? Please [star the repo](https://github.com/ltmoerdani/xiaomi-mimo-copilot-chat) and [leave a review](https://marketplace.visualstudio.com/items?itemName=ltmoerdani.xiaomi-mimo-copilot-chat&ssr=false#review-details) on the marketplace. It helps others find it.

### Sibling extensions

- **[OpenCode Copilot Chat](https://marketplace.visualstudio.com/items?itemName=ltmoerdani.opencode-copilot-chat)** - 33+ models (DeepSeek, Kimi, GLM, GPT, Gemini, Grok, free models) in Copilot Chat
- **[Cline Copilot Chat](https://marketplace.visualstudio.com/items?itemName=ltmoerdani.cline-copilot-chat)** - ClinePass models in Copilot Chat

---

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=ltmoerdani/xiaomi-mimo-copilot-chat&type=Date)](https://star-history.com/#repo=ltmoerdani/xiaomi-mimo-copilot-chat&Date)

---

## 📄 License

MIT. See [LICENSE](./LICENSE).

---

<p align="center">
  Built by <a href="https://github.com/ltmoerdani">ltmoerdani</a>. If this helps you, consider giving it a star.
</p>
