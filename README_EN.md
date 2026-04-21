# Bocha Agent Skills

[![Bocha API](https://img.shields.io/badge/API-Bocha-blue)](https://open.bocha.cn)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

English | [简体中文](README.md)

Welcome to the **Bocha Agent Skills** repository! This is the official collection of Agent Skills maintained by **Bocha Labs**, designed to empower Large Language Models (LLMs) and intelligent agents with robust external capabilities like real-time web search.

Our Official Site：[https://open.bocha.cn](https://open.bocha.cn)
Get your API KEY：[https://open.bocha.cn/api-keys](https://open.bocha.cn/api-keys)

## 🚀 What are these skills?

These skills are predefined tool instructions (usually written in `SKILL.md` format) that you can easily import into platforms like **ClawHub** or any custom agent framework. They provide clear, bilingual (English/Chinese) system prompts, API configurations, and workflow instructions to ensure the LLM interacts with Bocha APIs correctly and efficiently.

## 📦 Available Skills

| Skill Name | Description | Link |
|------------|-------------|------|
| **bocha-web-search** | The default web search skill using Bocha Web Search API. Designed for online lookup, fact-checking, and citation-based answers. | [View Skill](./bocha-web-search/SKILL.md) |
| **bocha-web-search-A2M** | A specialized web search variant optimized for A2M (Agent-to-Machine) communication scenarios. | [View Skill](./bocha-web-search-A2M/SKILL.md) |

*(More skills coming soon...)*

## 🛠️ How to Use

1. **Obtain an API Key**: You need a `BOCHA_API_KEY` to use these skills. Get yours at the [Bocha Open Platform](https://open.bocha.cn).
2. **Import the Skill**: Copy the content of the `SKILL.md` file from the desired skill folder and paste it into your agent's instruction/tool configuration.
3. **Configure Environment**: Ensure your agent runtime has the `BOCHA_API_KEY` configured in its environment variables.

## 🤝 Contributing

We welcome issues and pull requests! If you have ideas for new skills or improvements, please feel free to contribute.

## 📄 License

This project is licensed under the [MIT License](LICENSE).

