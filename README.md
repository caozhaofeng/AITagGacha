
AITagGacha是一个创新的AI绘画提示词生成工具，目前的功能有:生成对应主题的提示词+随机tag抽取+tag库标签选取+自动分词+模块化修改提示词+翻译

基于googleAI辅助,目前采用deepseek的API，后续打算加入更多API调用

# 🪄 AI Tag Gacha (SD 提示词抽卡神器)




**AI Tag Gacha** 是一款专为 Stable Diffusion (SD) 用户设计的**可视化提示词生成与管理工具**。

它采用“抽卡”的游戏化交互方式，结合 DeepSeek 强大的 AI 能力，帮助你快速生成、管理、翻译和组合复杂的 Prompt。它完全基于单文件 HTML 开发，无需安装 Node.js，**无需构建**，**下载即用**。

<img width="2945" height="1846" alt="image" src="https://github.com/user-attachments/assets/bc650d3b-c5e6-44e6-8959-62b83da4b567" />
<img width="3787" height="1824" alt="image" src="https://github.com/user-attachments/assets/4f9dbff8-046c-412c-9780-8a635307e9c6" />



## ✨ 核心功能 (Features)

* **⚡ 单文件运行 (Zero Setup):** 只有一个 `.html` 文件，双击即可在浏览器运行，无需 Python 或 Node.js 环境。
* **🎲 AI 一键抽卡 (AI Gacha):** 利用 DeepSeek 大模型，根据模糊主题（或完全随机）生成画面感极强的 Prompt。
* **📖 魔导书系统 (Grimoire):** 内置强大的标签库管理系统，支持分类检索、随机抽取、组合扩写。支持导入/导出 JSON 格式的自定义魔导书。
* **🛠️ 可视化编辑器:**
    * 支持**拖拽排序**标签。
    * 可视化调整权重 `(tag:1.2)`。
    * **锁定/解锁**特定槽位（如保留画风，重抽动作）。
* **🌐 智能翻译与解析:**
    * 自动将 AI 生成的英文 Prompt 翻译为中文对照。
    * **智能剪贴板解析**：粘贴一段杂乱的 Prompt，自动按（质量、画风、角色、动作等）分类填入槽位。
* **🎨 现代化 UI:** 基于 Tailwind CSS 的深色模式赛博朋克风格，流畅的动画体验。

## 🚀 快速开始 (Quick Start)

1.  **下载**: 点击本项目右上角的 `Code` -> `Download ZIP`，或者直接下载 `AI提示词抽卡2.1.html` 文件。
2.  **运行**: 直接使用 Chrome / Edge / Firefox 浏览器打开该 `.html` 文件。
3.  **配置 API**:
    * 点击侧边栏的 **设置 (Settings)**或**ESC**。
    * 输入你的 [DeepSeek API Key](https://platform.deepseek.com/)。
    * (可选) 如果有需要，可以修改 API Base URL。
4.  **开始创作**: 点击底部的“一键 AI 抽卡”或侧边栏的“魔导书”开始使用。

## 📖 魔导书 (Grimoire) JSON 格式

你可以创建自己的魔导书 JSON 文件并导入到工具中。标准格式如下：

```json
{
  "name": "我的二次元魔导书",
  "description": "包含常用的动作和服饰",
  "groups": [
    {
      "name": "角色外观",
      "categories": [
        {
          "name": "发型",
          "tags": [
            { "name": "long hair", "keyword": "长发" },
            { "name": "twintails", "keyword": "双马尾" }
          ]
        }
      ]
    }
  ]
}
```






# API 使用获取

### 1. DeepSeek (深度求索)
- **API Base URL:** `https://api.deepseek.com`
- **常用模型 (Model Names):**
  - `deepseek-chat`: (默认) 对应 DeepSeek-V3，不仅便宜且效果极佳，**推荐使用**。
  - `deepseek-reasoner`: 对应 DeepSeek-R1，推理能力强，但生成 creative writing 可能会有较多思考过程。

### 2. Grok (xAI)
- **API Base URL:** `https://api.x.ai/v1`
- **常用模型 (Model Names):**
  - `grok-2-latest`: (**推荐**) 指向最新的 Grok 2 模型。
  - `grok-2`
  - `grok-beta`

### 3. Google Gemini
- **API Base URL:** `https://generativelanguage.googleapis.com/v1beta`
- **常用模型 (Model Names):**
  - `gemini-2.0-flash`: (**推荐**) 速度快且免费额度较高。
  - `gemini-1.5-pro`
  - `gemini-1.5-flash`
  - `gemini-2.0-flash-lite-preview`

### 4. Custom (自定义/OpenAI 兼容)
如果你使用 OneAPI、NewAPI 或其他中转服务：
- **API Base URL:** 通常填写你的中转地址，例如 `https://api.openai.com/v1` 或你的私有域名 `https://my-oneapi.com/v1`。
- **常用模型:** 取决于你中转支持的模型，例如 `gpt-4o`, `claude-3-5-sonnet-20241022` 等。

> **注意：** > * 在设置中填写 URL 时，DeepSeek 和 Grok 通常不需要末尾的斜杠，但代码中已经做了兼容处理。
> * Gemini 的 URL 结构比较特殊，代码中是写死的 REST 风格调用，如果你在自定义 (Custom) 中使用 Gemini 模型（通过 OpenAI 兼容层），URL 通常以 `/v1` 结尾。