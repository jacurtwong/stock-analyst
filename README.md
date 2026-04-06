# 📈 Stock Analyst (v1.3.3)

**Stock Analyst** is a high-precision financial analysis engine designed for AI agents (like OpenClaw/Claude). It embodies the expertise of a senior financial analyst with 20 years of experience, specializing in the **US (Wall Street)**, **Malaysia (Bursa Malaysia/KLSE)**, and **Hong Kong (HKEX)** markets.

---

## 🚀 Core Capabilities

- **Market Intelligence**: Real-time Ticker resolution across three major global exchanges.
- **Deep Fundamental Analysis**: PE, ROE, Dividend Yield (DY), NTA, EPS, and YoY/QoQ growth trends.
- **Technical Indicator Synthesis**: Support/Resistance levels, RSI, MACD, and Moving Averages.
- **Institutional Tracking**: Monitoring major shareholders (e.g., EPF in Malaysia) and insider/director trades.
- **72h Catalyst Scanning**: Real-time news extraction from Seeking Alpha, Finviz, and KLSE Screener.

---

## 🛠 Required Skills & Dependencies

To function at full capacity, this skill integrates with the following specialized agent tools:

1.  **[multi-search-engine](https://github.com/openclaw/skills/tree/main/multi-search-engine)**: Used for broad market news and macroeconomic context.
2.  **[agent-browser](https://github.com/openclaw/skills/tree/main/agent-browser)**: **Mandatory** for the *Anti-Hallucination* mechanism. It performs live "Visual Checks" on exchange websites to verify "Last Done Price" and time stamps.
3.  **[smart-web-fetch](https://github.com/openclaw/skills/tree/main/smart-web-fetch)**: Handles robust data extraction from financial portals (Yahoo Finance, KLSE Screener, MalaysiaStock.biz).

---

## 🔍 Analysis Logic: The STIP & Triple-Threat Protocol

### 1. Smart Ticker Identification Protocol (STIP)
The engine automatically routes queries based on ticker format:
- **KLSE (Malaysia)**: 4-digit numeric (e.g., `1155`, `0245`).
- **US Markets**: 1-5 character alpha (e.g., `AAPL`, `NVDA`).
- **HKEX (Hong Kong)**: 5-digit numeric (e.g., `00700`).
- *Supports explicit suffixes (e.g., `.KL`, `.HK`) for override.*

### 2. The "Triple-Threat" Data Sourcing
- **Malaysia (Bursa)**: KLSE Screener (Financials) + MalaysiaStock.biz (Institutional/Insider Tracking) + Yahoo Finance (Validation).
- **US (NYSE/NASDAQ)**: Yahoo Finance (Real-time) + Finviz (Insiders/Ratios) + Seeking Alpha (72h News Catalysts).

### 3. Anti-Hallucination & Calibration
- **Visual Verification**: If a price discrepancy > 1% is detected between APIs and web scrapers, the engine triggers a mandatory manual browser check via `agent-browser`.
- **Fused Reporting**: Every report includes a mandatory timestamp: `[Data Collected: YYYY-MM-DD HH:mm:ss]`.

---

## 📱 Interaction Standards (Optimized for Telegram)

To ensure readability on mobile messaging surfaces, the output follows a strict layout:
- **No Markdown Tables**: Uses clean headers and bold key-value pairs instead.
- **Structure**:
    - `### [Ticker] Analysis Report`
    - **Fundamental Highlights** (PE, ROE, DY)
    - **Technical Levels** (Support/Resistance)
    - **Catalyst Summary** (Recent News)
    - **Hardcore Investment Verdict** (Entry, TP, SL)

---

## 📥 Installation

```bash
# Clone into your skills directory
git clone https://github.com/jacurtwong/stock-analyst.git ~/.openclaw/skills/stock-analyst
```

---

## ⚖️ Disclaimer
*This tool provides data-driven analysis for informational purposes only. It does not constitute financial advice. Always perform your own due diligence before investing.*

---
**Maintained by: jacurtwong** 🫡
