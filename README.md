# 🦅 Claude Code: Source Leak Analysis (March 31, 2026)

[![Status](https://img.shields.io/badge/Status-Historical_Record-blue.svg)]()
[![Date](https://img.shields.io/badge/Date-March_31,_2026-orange.svg)]()
[![Type](https://img.shields.io/badge/Type-Human_Error-red.svg)]()

> [!IMPORTANT]
> This repository is a detailed documentation of the event where Anthropic accidentally leaked the full source code for its **Claude Code** CLI tool.

---

### 🌐 Select Your Language / Selecciona tu idioma:
[🇺🇸 English](README.md) | [🇪🇸 Español](README.es.md) | [🇧🇷 Português](README.pt.md) | [🇨🇳 中文](README.zh.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | [🇯🇵 日本語](README.ja.md) | [🇷🇺 Русский](README.ru.md)

---

## 🔍 Incident Overview
On **March 31, 2026**, Anthropic inadvertently included a **59.8 MB** source map file (`cli.js.map`) in the **v2.1.88** release of the `@anthropic-ai/claude-code` package on the npm registry.

The leak was the result of a **packaging error** during the build process. Source maps are designed to map minified production code back to its original source for debugging; by including this file, Anthropic unknowingly provided the "blueprint" for their entire CLI architecture.

### 🛠️ Key Discoveries & Architectural Insights
Analysis of the **1,902 proprietary files** and **512,000 lines of TypeScript** revealed:

*   **KAIROS Orchestration Engine:** The "brain" of Claude Code. It handles advanced agentic behavior, tool-call loops, and complex state management that was previously thought to be handled entirely server-side.
*   **Undercover Mode:** A stealth feature designed for Anthropic employees. It allows the agent to make git contributions (commits/PRs) without automatically tagging them as AI-generated, effectively masking the use of AI in open-source projects.
*   **autoDream (Self-Healing Memory):** A sophisticated subsystem that activates during periods of user inactivity. It compresses past conversation context and "heals" its own memory to maintain maximum efficiency within the token window.
*   **Unreleased Model References:** The code contains explicit calls to internal models like **"Capybara"** (Claude 4.6) and **"Fennec"** (Opus 4.6), suggesting these models were already in active testing.

---

## 📸 Evidence & Documentation
The leak was first identified by security researcher **Chaofan Shou (@Fried_rice)** on X (Twitter).

![Original Tweet](assets/tweet.png)
*Initial discovery by @Fried_rice on X, triggering the global community analysis.*

---

## 📂 Directory Structure
| Path | Description |
| :--- | :--- |
| `source/` | Reconstructed TypeScript source code from the v2.1.88 leak. |
| `assets/` | Visual evidence and screenshots of the incident. |

---

## 🔗 Official Sources & Links
- **Primary Announcement:** [Chaofan Shou's Tweet](https://twitter.com/Fried_rice/status/2038894956459290963)
- **Technical Analysis:** [CyberNews: Anthropic Claude Code Source Leak Explained](https://cybernews.com/security/anthropic-claude-code-source-leak/)
- **Detailed Report:** [VentureBeat: Claude Code Source Leak Analysis](https://venturebeat.com/ai/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know/)

---

## ⚖️ Legal Disclaimer
The code in the `source/` directory is the **proprietary intellectual property of Anthropic**. This repository is for **historical and educational documentation only**. Unauthorized redistribution or commercial use of the leaked code may violate copyright laws and Anthropic's Terms of Service.

---
*Generated with ❤️ to document a milestone in AI development history.*
