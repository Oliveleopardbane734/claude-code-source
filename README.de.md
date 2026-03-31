# 🦅 Claude Code: Quellcode-Leak-Analyse (31. März 2026)

[![Status](https://img.shields.io/badge/Status-Historisches_Dokument-blue.svg)]()
[![Datum](https://img.shields.io/badge/Datum-31._März_2026-orange.svg)]()
[![Typ](https://img.shields.io/badge/Typ-Menschliches_Versagen-red.svg)]()

> [!IMPORTANT]
> Dieses Repository ist eine detaillierte Dokumentation des Ereignisses, bei dem Anthropic versehentlich den vollständigen Quellcode seines CLI-Tools **Claude Code** geleakt hat.

---

### 🌐 Wählen Sie Ihre Sprache / Select Your Language:
[🇺🇸 English](README.md) | [🇪🇸 Español](README.es.md) | [🇧🇷 Português](README.pt.md) | [🇨🇳 中文](README.zh.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | [🇯🇵 日本語](README.ja.md) | [🇷🇺 Русский](README.ru.md)

---

## 🔍 Vorfallsübersicht
Am **31. März 2026** hat Anthropic versehentlich eine **59,8 MB** große Source-Map-Datei (`cli.js.map`) in der Version **v2.1.88** des Pakets `@anthropic-ai/claude-code` im npm-Register veröffentlicht.

Das Leak war das Ergebnis eines **Verpackungsfehlers** während des Build-Prozesses. Source-Maps sind dafür gedacht, minimierten Produktionscode für das Debugging auf seinen ursprünglichen Quellcode zurückzuführen; durch das Einschließen dieser Datei lieferte Anthropic unwissentlich den „Bauplan“ für ihre gesamte CLI-Architektur.

### 🛠️ Wichtige Entdeckungen & Architektonische Einblicke
Die Analyse der **1.902 proprietären Dateien** und **512.000 Zeilen TypeScript** ergab:

*   **KAIROS Orchestrierungs-Engine:** Das „Gehirn“ von Claude Code. Sie verarbeitet fortgeschrittenes agentisches Verhalten, Tool-Call-Schleifen und komplexes Zustandsmanagement, von dem man bisher dachte, dass es vollständig serverseitig abgewickelt wird.
*   **Undercover-Modus:** Eine Stealth-Funktion für Anthropic-Mitarbeiter. Sie ermöglicht es dem Agenten, Git-Beiträge (Commits/PRs) zu leisten, ohne sie automatisch als KI-generiert zu kennzeichnen, wodurch der Einsatz von KI in Open-Source-Projekten effektiv verschleiert wird.
*   **autoDream (Selbstheilendes Gedächtnis):** Ein hochentwickeltes Subsystem, das sich während Inaktivitätsphasen des Benutzers aktiviert. Es komprimiert vergangene Konversationskontexte und „heilt“ sein eigenes Gedächtnis, um maximale Effizienz innerhalb des Token-Fensters zu erhalten.
*   **Referenzen auf unveröffentlichte Modelle:** Der Code enthält explizite Aufrufe interner Modelle wie **"Capybara"** (Claude 4.6) und **"Fennec"** (Opus 4.6), was darauf hindeutet, dass diese Modelle bereits aktiv getestet wurden.

---

## 📸 Beweise & Dokumentation
Der Leak wurde zuerst vom Sicherheitsforscher **Chaofan Shou (@Fried_rice)** auf X (Twitter) identifiziert.

![Original Tweet](assets/tweet.png)
*Erste Entdeckung durch @Fried_rice auf X, die die globale Community-Analyse auslöste.*

---

## 📂 Verzeichnisstruktur
| Pfad | Beschreibung |
| :--- | :--- |
| `source/` | Rekonstruierter TypeScript-Quellcode aus dem v2.1.88-Leak. |
| `assets/` | Visuelle Beweise und Screenshots des Vorfalls. |

---

## 🔗 Offizielle Quellen & Links
- **Primäre Ankündigung:** [Chaofan Shous Tweet](https://twitter.com/Fried_rice/status/2038894956459290963)
- **Technische Analyse:** [CyberNews: Anthropic Claude Code Quellcode-Leak erklärt](https://cybernews.com/security/anthropic-claude-code-source-leak/)
- **Detaillierter Bericht:** [VentureBeat: Claude Code Quellcode-Leak-Analyse](https://venturebeat.com/ai/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know/)

---

## ⚖️ Haftungsausschluss
Der Code im Verzeichnis `source/` ist das **proprietäre geistige Eigentum von Anthropic**. Dieses Repository dient ausschließlich der **historischen und pädagogischen Dokumentation**. Die unbefugte Weitergabe oder kommerzielle Nutzung des geleakten Codes kann gegen Urheberrechtsgesetze und die Nutzungsbedingungen von Anthropic verstoßen.

---
*Erstellt mit ❤️ zur Dokumentation eines Meilensteins in der Geschichte der KI-Entwicklung.*
