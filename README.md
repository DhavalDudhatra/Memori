# Memori

<p align="center">
  <img src="https://raw.githubusercontent.com/MemoriLabs/Memori/main/images/benchmark.png" alt="Memori banner" width="100%" />
</p>

<p align="center">
  <a href="https://memorilabs.ai/">
    <img src="https://img.shields.io/badge/Website-memorilabs.ai-0A84FF?style=for-the-badge&logo=globe&logoColor=white" alt="Website" />
  </a>
  <a href="https://github.com/MemoriLabs/Memori/stargazers">
    <img src="https://img.shields.io/badge/Stars-⭐-FFB000?style=for-the-badge" alt="Stars" />
  </a>
  <a href="https://github.com/MemoriLabs/Memori/issues">
    <img src="https://img.shields.io/badge/Issues-Open-FF5A5F?style=for-the-badge" alt="Issues" />
  </a>
  <a href="https://discord.gg/FpytKAxnFb">
    <img src="https://img.shields.io/badge/Community-Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord" />
  </a>
  <a href="https://github.com/MemoriLabs/Memori/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-Apache%202.0-3A7F0D?style=for-the-badge" alt="License" />
  </a>
</p>

<p align="center">
  <strong>Memory from what agents do, not just what they say.</strong>
</p>

Memori is agent-native memory infrastructure for production AI systems. It turns agent execution and conversation into persistent, structured memory that is retrieval-ready, LLM-agnostic, and easy to deploy in the environments you already trust.

- Built for enterprise and production workloads
- Works with your existing data stack and deployment model
- Supports multiple LLMs, frameworks, and SDKs
- Captures long-term context without forcing a full app rewrite

<hr>

## Why Memori?

Most AI systems forget between sessions. Memori gives your agents durable memory across users, processes, and sessions.

- Persistent memory across conversations and workflows
- Structured recall for facts, preferences, and context
- Better user experience with reduced repeat questions
- Lower prompt overhead using targeted memory retrieval
- Flexible deployment: cloud, VPC, single-tenant, or on-prem

<hr>

## Core capabilities

<div align="center">
  <img src="https://img.shields.io/badge/LLM%20agnostic-Yes-00C853?style=flat-square" />
  <img src="https://img.shields.io/badge/Frameworks-LangChain%20%7C%20Agno%20%7C%20Pydantic%20AI-2962FF?style=flat-square" />
  <img src="https://img.shields.io/badge/Deployments-Cloud%20%7C%20BYODB%20%7C%20On-prem-FF6D00?style=flat-square" />
  <img src="https://img.shields.io/badge/Memory-Advanced%20Augmentation-7C4DFF?style=flat-square" />
</div>

### Memory concepts

Memori tracks memory at multiple levels:

- Entity: user, customer, or identity
- Process: app, workflow, or agent
- Session: active interaction between the entity and process
- Augmentation: facts, rules, preferences, people, events, and relationships

This enables richer memory behavior without increasing app complexity.

<hr>

## Quick start

### Install

<details>
<summary><b>TypeScript SDK</b></summary>

```bash
npm install @memorilabs/memori
```

</details>

<details>
<summary><b>Python SDK</b></summary>

```bash
pip install memori
```

</details>

### Use it

<details>
<summary><b>TypeScript</b></summary>

```typescript
import { OpenAI } from 'openai';
import { Memori } from '@memorilabs/memori';

const client = new OpenAI();
const mem = new Memori().llm
  .register(client)
  .attribution('user_123', 'support_agent');

async function main() {
  await client.chat.completions.create({
    model: 'gpt-4o-mini',
    messages: [{ role: 'user', content: 'My favorite color is blue.' }],
  });

  const response = await client.chat.completions.create({
    model: 'gpt-4o-mini',
    messages: [{ role: 'user', content: "What's my favorite color?" }],
  });

  console.log(response.choices[0].message.content);
}
```

</details>

<details>
<summary><b>Python</b></summary>

```python
from memori import Memori
from openai import OpenAI

client = OpenAI()
mem = Memori().llm.register(client)
mem.attribution(entity_id="user_123", process_id="support_agent")

client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role": "user", "content": "My favorite color is blue."}],
)

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role": "user", "content": "What's my favorite color?"}],
)
print(response.choices[0].message.content)
```

</details>

<hr>

## Supported ecosystems

### LLMs

- Anthropic
- Bedrock
- DeepSeek
- Gemini
- Grok (xAI)
- OpenAI (Chat Completions & Responses API)

### Frameworks

- Agno
- LangChain
- Pydantic AI

### Platforms

- DeepSeek
- Nebius AI Studio

<hr>

## Product highlights

### Memori Cloud

Zero-config memory service for developers who want a managed, production-ready memory layer.

### BYODB

Bring your own database and deploy in a model that matches your infrastructure requirements.

### MCP integration

Connect Memori to tools like Claude Code, Cursor, Codex, Warp, and other client environments with minimal setup.

### Benchmark results

Memori was evaluated on the LoCoMo benchmark for long-conversation memory and achieved strong retrieval quality while significantly reducing prompt size and cost compared with naive baselines.

<p align="center">
  <a href="https://memorilabs.ai/benchmark">
    <img src="https://raw.githubusercontent.com/MemoriLabs/Memori/main/images/benchmark.png" alt="Memori benchmark results" width="80%" />
  </a>
</p>

<hr>

## Architecture at a glance

```text
User / Agent / App
        │
        ▼
   Memori SDK
        │
        ▼
  Memory Pipeline
  ├─ Attribution
  ├─ Session tracking
  ├─ Memory extraction
  ├─ Retrieval + ranking
  └─ Context recall
        │
        ▼
    LLM / App Runtime
```

<hr>

## Documentation

- [Website](https://memorilabs.ai/)
- [Docs](https://memorilabs.ai/docs/memori-cloud/)
- [BYODB Docs](https://memorilabs.ai/docs/memori-byodb/)
- [Benchmark Overview](https://memorilabs.ai/benchmark)
- [Benchmark Paper](https://arxiv.org/abs/2603.19935)

<hr>

## Community and support

- [Discord](https://discord.gg/FpytKAxnFb)
- [Issues](https://github.com/MemoriLabs/Memori/issues)
- [Contributing Guide](https://github.com/MemoriLabs/Memori/blob/main/CONTRIBUTING.md)

<hr>

## License

Apache 2.0 — see [LICENSE](https://github.com/MemoriLabs/Memori/blob/main/LICENSE).

<p align="center">
  <a href="https://github.com/MemoriLabs/Memori/graphs/contributors">
    <img src="https://contrib.rocks/image?repo=MemoriLabs/Memori" alt="Contributors" />
  </a>
</p>

<p align="center">
  <strong>Built for agents that remember.</strong>
</p>
