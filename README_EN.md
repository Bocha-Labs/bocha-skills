# Bocha Skills

[![Bocha API](https://img.shields.io/badge/API-Bocha-blue)](https://open.bocha.cn)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)

English | [简体中文](README.md)

Welcome to the **Bocha Skills** repository, officially maintained by **Bocha Labs**. This project aims to empower Large Language Models (LLMs) and AI agents with powerful external capabilities, such as real-time web search.

Our Official Site: [https://open.bocha.cn](https://open.bocha.cn)
Get your API KEY: [https://open.bocha.cn/api-keys](https://open.bocha.cn/api-keys)

## 🚀 About Agent Skills

An Agent Skill is essentially a set of predefined tool instructions, typically provided as a `SKILL.md` file. You can easily integrate them into platforms like **ClawHub** or your own custom agent frameworks.

These skills include highly optimized bilingual (English/Chinese) system prompts, standard API configurations, and clear workflow guidelines. This ensures that your LLMs can interact with Bocha APIs accurately and efficiently.

## 📦 Skill Directory

| Skill Name | Description | Link |
|------------|-------------|------|
| **bocha-web-search** | The default web search tool powered by Bocha. Ideal for online information retrieval, fact-checking, and generating answers with source citations. | [View Skill](./bocha-web-search/SKILL.md) |
| **bocha-web-search-A2M** | A specialized variant of the web search tool, optimized specifically for A2M (Agent-to-Machine) scenarios. | [View Skill](./bocha-web-search-A2M/SKILL.md) |

*(More skills coming soon...)*

## 🛠️ Quick Start

1. **Get an API Key**: To use these skills, you first need a `BOCHA_API_KEY`. You can easily obtain one for free from the [Bocha Open Platform](https://open.bocha.cn).
2. **Import Skill Configuration**: Navigate to the specific skill folder you need, copy the contents of the `SKILL.md` file, and paste it into your agent's system prompt or tool configuration section.
3. **Set Environment Variables**: Make sure that the `BOCHA_API_KEY` is properly set in your agent's execution environment.

## 🤝 Contributing

We highly encourage community contributions! Whether you have suggestions for existing skills or want to propose new ones, feel free to open an Issue or submit a Pull Request.

## 📄 License
 
 This project is licensed under the [Apache License 2.0](LICENSE).
