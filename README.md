# 👓 MARVIS — AI-Powered Smart Specs Handyman Assistant with Scanner & Voice Input

> **1st Place Winner - Mentra Track @ HackMIT 2025**  
> Hands-free augmented reality (AR) assembly and repair guide powered by barcode scanning, voice controls, and multi-LLM orchestration.

---

## 🌟 Overview

**Marvis** transforms smart glasses into an intelligent, hands-free handyman assistant. Whether assembling IKEA furniture, building complex Lego sets, or repairing household appliances, Marvis eliminates the hassle of flipping through physical manuals. 

Simply scan a product barcode through your camera or smart glasses, and Marvis automatically identifies the product, searches the web for official PDF manuals, extracts action-oriented assembly steps using AI, and presents them in an interactive AR overlay with voice navigation.

---

## ✨ Key Features

- 📷 **Barcode & Computer Vision Scanning**: Instantly scans product barcodes from physical packaging or devices.
- ⚡ **Ultra-Fast Product Identification**: Uses **Cerebras Llama 3.1 8B** for instant product title mapping.
- 🔍 **Automated Manual Search**: Searches Google via **SerpAPI / Exa** to discover official instruction manuals and PDFs.
- 🧠 **AI Instruction Generation**: Leverages **Anthropic Claude 3** to parse complex PDF manuals into concise, action-oriented AR steps.
- 👓 **MentraOS Smart Glasses Integration**: Displays real-time step guidance directly on the smart glasses Heads-Up Display (HUD).
- 🎤 **Voice Command Navigation**: Voice-activated step control ("Next step", "Previous step", "Repeat instruction", "I need help").
- 🌐 **Web Dashboard & Photo Viewer**: Includes live web management interfaces at `/webview` and `/photo-viewer`.
- ☁️ **AWS S3 Persistence**: Saves instruction history and metadata (`informationlive.json`) to cloud storage.

---

## 🚀 How It Works (The AI Pipeline)

```
[📷 Barcode Scan] -> [⚡ Cerebras LLM ID] -> [🔍 SerpAPI PDF Search] -> [🧠 Claude AI Parsing] -> [👓 AR HUD & Voice Guidance]
```

1. **Scan Barcode**: Camera captures product barcode.
2. **Identify Product**: Cerebras LLM returns the exact product title.
3. **Fetch Manual**: SerpAPI queries Google for the official PDF instruction manual.
4. **Generate Steps**: Anthropic Claude extracts step-by-step instructions optimized for HUD rendering.
5. **Guide User**: Smart glasses render AR instructions with voice feedback.

---

## 🛠️ Tech Stack

| Layer | Technology | Description |
| :--- | :--- | :--- |
| **Runtime & Language** | Node.js (v18+) / Bun, TypeScript | Core application logic and async handling |
| **Web Server** | Express.js, EJS | REST API routing and dashboard rendering |
| **Smart Glasses SDK** | `@mentra/sdk` (MentraOS) | AR display layout and voice transcription |
| **AI Processing** | Anthropic Claude 3, Cerebras Llama 3.1 | Instruction parsing & fast product identification |
| **Search Engine** | SerpAPI, Exa AI | Google search integration for PDF manuals |
| **Cloud Storage** | AWS S3 | Project state & live metadata storage |

---

## 📦 Setup & Local Execution

### Prerequisites
- Node.js (v18+) or Bun (v1.0+)
- npm or bun

### 1. Installation
```bash
git clone https://github.com/dhavajsjain15/MARVIS-SMART-SPECS-WITH-SCANNER-AND-VOICE-INPUT.git
cd MARVIS-SMART-SPECS-WITH-SCANNER-AND-VOICE-INPUT
npm install
```

### 2. Environment Setup
Copy `.env.example` to `.env` and fill in your API credentials:
```bash
cp .env.example .env
```

**Required `.env` Configuration:**
```env
MENTRAOS_API_KEY=your_mentra_api_key
PACKAGE_NAME=com.marvis.hackmit2025
ANTHROPIC_API_KEY=your_anthropic_api_key
CEREBRAS_API_KEY=your_cerebras_api_key
SERPAPI_KEY=your_serpapi_key
PORT=3001
NODE_ENV=development
```

### 3. Run Development Server
```bash
npm run dev   # Or npx tsx src/index.ts
```

---

## 🌐 Web Dashboards

Once running locally on port `3001`:
- 📊 **Main Web Dashboard**: [http://localhost:3001/webview](http://localhost:3001/webview)
- 📷 **Live Photo Viewer**: [http://localhost:3001/photo-viewer](http://localhost:3001/photo-viewer)

---

## 📜 License & Credits

- Created for **HackMIT 2025** (1st Place Mentra Track).
- Licensed under the **MIT License**.
