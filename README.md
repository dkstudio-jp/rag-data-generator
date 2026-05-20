# dkstudio RAG Data Generator

[![Live Demo](https://img.shields.io/badge/Live%20Demo-▶%20Open-cc9966?style=for-the-badge)](https://dkstudio-jp.github.io/rag-data-generator/rag-data-generator.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-7a9085?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Privacy First](https://img.shields.io/badge/Privacy-Local%20Only-5b7d73?style=for-the-badge)](#-privacy-first)
[![No Server](https://img.shields.io/badge/Server-Not%20Required-444?style=for-the-badge)](#-installation)

**For Personal AI Operating System (Personal AI OS)**

A privacy-first, browser-only tool that transforms any text into structured RAG (Retrieval-Augmented Generation) data — ready for AnythingLLM, LM Studio, Ollama, and other Personal AI OS environments.

No server. No account. No data leaves your browser.

---

## ✨ What it does

Paste any text → choose your LLM → adjust chunk settings → download RAG-ready data.

```
Your text  →  Chunking  →  Preview  →  Download
(FAQ / Manual / Blog / Docs)     (JSON / JSONL / Markdown / CSV / ...)
```

The tool helps you understand how your text will behave inside a RAG system before you commit to an embedding API, and shows you the real cost of doing so.

---

## 🤖 Compatible Personal AI OS

| System | Recommended Format |
|---|---|
| **AnythingLLM** | JSON, TXT |
| **LM Studio** | JSONL, TXT |
| **Ollama** | JSON, JSONL |
| **LangChain** | JSON, JSONL |
| **LlamaIndex** | JSONL |
| **ChromaDB / Pinecone / Qdrant** | JSONL |
| **Obsidian** | Markdown |
| **Notion AI** | Markdown |
| **Enterprise systems** | XML, XLSX |

---

## 🔒 Privacy First

This tool was designed with privacy as a core principle — not an afterthought.

- **All processing is local** — your text never leaves your browser
- **No server, no tracking, no analytics**
- **API keys** (optional, for model list updates) are stored in your browser's `localStorage` only
- **Privacy Mode** — toggle ON to auto-delete everything when you close the tab
- **Clear All button** — removes all data, API keys, and cached models instantly

> ⚠️ If you are processing personal or sensitive data, please use the **Clear All** button after use. dkstudio accepts no responsibility for any damages arising from use of this service.

---

## 🚀 How to Use

**Step 1 — Choose your LLM**
Select from 15+ curated models across Anthropic, OpenAI, Google, Mistral, and Meta.
See real-time cost, speed, and quality scores. Optionally fetch live model lists using your own API key.
Ollama local models are auto-detected.

**Step 2 — Paste your text and adjust**
Paste any text. Adjust chunk size, overlap, and top-k with live preview.
Character count and estimated token count update instantly.

**Step 3 — Check cost and generate**
See the cost efficiency grade (S / A / B / C) for your chosen model.
Select output format and download your RAG data.

---

## 📦 Output Formats

| Format | Best for |
|---|---|
| **JSON** ⭐ | AnythingLLM, LangChain, universal |
| **JSONL** ⭐ | LlamaIndex, ChromaDB, Pinecone, Qdrant |
| **Markdown** ⭐ | Obsidian, Notion, human review |
| **TXT** | Maximum compatibility |
| **CSV** | Spreadsheet review and analysis |
| **XLSX** | Detailed analysis with metadata sheet |
| **XML** | Enterprise / SharePoint / Confluence |
| **YAML** | Haystack, config-based pipelines |

---

## 🤖 Supported LLMs

### Cloud (auto-updated via API key)

| Provider | Models |
|---|---|
| **Anthropic** | Claude Opus 4.7, Sonnet 4.6, Haiku 4.5 (curated) |
| **OpenAI** | GPT-4o, GPT-4o mini, o3, o4-mini (live fetch) |
| **Google** | Gemini 2.5 Pro, Flash, Flash-Lite (live fetch) |
| **Mistral** | Mistral Large, Small (live fetch) |

### Local (auto-detected)

- **Ollama** — all locally installed models detected automatically
- **Meta Llama** — Llama 3.3 70B, Llama 3.2 3B
- **Qwen** — Qwen 2.5 14B
- **Custom** — add any model manually with your own cost / speed / quality values

---

## 📊 Cost Efficiency Grading

| Grade | Cost (input $/MTok) | Best for |
|---|---|---|
| **S** | Free or < $0.50 | High-volume, always-on services |
| **A** | $0.50 – $3.00 | Balanced everyday use |
| **B** | $3.00 – $8.00 | High-quality production |
| **C** | > $8.00 | Research, maximum quality |

---

## 🛠 Installation

No installation required. This is a single self-contained HTML file.

**Option A — Direct use**
Download `rag-data-generator.html` and open it in any modern browser.

**Option B — Host on your server**
Upload to any web server. No backend required.
```
/your-site/
  rag-data-generator.html   ← drop it anywhere
```

**Option C — GitHub Pages**
Fork this repo and enable GitHub Pages. Live at:
`https://yourusername.github.io/rag-data-generator/rag-data-generator.html`

---

## 📁 File Structure

```
rag-data-generator/
├── rag-data-generator.html    # Complete application (single file)
└── README.md                  # This file
```

Everything is in one file. No build step, no dependencies, no Node.js.

The only external resource loaded is [SheetJS](https://sheetjs.com/) (CDN, for Excel export).

---

## 🏗 Pro Version (Coming Soon)

A PHP server-side version for production deployment is in development:

- **Persistent knowledge base** — SQLite storage with full CRUD
- **Gemini / Claude Embedding API** — auto-vectorize on upload
- **Vector search** — cosine similarity in pure PHP
- **Admin panel** — manage entries without code
- **Multi-user support** — session-based isolation
- **API endpoint** — drop-in backend for AnythingLLM and LangChain

Built for Sakura Internet and similar shared hosting environments.

Interested? → [dkstudio.jp](https://dkstudio.jp)

---

## 📝 License

MIT License — Copyright (c) 2026 dkstudio

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

**The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.**

The Software is provided "as is", without warranty of any kind.

### Credit Request

This is not a legal requirement — just a kind ask.

If you use this tool in a project, article, video, or product, a mention like one of these would mean a lot:

```
Powered by dkstudio RAG Data Generator (github.com/dkstudio-jp/rag-data-generator)
```
```
RAG data generated with dkstudio RAG Data Generator — MIT License
```

---

## 🌐 Links

- **Live Demo** — [dkstudio-jp.github.io/rag-data-generator](https://dkstudio-jp.github.io/rag-data-generator/rag-data-generator.html)
- **Website** — [dkstudio.jp](https://dkstudio.jp)
- **GitHub** — [github.com/dkstudio-jp](https://github.com/dkstudio-jp)

---

## 日本語

**dkstudio RAG Data Generator** は、テキストをRAGデータに変換するプライバシーファーストのブラウザツールです。

AnythingLLM・LM Studio・Ollamaなどの **Personal AI OS** 向けに設計されています。

- サーバー不要・アカウント不要
- 入力テキストは外部に送信されません
- 15以上のLLMのコスパをリアルタイムで比較
- JSON・JSONL・Markdown・CSV・XLSX・XML・YAML・TXT の8形式で出力
- 日本語・英語 UI 切り替え対応

MITライセンスで公開しています。使用・改変・再配布自由です。
クレジット表記は法的義務ではありませんが、とても励みになります。

---

*Made with care by [dkstudio](https://dkstudio.jp) — Niigata, Japan*
