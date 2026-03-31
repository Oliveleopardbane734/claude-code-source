# 🦅 Claude Code: ソースコード漏洩分析 (2026年3月31日)

[![ステータス](https://img.shields.io/badge/ステータス-歴史的記録-blue.svg)]()
[![日付](https://img.shields.io/badge/日付-2026年3月31日-orange.svg)]()
[![タイプ](https://img.shields.io/badge/タイプ-人為的ミス-red.svg)]()

> [!IMPORTANT]
> このリポジトリは、Anthropicが自社のCLIツール **Claude Code** の完全なソースコードを誤って漏洩させた事件の詳細な記録です。

---

### 🌐 言語を選択 / Select Your Language:
[🇺🇸 English](README.md) | [🇪🇸 Español](README.es.md) | [🇧🇷 Português](README.pt.md) | [🇨🇳 中文](README.zh.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | [🇯🇵 日本語](README.ja.md) | [🇷🇺 Русский](README.ru.md)

---

## 🔍 事件の概要
**2026年3月31日**、Anthropicはnpmレジストリ上の `@anthropic-ai/claude-code` パッケージの **v2.1.88** リリースにおいて、不注意にも **59.8 MB** のソースマップファイル (`cli.js.map`) を含めてしまいました。

この漏洩は、ビルドプロセス中の**パッケージングミス**の結果でした。ソースマップは、デバッグのために難読化されたプロダクションコードをオリジナルのソースにマッピングするように設計されていますが、このファイルを含めることで、Anthropicは知らず知らずのうちにCLIアーキテクチャ全体の「設計図」を提供してしまいました。

### 🛠️ 主な発見とアーキテクチャの洞察
**1,902個の専有ファイル**と **512,000行のTypeScript** の分析により、以下が明らかになりました：

*   **KAIROSオーケストレーション・エンジン：** Claude Codeの「脳」にあたる部分。高度なエージェント動作、ツール呼び出しループ、および従来は完全にサーバー側で処理されていると考えられていた複雑な状態管理を処理します。
*   **アンダーカバー・モード (Undercover Mode)：** Anthropic従業員向けに設計されたステルス機能。エージェントがAI生成であることを自動的にタグ付けせずにgit貢献（コミット/PR）を行うことを可能にし、オープンソースプロジェクトでのAIの使用を事実上隠蔽します。
*   **autoDream（自己修復メモリ）：** ユーザーの非アクティブ時にアクティブになる洗練されたサブシステム。過去の会話コンテキストを圧縮し、メモリを「修復」することで、トークンウィンドウ内での効率を最大限に維持します。
*   **未発表モデルの参照：** コード内には、**"Capybara"** (Claude 4.6) や **"Fennec"** (Opus 4.6) といった内部モデルへの明示的な呼び出しが含まれており、これらのモデルがすでにアクティブなテスト段階にあったことを示唆しています。

---

## 📸 証拠とドキュメント
漏洩は、セキュリティ研究者の **Chaofan Shou (@Fried_rice)** 氏によって X (Twitter) 上で最初に特定されました。

![オリジナルのツイート](assets/tweet.png)
*@Fried_rice氏によるX上での最初の発見。これが世界的なコミュニティによる分析の引き金となりました。*

---

## 📂 ディレクトリ構成
| パス | 説明 |
| :--- | :--- |
| `source/` | v2.1.88の漏洩から復元されたTypeScriptソースコード。 |
| `assets/` | 事件の視覚的証拠とスクリーンショット。 |

---

## 🔗 公式ソースとリンク
- **一次発表：** [Chaofan Shou氏のツイート](https://twitter.com/Fried_rice/status/2038894956459290963)
- **技術分析：** [CyberNews: Anthropic Claude Codeのソースコード漏洩解説](https://cybernews.com/security/anthropic-claude-code-source-leak/)
- **詳細レポート：** [VentureBeat: Claude Codeソースコード漏洩分析](https://venturebeat.com/ai/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know/)

---

## ⚖️ 法的免責事項
`source/` ディレクトリ内のコードは **Anthropicの専有的な知的財産** です。このリポジトリは **歴史的および教育的なドキュメントのみ** を目的としています。漏洩したコードの無断再配布や商業利用は、著作権法およびAnthropicの利用規約に違反する可能性があります。

---
*AI開発史における重要なマイルストーンを記録するために、❤️を込めて作成されました。*
