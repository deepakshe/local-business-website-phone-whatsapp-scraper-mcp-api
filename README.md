# Local Business Phone & WhatsApp Scraper MCP Server & Python API

[![Apify Store](https://img.shields.io/badge/Apify_Store-Run_on_Apify-blue?style=for-the-badge&logo=apify)](https://apify.com/deepaksheoran172/local-business-website-phone-whatsapp-scraper)
[![MCP Server](https://img.shields.io/badge/MCP-Model_Context_Protocol-purple?style=for-the-badge)](https://modelcontextprotocol.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Hub](https://img.shields.io/badge/Live_Catalog-B2B_Scrapers_Hub-emerald?style=for-the-badge)](https://deepakshe.github.io/b2b-mcp-apify-scrapers-hub/)

> **Extract validated phone numbers, WhatsApp links, and direct contact emails from local business websites. MCP Server & Python SDK.**

---

## ⚡ Instant Normalized Output (Sample JSON)

```json
[
  {
    "website": "https://example-dentist.com",
    "phone_numbers": [
      "+1-555-0199"
    ],
    "whatsapp_urls": [
      "https://wa.me/15550199"
    ],
    "emails": [
      "info@example-dentist.com"
    ]
  }
]
```

---

## ⚡ The Problem vs. The Solution

Scraping local directories often misses direct communication channels. This tool crawls headers, footers, and contact pages using regex and DOM parsing to harvest WhatsApp click-to-chat links, direct landlines, and owner emails.

- **Zero-Proxy Architecture:** Pure asynchronous execution designed for extreme speed (<50MB RAM).
- **Multi-Interface Support:** Run via pure Python SDK, cURL, Node.js fetch, n8n / Make.com workflow, or Claude / Cursor MCP Agent.
- **Production Reliable:** Backed by Apify's serverless infrastructure with 99.9% uptime SLA.

---

## 🚀 Quickstart: 1-Line cURL (Test in 2 Seconds)

```bash
curl -X POST "https://api.apify.com/v2/acts/deepaksheoran172~local-business-website-phone-whatsapp-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{\"websites\": [\"https://example-dentist.com\", \"https://example-plumbing.com\"]}'
```

---

## 🚀 Quickstart: Pure Python (Zero-Dependency)

No third-party SDKs required. Run directly with Python standard library:

```python
import json
import os
import urllib.request

APIFY_TOKEN = os.getenv("APIFY_TOKEN", "YOUR_APIFY_TOKEN")
ACTOR_URL = "https://api.apify.com/v2/acts/deepaksheoran172~local-business-website-phone-whatsapp-scraper/run-sync-get-dataset-items?token=" + APIFY_TOKEN

payload = {
  "websites": [
    "https://example-dentist.com",
    "https://example-plumbing.com"
  ]
}

req = urllib.request.Request(
    ACTOR_URL,
    data=json.dumps(payload).encode("utf-8"),
    headers={"Content-Type": "application/json"},
    method="POST"
)

with urllib.request.urlopen(req, timeout=120) as resp:
    results = json.loads(resp.read().decode("utf-8"))
    print(f"Retrieved {len(results)} items:")
    print(json.dumps(results[:2], indent=2))
```

---

## 🌐 Quickstart: Node.js / TypeScript

```javascript
const APIFY_TOKEN = process.env.APIFY_TOKEN || 'YOUR_APIFY_TOKEN';
const ACTOR_URL = `https://api.apify.com/v2/acts/deepaksheoran172~local-business-website-phone-whatsapp-scraper/run-sync-get-dataset-items?token=${APIFY_TOKEN}`;

const payload = {
  "websites": [
    "https://example-dentist.com",
    "https://example-plumbing.com"
  ]
};

async function run() {
  const res = await fetch(ACTOR_URL, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(payload)
  });
  const items = await res.json();
  console.log(`Received ${items.length} records:`, items.slice(0, 2));
}

run().catch(console.error);
```

---

## 🤖 Claude Desktop & Cursor MCP Server Setup

Add this actor to your `claude_desktop_config.json` to allow Claude / Cursor AI agents to execute it autonomously:

```json
{
  "mcpServers": {
    "local-business-website-phone-whatsapp-scraper": {
      "command": "npx",
      "args": ["-y", "@apify/actors-mcp-server"],
      "env": {
        "APIFY_TOKEN": "YOUR_APIFY_TOKEN",
        "ACTOR_NAME": "deepaksheoran172/local-business-website-phone-whatsapp-scraper"
      }
    }
  }
}
```

---

## 🔄 n8n & Make.com Automation

A fully configured production n8n workflow template is bundled in this repository as [`workflow.json`](./workflow.json).

1. In n8n, click **Workflow** -> **Import from File...** and select `workflow.json`.
2. Provide your `APIFY_TOKEN` in the environment variables or HTTP Request node.
3. Schedule it to run daily or trigger on demand from webhooks.

---

## 📊 Output Schema Highlights

Each returned item includes normalized, RFC-compliant fields:
- `website`
- `phone_numbers`
- `whatsapp_urls`
- `emails`
- `social_profiles`

---

## 🏷️ Pricing & 60% Launch Discount

- **Apify Store:** Available under pay-per-result pricing with a **60% Launch Discount**.
- **Run Online:** Test it instantly on the [Apify Store Console](https://apify.com/deepaksheoran172/local-business-website-phone-whatsapp-scraper).
- **Fleet Hub:** Explore all 62 enterprise scrapers and MCP servers at [b2b-mcp-apify-scrapers-hub](https://deepakshe.github.io/b2b-mcp-apify-scrapers-hub/).

---

## 🛡️ 100% Automated Self-Service & Zero-DM Guarantee

- **Pure Self-Service:** Runs autonomously via Apify Cloud API. No sales calls, manual configuration, or onboarding tickets needed.
- **Pay-Per-Result:** Only successful output items are billed. Zero-charge on failed executions.
- **API Documentation:** For key creation, webhooks, and concurrency settings, see [Apify Docs](https://docs.apify.com/platform/actors/running/api).

---

## 📄 License

MIT License. Free for personal, commercial, and enterprise integration.
