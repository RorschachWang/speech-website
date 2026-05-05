# OFFTYPE（语壳）&middot; Your Voice. Stays Local.

[中文](#chinese) | [English](#english)

---

## 中文

全离线 Windows 语音输入工具。说话自动变文字，无需联网，数据不出你的电脑。

### 核心功能

- **PTT 按键说话**：Ctrl+Space 按住说话，松开上屏
- **VAD 持续监听**：自动检测说话和停顿，逐句上屏
- **翻译模式**：说中文 → 输出英/日/韩/法/西/德文
- **润色模式**：口语 → Formal / Casual / Simple 风格改写
- **自定义词典**：定义人名、术语、缩写

### 技术架构

```
麦克风 → PyAudio
  ↓
VAD 检测 → Silero VAD (silero_vad.onnx)
  ↓
ASR 识别 → sherpa-onnx SenseVoice / Qwen3-ASR
  ↓
LLM 后处理 → llama.cpp Qwen2.5-1.5B 本地 / Ollama Qwen2.5-7B 可选
  ↓
文本注入 → 剪贴板 + Ctrl+V
```

- **Python 后端**：WebSocket 端口 8765，sherpa-onnx + silero_vad + llama-cpp
- **C# WPF 前端**：迷你浮动窗，Acrylic 毛玻璃，系统托盘，全局热键
- **全离线**：ASR、翻译、润色全部本地完成，零外部网络请求

### 模型

| 模型 | 大小 | 说明 |
|------|------|------|
| SenseVoice-Small | 239 MB | 必装，5 语种自动检测 |
| Qwen3-ASR 0.6B | 988 MB | 可选，22 方言 |
| Qwen2.5-1.5B GGUF | 1.04 GB | 可选，本地翻译/润色 |

模型按需下载，HuggingFace 主源 + ModelScope 国内备源，SHA256 校验 + 断点续传。

### 下载

[**下载 OFFTYPE（Windows）**](https://github.com/RorschachWang/speech-website/releases/latest)

### 系统要求

Windows 10/11 x64 · 麦克风 · 2 GB 磁盘空间 · 4 GB 内存

---

## English

Fully offline Windows voice input tool. Speak naturally, and your words appear as text. No internet required. Your voice stays on your machine.

### Features

- **PTT (Push-to-Talk)**：Hold Ctrl+Space, speak, release to type
- **VAD (Voice Activity Detection)**：Continuous listening with auto sentence detection
- **Translate**：Speak Chinese → output in English, Japanese, Korean, French, Spanish, or German
- **Polish**：Rewrite casual speech in Formal / Casual / Simple styles
- **Custom Dictionary**：Define how names, terms, and abbreviations should be written

### Architecture

```
Microphone → PyAudio
  ↓
VAD → Silero VAD
  ↓
ASR → sherpa-onnx SenseVoice / Qwen3-ASR
  ↓
LLM → llama.cpp Qwen2.5-1.5B (local) / Ollama Qwen2.5-7B (optional)
  ↓
Output → Clipboard + Ctrl+V injection
```

- **Python backend**：WebSocket on port 8765, sherpa-onnx + silero_vad + llama-cpp
- **C# WPF frontend**：Mini floating window, acrylic blur, system tray, global hotkey
- **Fully offline**：ASR, translation, and polish all run locally — zero external network requests

### Models

| Model | Size | Notes |
|------|------|-------|
| SenseVoice-Small | 239 MB | Mandatory, 5-language auto-detection |
| Qwen3-ASR 0.6B | 988 MB | Optional, 22 dialect families |
| Qwen2.5-1.5B GGUF | 1.04 GB | Optional, on-device translation/polish |

On-demand download via HuggingFace (primary) + ModelScope (China fallback), with SHA256 verification and resume support.

### Download

[**Download OFFTYPE for Windows**](https://github.com/RorschachWang/speech-website/releases/latest)

### Requirements

Windows 10/11 x64 &middot; Microphone &middot; 2 GB disk &middot; 4 GB RAM

### License

Apache 2.0 / MIT. See LICENSE.txt and NOTICE.txt.
