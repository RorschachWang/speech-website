# OFFTYPE v1.0.1 发布同步

> 2026-05-05

## 已发布

| 项目 | 值 |
|------|-----|
| 安装包 | https://github.com/RorschachWang/speech-website/releases/download/v1.0.1/OFFTYPE-Setup-1.0.1.exe |
| 大小 | 189 MB |
| SHA256 | `7affe31f816a071b3d4c6ec3ac617885d60c4087cea0548d955a7d8a3c43cf4b` |

## 本次修复

- **VAD 模式崩溃**：Silero VAD 模型要求恰好 512 采样点/帧，DEFAULT_CONFIG 设为 1024 导致每帧抛异常 → 日志爆炸 3.2GB → 系统变慢
- **VADIterator.reset() 崩溃**：已安装版 silero_vad 没有此方法，加 try/except 保护
- **日志轮转**：FileHandler → RotatingFileHandler（10MB × 3），防止日志无限增长
- **websockets 日志静音**：不再刷 DEBUG 级别日志

## 网站侧已更新

- [x] 下载直链指向 v1.0.1
- [x] 7 种语言 changelog 均已添加 v1.0.1 条目
- [x] version.json → version: 2（客户端升级提示）
- [x] Release 上传到 speech-website（公开仓）

## 无需操作

上次 v1.0.0 的更新内容全部保留，本次仅追加 v1.0.1 changelog。下载页、隐私政策、文档等无结构变更。
