# 🦅 Claude Code: Análise do Vazamento do Código-Fonte (31 de março de 2026)

[![Estado](https://img.shields.io/badge/Estado-Registro_Histórico-blue.svg)]()
[![Data](https://img.shields.io/badge/Data-31_de_março_de_2026-orange.svg)]()
[![Tipo](https://img.shields.io/badge/Tipo-Erro_Humano-red.svg)]()

> [!IMPORTANT]
> Este repositório é uma documentação detalhada do evento em que a Anthropic vazou acidentalmente o código-fonte completo de sua ferramenta CLI **Claude Code**.

---

### 🌐 Selecione seu idioma / Select Your Language:
[🇺🇸 English](README.md) | [🇪🇸 Español](README.es.md) | [🇧🇷 Português](README.pt.md) | [🇨🇳 中文](README.zh.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | [🇯🇵 日本語](README.ja.md) | [🇷🇺 Русский](README.ru.md)

---

## 🔍 Resumo do Incidente
Em **31 de março de 2026**, a Anthropic incluiu inadvertidamente um arquivo de mapas de fonte (source map) de **59,8 MB** (`cli.js.map`) na versão **v2.1.88** do pacote `@anthropic-ai/claude-code` no registro npm.

O vazamento foi o resultado de um **erro de empacotamento** durante o processo de build. Os mapas de fonte são projetados para mapear o código de produção minificado de volta à sua fonte original para depuração; ao incluir este arquivo, a Anthropic forneceu sem saber a "planta" de toda a sua arquitetura CLI.

### 🛠️ Descobertas Principais e Insights Arquiteturais
A análise dos **1.902 arquivos proprietários** e **512.000 linhas de TypeScript** revelou:

*   **Motor de Orquestração KAIROS:** O "cérebro" do Claude Code. Ele lida com comportamento agêntico avançado, loops de chamadas de ferramentas e gerenciamento de estado complexo que anteriormente se pensava ser processado inteiramente no lado do servidor.
*   **Modo Undercover (Disfarçado):** Um recurso de furtividade projetado para funcionários da Anthropic. Ele permite que o agente faça contribuições git (commits/PRs) sem marcá-las automaticamente como geradas por IA, ocultando efetivamente o uso de IA em projetos de código aberto.
*   **autoDream (Memória de Autocura):** Um subsistema sofisticado que é ativado durante períodos de inatividade do usuário. Ele comprime o contexto de conversas passadas e "cura" sua própria memória para manter a eficiência máxima dentro da janela de tokens.
*   **Referências a Modelos Não Lançados:** O código contém chamadas explícitas para modelos internos como **"Capybara"** (Claude 4.6) e **"Fennec"** (Opus 4.6), sugerindo que esses modelos já estavam em testes ativos.

---

## 📸 Evidência e Documentação
O vazamento foi identificado inicialmente pelo pesquisador de segurança **Chaofan Shou (@Fried_rice)** no X (Twitter).

![Tweet Original](assets/tweet.png)
*Descoberta inicial por @Fried_rice no X, desencadeando a análise da comunidade global.*

---

## 📂 Estrutura do Diretório
| Caminho | Descrição |
| :--- | :--- |
| `source/` | Código-fonte TypeScript reconstruído a partir do vazamento v2.1.88. |
| `assets/` | Evidência visual e capturas de tela do incidente. |

---

## 🔗 Fontes Oficiais e Links
- **Anúncio Primário:** [Tweet de Chaofan Shou](https://twitter.com/Fried_rice/status/2038894956459290963)
- **Análise Técnica:** [CyberNews: Vazamento de código do Anthropic Claude Code explicado](https://cybernews.com/security/anthropic-claude-code-source-leak/)
- **Relatório Detalhado:** [VentureBeat: Análise do vazamento de Claude Code](https://venturebeat.com/ai/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know/)

---

## ⚖️ Aviso Legal
O código no diretório `source/` é **propriedade intelectual da Anthropic**. Este repositório destina-se apenas a **documentação histórica e educacional**. A redistribuição não autorizada ou o uso comercial do código vazado pode violar as leis de direitos autorais e os Termos de Serviço da Anthropic.

---
*Gerado com ❤️ para documentar um marco na história do desenvolvimento da IA.*
