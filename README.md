# Bocha Agent Skills (博查智能体技能库)

[![Bocha API](https://img.shields.io/badge/API-Bocha-blue)](https://api.bocha.cn)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

[English](README_EN.md) | 简体中文

欢迎来到 **Bocha Agent Skills** 仓库！这是由 **Bocha Labs** 官方维护的智能体技能集合。旨在为大语言模型 (LLM) 和智能体 (Agents) 提供强大的外部能力，如实时联网搜索等。

我们的官网：[https://open.bocha.cn](https://open.bocha.cn)
获取 API KEY：[https://open.bocha.cn/api-keys](https://open.bocha.cn/api-keys)

## 🚀 什么是这些技能？

这些技能是预定义的工具指令（通常以 `SKILL.md` 格式编写），你可以轻松地将它们导入到 **ClawHub** 等平台或任何自定义的智能体框架中。它们提供了清晰的中英双语系统提示词、API 配置和工作流程指令，确保 LLM 能够准确高效地与博查 API 交互。

## 📦 包含的技能

| 技能名称 | 描述 | 链接 |
|----------|------|------|
| **bocha-web-search** | 默认的博查 Web 搜索工具。适用于在线查询、事实核查和提供带引用的回答。 | [查看技能](./bocha-web-search/SKILL.md) |
| **bocha-web-search-A2M** | 针对 A2M 场景专门优化的博查 Web 搜索变体。 | [查看技能](./bocha-web-search-A2M/SKILL.md) |

*(更多技能即将推出...)*

## 🛠️ 如何使用

1. **获取 API Key**: 你需要一个 `BOCHA_API_KEY` 才能使用这些技能。请前往 [博查开发者平台](https://api.bocha.cn) 获取。
2. **导入技能**: 复制你所需技能文件夹中的 `SKILL.md` 内容，并将其粘贴到你的智能体指令/工具配置中。
3. **配置环境**: 确保你的智能体运行环境中已配置 `BOCHA_API_KEY` 环境变量。

## 🤝 贡献与反馈

欢迎提交 Issue 和 PR！如果您对新技能有任何想法或建议，请随时参与贡献。
## 📄 开源协议 (License)

本项目基于 [MIT License](LICENSE) 协议开源。

