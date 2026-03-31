# 🦅 Claude Code: Análisis de la Filtración del Código Fuente (31 de marzo de 2026)

[![Estado](https://img.shields.io/badge/Estado-Registro_Histórico-blue.svg)]()
[![Fecha](https://img.shields.io/badge/Fecha-31_de_marzo_de_2026-orange.svg)]()
[![Tipo](https://img.shields.io/badge/Tipo-Error_Humano-red.svg)]()

> [!IMPORTANT]
> Este repositorio es una documentación detallada del evento en el que Anthropic filtró accidentalmente el código fuente completo de su herramienta CLI **Claude Code**.

---

### 🌐 Selecciona tu idioma / Select Your Language:
[🇺🇸 English](README.md) | [🇪🇸 Español](README.es.md) | [🇧🇷 Português](README.pt.md) | [🇨🇳 中文](README.zh.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | [🇯🇵 日本語](README.ja.md) | [🇷🇺 Русский](README.ru.md)

---

## 🔍 Resumen del Incidente
El **31 de marzo de 2026**, Anthropic incluyó inadvertidamente un archivo de mapas de fuente (source map) de **59.8 MB** (`cli.js.map`) en la versión **v2.1.88** del paquete `@anthropic-ai/claude-code` en el registro de npm.

La filtración fue el resultado de un **error de empaquetado** durante el proceso de compilación. Los mapas de fuente están diseñados para mapear el código de producción minificado de vuelta a su fuente original para la depuración; al incluir este archivo, Anthropic proporcionó sin saberlo el "plano" de toda su arquitectura CLI.

### 🛠️ Descubrimientos Clave y Perspectivas Arquitectónicas
El análisis de los **1,902 archivos propietarios** y las **512,000 líneas de TypeScript** reveló:

*   **Motor de Orquestación KAIROS:** El "cerebro" de Claude Code. Maneja comportamientos agénticos avanzados, bucles de llamadas a herramientas y una gestión de estado compleja que anteriormente se pensaba que era manejada enteramente en el lado del servidor.
*   **Modo Undercover (Encubierto):** Una función de sigilo diseñada para empleados de Anthropic. Permite al agente realizar contribuciones de git (commits/PRs) sin etiquetarlas automáticamente como generadas por IA, ocultando efectivamente el uso de IA en proyectos de código abierto.
*   **autoDream (Memoria de Autocuración):** Un subsistema sofisticado que se activa durante períodos de inactividad del usuario. Comprime el contexto de conversaciones pasadas y "cura" su propia memoria para mantener la máxima eficiencia dentro de la ventana de tokens.
*   **Referencias a Modelos no Lanzados:** El código contiene llamadas explícitas a modelos internos como **"Capybara"** (Claude 4.6) y **"Fennec"** (Opus 4.6), sugiriendo que estos modelos ya estaban en pruebas activas.

---

## 📸 Evidencia y Documentación
La filtración fue identificada inicialmente por el investigador de seguridad **Chaofan Shou (@Fried_rice)** en X (Twitter).

![Tweet Original](assets/tweet.png)
*Descubrimiento inicial por @Fried_rice en X, activando el análisis de la comunidad global.*

---

## 📂 Estructura del Directorio
| Ruta | Descripción |
| :--- | :--- |
| `source/` | Código fuente de TypeScript reconstruido a partir de la filtración v2.1.88. |
| `assets/` | Evidencia visual y capturas de pantalla del incidente. |

---

## 🔗 Fuentes Oficiales y Enlaces
- **Anuncio Primario:** [Tweet de Chaofan Shou](https://twitter.com/Fried_rice/status/2038894956459290963)
- **Análisis Técnico:** [CyberNews: Análisis de la filtración de Claude Code](https://cybernews.com/security/anthropic-claude-code-source-leak/)
- **Reporte Detallado:** [VentureBeat: Análisis de la filtración de Claude Code](https://venturebeat.com/ai/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know/)

---

## ⚖️ Descargo de Responsabilidad Legal
El código en el directorio `source/` es **propiedad intelectual de Anthropic**. Este repositorio es solo para **documentación histórica y educativa**. La redistribución no autorizada o el uso comercial del código filtrado pueden violar las leyes de derechos de autor y los Términos de Servicio de Anthropic.

---
*Generado con ❤️ para documentar un hito en la historia del desarrollo de la IA.*
