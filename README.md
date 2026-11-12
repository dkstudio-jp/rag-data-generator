# dkstudio RAG Data Generator

[![Live Demo](https://img.shields.io/badge/Live%20Demo-▶%20Open-cc9966?style=for-the-badge)](https://dkstudio-jp.github.io/rag-data-generator/rag-data-generator.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-7a9085?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Privacy First](https://img.shields.io/badge/Privacy-Local%20Only-5b7d73?style=for-the-badge)](#-privacy-first)
[![No Server](https://img.shields.io/badge/Server-Not%20Required-444?style=for-the-badge)](#-installation)

**For Personal AI Operating System (Personal AI OS)**

A privacy-first, browser-only tool that transforms any text into structured RAG (Retrieval-Augmented Generation) data — ready for AnythingLLM, LM Studio, Ollama, and other Personal AI OS environments.

No server. No account. Your text never leaves your browser.

---

## 🆕 What's new in v3.0.0 — model-agnostic

LLM models and prices change every few months, so v3 no longer ties the tool to specific model names.

- **Usage types instead of model names** — five built-in profiles (cloud high-end / standard / light, local large / small) with typical values
- **Every number is editable** — click ✎ on any profile to enter the real price and context length of the model you actually use
- **Choosing a profile is optional** — chunks do not depend on the model, so you can generate without picking one
- **Context usage check** — shows how much of the context window your top-k setting occupies, with a warning above 50%
- **Named model list is opt-in** — `models.json` is no longer loaded automatically, and its data date is shown when you load it

---

## ✨ What it does

Paste any text → adjust chunk settings → (optionally) compare costs → download RAG-ready data.

```
Your text  →  Chunking  →  Preview  →  Download
(FAQ / Manual / Blog / Docs)     (JSON / JSONL / Markdown / CSV / ...)
```

The tool helps you understand how your text will behave inside a RAG system before you commit to an embedding API, and gives you a rough idea of what it will cost.

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
- **API keys** (optional, for fetching model lists) are stored in your browser's `localStorage` only
- **Privacy Mode** — toggle ON to auto-delete everything when you close the tab
- **Clear All button** — removes all data, API keys, edited values, and loaded model lists instantly

Network requests the page can make, none of which include your text:

- [SheetJS](https://sheetjs.com/) from a CDN (for Excel export)
- A check for a local Ollama server at `localhost:11434`
- `models.json` from this repository — only after you choose to load it
- Provider model-list APIs — only when you enter your own API key and click Fetch

> ⚠️ If you are processing personal or sensitive data, please use the **Clear All** button after use. dkstudio accepts no responsibility for any damages arising from use of this service.

---

## 🚀 How to Use

**Step 1 — Choose a usage type (optional)**
Pick the profile closest to the model you plan to use, or skip this step entirely.
Click ✎ to replace the typical values with real ones, or use "＋ Manual" to add your own profile.
Up to four profiles can be compared side by side.

**Step 2 — Paste your text and adjust**
Paste any text. Adjust chunk size, overlap, and top-k with live preview.
Character count and estimated token count update instantly.

**Step 3 — Check cost and generate**
See the cost-efficiency grade and context usage for each profile in the comparison.
Select an output format and download your RAG data.

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

When no profile is selected, the metadata records `"model": "any"`.

---

## 🧩 Model-agnostic profiles

### Built-in usage types

| Type | Input $/MTok | Output $/MTok | Context | Typical use |
|---|---|---|---|---|
| **Cloud · High-end** | 5.00 | 25.00 | 200K | Accuracy-critical work |
| **Cloud · Standard** | 2.50 | 12.00 | 200K | Balanced everyday use |
| **Cloud · Light** | 0.30 | 1.50 | 128K | Bulk documents, always-on services |
| **Local · Large** | Free | Free | 32K | Large models on your own machine |
| **Local · Small** | Free | Free | 8K | Small models on ordinary hardware |

These are **typical ballpark values, not any vendor's price list**. Check your provider's current pricing and edit the numbers with ✎.

### Other ways to add profiles

- **Manual** — add any model with your own cost, context length, speed, and quality values
- **Ollama** — locally installed models are detected automatically
- **API fetch** — list the models currently offered by OpenAI, Google, or Mistral using your own API key. Prices are not available from these APIs, so typical values are guessed from the model name and marked as such
- **`models.json`** — load a list of named models from a URL, a file, or this repository

### About `models.json`

`models.json` in this repository is an optional, community-maintained list of named models. It is not loaded unless you ask for it, and the tool shows the list's `updated` date so you can judge how current it is. Pull requests to update it are welcome.

```json
{
  "updated": "2026-05-20",
  "models": [
    {
      "id": "example-model",
      "provider": "custom",
      "name": "Example Model",
      "inP": 1.00, "outP": 3.00,
      "ctx": 128000,
      "speed": 80, "quality": 85,
      "tags": ["Example"],
      "desc": { "ja": "説明", "en": "Description" }
    }
  ]
}
```

---

## 📊 Cost Efficiency Grading

The grade is calculated from a blended price: `input × 0.7 + output × 0.3` (USD per million tokens).

| Grade | Blended price | Best for |
|---|---|---|
| **S** | Free or < $0.50 | High-volume, always-on services |
| **A** | $0.50 – $3.00 | Balanced everyday use |
| **B** | $3.00 – $8.00 | High-quality production |
| **C** | $8.00 – $20.00 | Maximum quality |
| **D** | ≥ $20.00 | Research, special cases |

Token counts are rough estimates (characters ÷ 3). Japanese text usually uses more tokens than this, so treat costs as a lower bound.

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
├── models.json                # Optional list of named models (opt-in)
└── README.md                  # This file
```

The application is one file. No build step, no dependencies, no Node.js.

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

### v3.0.0 の変更点 — モデルを限定しない仕様に

LLMのモデルと価格は数か月で入れ替わるため、v3 では特定のモデル名に依存しない作りに変えました。

- モデル名ではなく **利用タイプ**（クラウド高性能・標準・軽量、ローカル大型・小型）から選択
- 数値は目安値で、**✎ から実際の単価・コンテキスト長に書き換え可能**
- タイプの選択は任意。**選ばなくても生成できます**
- top-k の設定がコンテキスト長をどれだけ占めるかを表示し、50%を超えると警告
- 具体的なモデル一覧（`models.json`）は**任意の読み込み**になり、データ更新日を表示

### 特長

- サーバー不要・アカウント不要
- 入力テキストは外部に送信されません
- 最大4つのプロファイルでコスパを並べて比較
- JSON・JSONL・Markdown・CSV・XLSX・XML・YAML・TXT の8形式で出力
- 日本語・英語 UI 切り替え対応

組み込みの数値は各社の価格表ではなく、おおよその目安です。実際に使うモデルの価格を確認して書き換えてください。トークン数は「文字数÷3」の概算で、日本語では実際より少なめに出ます。

MITライセンスで公開しています。使用・改変・再配布自由です。
クレジット表記は法的義務ではありませんが、とても励みになります。

---

*Made with care by [dkstudio](https://dkstudio.jp) — Niigata, Japan*
