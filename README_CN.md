# 📈 股票分析助手 (Stock Analyst v1.3.3)

**Stock Analyst** 是一款专为 AI 智能体（如 OpenClaw/Claude）设计的高精度金融分析引擎。它集成了拥有 20 年经验的高级金融分析师的专业知识，专注于 **美股 (Wall Street)**、**马股 (Bursa Malaysia/KLSE)** 及 **港股 (HKEX)** 市场。

---

## 🚀 核心能力

- **智能市场识别**：支持全球三大主流交易所的 Ticker 自动识别与路由。
- **深度基本面分析**：涵盖 PE、ROE、股息率 (DY)、每股净资产 (NTA)、EPS 及 YoY/QoQ 增长趋势。
- **技术面指标综合**：自动计算支撑/阻力位、RSI、MACD 及移动平均线。
- **机构筹码追踪**：监控马股大股东（如 EPF）动向及内部人士/董事增减持。
- **72 小时催化剂扫描**：从 Seeking Alpha、Finviz 和 KLSE Screener 实时提取重磅新闻。

---

## 🛠 依赖插件与技能

为了发挥最大效能，本技能与以下 OpenClaw 插件深度集成。请使用提供的 **ClawHub** 命令进行安装：

1.  **[multi-search-engine](https://clawhub.ai/gpyangyoujun/multi-search-engine)**：用于抓取宏观经济背景及行业新闻。
    - **安装命令**: `clawhub install gpyangyoujun/multi-search-engine`
2.  **[agent-browser](https://github.com/vercel-labs/agent-browser)**：**强制要求**。用于执行“防幻觉”视觉校验，直接访问交易所网页核实实时成交价与时间戳。
    - **安装命令**: `npm install -g agent-browser && agent-browser install`
3.  **[smart-web-fetch](https://clawhub.ai/jacurtwong/smart-web-fetch)**：用于从 Yahoo Finance、KLSE Screener 等门户高效提取结构化数据。
    - **安装命令**: `clawhub install jacurtwong/smart-web-fetch`

---

## 🔍 分析逻辑：STIP 与三位一体协议

### 1. 智能代码识别协议 (STIP)
引擎根据 Ticker 格式自动路由：
- **马股 (KLSE)**: 4位纯数字 (如 `1155`, `0245`)。
- **美股 (US Markets)**: 1-5位纯字母 (如 `AAPL`, `NVDA`)。
- **港股 (HKEX)**: 5位纯数字 (如 `00700`)。
- *支持显示后缀 (如 `.KL`, `.HK`) 强制指定市场。*

### 2. “三位一体”数据采集
- **马股 (Bursa)**：KLSE Screener (财务) + MalaysiaStock.biz (机构/内部人士追踪) + Yahoo Finance (价格校验)。
- **美股 (NYSE/NASDAQ)**：Yahoo Finance (实时) + Finviz (内部交易/比率) + Seeking Alpha (72h 新闻催化剂)。

### 3. 防幻觉与校准机制
- **视觉二次确认**：若 API 与网页抓取的价格差异 > 1%，引擎将强制通过 `agent-browser` 开启浏览器进行人工级别的视觉校验。
- **时间戳标注**：每份报告均包含强制性的采集时间：`[数据采集时间：YYYY-MM-DD HH:mm:ss]`。

---

## 📱 交互规范 (针对 Telegram 优化)

为确保在移动端拥有最佳阅读体验，输出报告严格遵循以下格式：
- **严禁使用 Markdown 表格**：统一使用清晰的标题与加粗键值对。
- **标准结构**：
    - `### [代码] 分析报告`
    - **基本面亮点** (PE, ROE, DY)
    - **技术面关键位** (支撑位/阻力位)
    - **催化剂总结** (近期新闻)
    - **硬核投资评价** (买入点, 目标价, 止损价)

---

## 📥 安装指南

```bash
# 克隆至您的技能目录
git clone https://github.com/jacurtwong/stock-analyst.git ~/.openclaw/skills/stock-analyst
```

---

## ⚖️ 免责声明
*本工具仅提供基于数据的分析供参考，不构成任何投资建议。在做出投资决策前，请务必进行独立研究。*

---
**维护者: jacurtwong** 🫡
