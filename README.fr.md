# 🦅 Claude Code : Analyse de la Fuite du Code Source (31 mars 2026)

[![Statut](https://img.shields.io/badge/Statut-Archive_Historique-blue.svg)]()
[![Date](https://img.shields.io/badge/Date-31_mars_2026-orange.svg)]()
[![Type](https://img.shields.io/badge/Type-Erreur_Humaine-red.svg)]()

> [!IMPORTANT]
> Ce dépôt est une documentation détaillée de l'événement où Anthropic a accidentellement divulgué le code source complet de son outil CLI **Claude Code**.

---

### 🌐 Sélectionnez votre langue / Select Your Language :
[🇺🇸 English](README.md) | [🇪🇸 Español](README.es.md) | [🇧🇷 Português](README.pt.md) | [🇨🇳 中文](README.zh.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | [🇯🇵 日本語](README.ja.md) | [🇷🇺 Русский](README.ru.md)

---

## 🔍 Résumé de l'Incident
Le **31 mars 2026**, Anthropic a par mégarde inclus un fichier de carte source (source map) de **59,8 Mo** (`cli.js.map`) dans la version **v2.1.88** du paquet `@anthropic-ai/claude-code` sur le registre npm.

La fuite est le résultat d'une **erreur d'empaquetage** lors du processus de build. Les cartes sources sont conçues pour mapper le code de production minifié vers sa source originale pour le débogage ; en incluant ce fichier, Anthropic a fourni sans le savoir le "plan" de toute son architecture CLI.

### 🛠️ Découvertes Clés et Perspectives Architecturales
L'analyse des **1 902 fichiers propriétaires** et des **512 000 lignes de TypeScript** a révélé :

*   **Moteur d'Orchestration KAIROS :** Le "cerveau" de Claude Code. Il gère les comportements agentiques avancés, les boucles d'appels d'outils et une gestion d'état complexe que l'on pensait auparavant être gérée entièrement côté serveur.
*   **Mode Undercover (Sous Couverture) :** Une fonctionnalité de discrétion conçue pour les employés d'Anthropic. Elle permet à l'agent d'effectuer des contributions git (commits/PRs) sans les marquer automatiquement comme générées par IA, masquant ainsi l'utilisation de l'IA dans les projets open-source.
*   **autoDream (Mémoire d'Auto-Guérison) :** Un sous-système sophistiqué qui s'active pendant les périodes d'inactivité de l'utilisateur. Il compresse le contexte des conversations passées et "guérit" sa propre mémoire pour maintenir une efficacité maximale dans la fenêtre de jetons.
*   **Références à des Modèles non Lancés :** Le code contient des appels explicites à des modèles internes tels que **"Capybara"** (Claude 4.6) et **"Fennec"** (Opus 4.6), suggérant que ces modèles étaient déjà en phase de test actif.

---

## 📸 Preuves et Documentation
La fuite a été initialement identifiée par le chercheur en sécurité **Chaofan Shou (@Fried_rice)** sur X (Twitter).

![Tweet Original](assets/tweet.png)
*Découverte initiale par @Fried_rice sur X, déclenchant l'analyse de la communauté mondiale.*

---

## 📂 Structure du Répertoire
| Chemin | Description |
| :--- | :--- |
| `source/` | Code source TypeScript reconstruit à partir de la fuite v2.1.88. |
| `assets/` | Preuves visuelles et captures d'écran de l'incident. |

---

## 🔗 Sources Officielles et Liens
- **Annonce Primaire :** [Tweet de Chaofan Shou](https://twitter.com/Fried_rice/status/2038894956459290963)
- **Analyse Technique :** [CyberNews : La fuite du code source d'Anthropic Claude Code expliquée](https://cybernews.com/security/anthropic-claude-code-source-leak/)
- **Rapport Détaillé :** [VentureBeat : Analyse de la fuite du code source de Claude Code](https://venturebeat.com/ai/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know/)

---

## ⚖️ Mentions Légales
Le code présent dans le répertoire `source/` est la **propriété intellectuelle exclusive d'Anthropic**. Ce dépôt est destiné uniquement à une **documentation historique et éducative**. La redistribution non autorisée ou l'utilisation commerciale du code fuité peut enfreindre les lois sur le droit d'auteur et les conditions d'utilisation d'Anthropic.

---
*Généré avec ❤️ pour documenter une étape marquante de l'histoire du développement de l'IA.*
