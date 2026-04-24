# Bocha Skills 博查技能库

[![Bocha API](https://img.shields.io/badge/API-Bocha-blue)](https://open.bocha.cn)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)

[English](README_EN.md) | 简体中文

欢迎来到 **Bocha Skills** 仓库！本仓库由 **Bocha Labs** 官方维护，致力于为大语言模型（LLM）和各类智能体（Agents）提供强大的外部能力支持，例如实时联网搜索等。

我们的官网：[https://open.bocha.cn](https://open.bocha.cn)
获取 API KEY：[https://open.bocha.cn/api-keys](https://open.bocha.cn/api-keys)

## 🚀 技能库简介

技能（Skill）本质上是预定义的工具指令（通常以 `SKILL.md` 的形式呈现）。你可以非常方便地将它们接入到 **ClawHub** 等平台，或是你自定义的智能体框架中。

本仓库内的技能内置了经过优化的中英双语系统提示词（Prompt）、API 接入规范以及标准工作流，能够确保大模型准确、高效地调用博查 API。

## 📦 现有技能列表

| 技能名称 | 描述 | 链接 |
|----------|------|------|
| **bocha-web-search** | 博查默认的 Web 搜索工具。适用于在线资料查询、事实核查，以及生成带有信息来源引用的回答。 | [查看技能](./bocha-web-search/SKILL.md) |
| **bocha-web-search-A2M** | 专为 A2M（Agent-to-Machine，智能体与机器通信）场景优化的 Web 搜索版本。 | [查看技能](./bocha-web-search-A2M/SKILL.md) |

*(更多技能持续更新中...)*

## 🛠️ 快速上手

1. **获取 API Key**：在使用技能前，你需要拥有一个 `BOCHA_API_KEY`。请前往 [博查开放平台](https://open.bocha.cn) 免费申请。
2. **导入技能配置**：找到你需要的技能目录，复制其中的 `SKILL.md` 文件内容，将其粘贴到你的智能体指令或工具配置区域。
3. **配置环境变量**：请确保你的智能体运行环境中，已正确配置 `BOCHA_API_KEY` 环境变量。

## 🤝 参与贡献

如果你对现有技能有任何优化建议，或是希望贡献新的技能，欢迎随时提交 Issue 或 Pull Request！

## 📄 开源协议
 
 本项目基于 [Apache License 2.0](LICENSE) 协议开源。
