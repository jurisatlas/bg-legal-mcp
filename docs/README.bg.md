[← All JurisAtlas Jurisdictions](https://github.com/jurisatlas) · [Unified Multi-Country Installer](https://github.com/jurisatlas/cli) · [English README](../README.md)

**Languages:** [English](../README.md) | **Български**

# Официално правно търсене за вашия AI асистент — България (`bg-legal-mcp`)

Този безплатен Model Context Protocol (MCP) сървър в режим само за четене свързва вашето AI приложение (Claude Desktop & Claude Code CLI, Cursor, VS Code (GitHub Copilot / Cline / Roo Code), Windsurf, Google Antigravity & Gemini CLI, LM Studio, OpenAI Codex CLI, and Continue.dev) директно с Държавен вестник (`dv.parliament.bg`) и Централния уеб интерфейс за съдебни актове (`legalacts.justice.bg`) за **България**.

**Безплатно & Open Source (MIT) · Само за четене от официални портали · Без API ключове · Без достъп до лични файлове · Деинсталиране с 1 клик**

---

## Лесна инсталация (Без програмиране, без ZIP)

> [!TIP]
> **Инсталатор от 1 файл (Без разархивиране на ZIP):** Изтеглете само файла по-долу и кликнете два пъти — той автоматично изтегля всички нужни файлове от GitHub във фонов режим и отваря прозореца за настройка. Пълният ZIP (`<> Code` → `Download ZIP`) остава наличен по желание.
> - **Windows:** [`Click_Here_To_Install_Windows.bat`](https://github.com/jurisatlas/bg-legal-mcp/raw/main/Click_Here_To_Install_Windows.bat)
> - **macOS:** [`Click_Here_To_Install_Mac.command`](https://github.com/jurisatlas/bg-legal-mcp/raw/main/Click_Here_To_Install_Mac.command)
> - Нуждаете се от повече държави? Използвайте **[Обединения инсталатор (jurisatlas/cli)](https://github.com/jurisatlas/cli)** или **[jurisatlas-mcp](https://github.com/jurisatlas/jurisatlas-mcp)**.

1. **Изтеглете 1 файл:** Кликнете на Windows (`.bat`) или macOS (`.command`) линка по-горе (или по желание пълния ZIP).
2. **Кликнете два пъти за старт:** Инсталаторът автоматично изтегля актуалните файлове от GitHub във фонов режим и отваря графичния прозорец.
3. **Свързване на AI приложения:** Проверете автоматично откритите AI програми (Claude Desktop & Claude Code CLI, Cursor, VS Code (GitHub Copilot / Cline / Roo Code), Windsurf, Google Antigravity & Gemini CLI, LM Studio, OpenAI Codex CLI, and Continue.dev), натиснете **Install to Selected AI Clients** и рестартирайте AI приложението.

**Бележка за ChatGPT Desktop / Web и Claude Web:** Тези приложения използват отдалечен HTTPS MCP URL (`--transport streamable-http`, вижте по-долу).

### Свързване чрез MCP линк или JSON

- **1-Click Links & Claude `.mcpb`:** [jurisatlas.github.io](https://jurisatlas.github.io) (Cursor `cursor://`, VS Code `vscode:mcp/`, Claude Desktop `.mcpb`).
- **Local MCP JSON (`uvx`):** `bg-legal-mcp` via `https://github.com/jurisatlas/bg-legal-mcp/archive/refs/heads/main.zip` (see Developer Reference below; no Git required).
- **Remote HTTPS MCP (`https://.../mcp`):** `bg-legal-mcp --transport streamable-http --host 0.0.0.0 --port 8000` or 1-click deploy on FastMCP Cloud / Render via [`jurisatlas-mcp`](https://github.com/jurisatlas/jurisatlas-mcp).

<details>
<summary><b>Виждате предупреждение Windows SmartScreen или macOS Gatekeeper? (Нормално и безопасно)</b></summary>

- **Windows (SmartScreen):** Кликнете **More info** → **Run anyway**.
- **macOS (Gatekeeper / Sequoia):** Отворете **System Settings → Privacy & Security** и кликнете **Open Anyway**.

</details>

**Сигурност & деинсталиране с 1 клик:** Работи само в режим на четене от публични официални портали и няма достъп до личните ви файлове. За премахване отворете инсталатора отново и кликнете **Uninstall / Remove**.

---

## Изпробвайте веднага: 3 примерни заявки

1. > Провери цитата `ECLI:BG:SC001:2024:001 or ДВ бр. 10` в официалните регистри за България и обобщи основното правно положение.
2. > Намери приложимото законодателство и съдебна практика за България по конкретен правен въпрос с официални връзки.
3. > Представи трите съдебни инстанции в България и потърси актуални решения на апелативните съдилища.

---

## Съдебни инстанции и официални източници

| Съдебна инстанция | Обхванати съдилища |
|:---|:---|
| **Първа инстанция (Районни, окръжни и административни съдилища)** | 113 Районни съдилища (District Courts), 28 Окръжни съдилища (Regional Courts in 1st instance) & 28 Административни съдилища |
| **Втора инстанция (5 Апелативни съдилища)** | 5 Апелативни съдилища (Sofia, Plovdiv, Varna, Burgas, Veliko Tarnovo) |
| **ВКС, ВАС и Конституционен съд** | Върховен касационен съд (ВКС), Върховен административен съд (ВАС) & Конституционен съд |

- **State Gazette of Bulgaria (dv.parliament.bg) & Lex.bg:** [https://dv.parliament.bg](https://dv.parliament.bg) (`pravko.bg`, `dv.parliament.bg`, `parliament.bg`, `lex.bg`)
- **Централен уеб интерфейс за публикуване на съдебните актове (legalacts.justice.bg — All District, Regional, Appellate & Supreme Courts):** [https://legalacts.justice.bg](https://legalacts.justice.bg) (`vks.bg`, `constcourt.bg`, `portalpravo.bg`, `legalacts.justice.bg`, `sac.government.bg`)

---

<details>
<summary><b>Техническа справка за разработчици (6 MCP инструмента, 3 промпта, uvx, ръчен JSON & Streamable HTTP)</b></summary>

### Standardized MCP Tools (6 Tools)

| Tool | Description |
|:---|:---|
| `search_legislation` | Searches enacted statutes, codes, regulations, and official gazettes in Bulgaria. Returns `source_tier` (`official_registry_api` vs `web_search_fallback`) and structured `warnings`. |
| `search_case_law` | Searches national jurisprudence and judicial archives for Bulgaria, tagging official API vs web fallback hits. |
| `search_tiered_court_decisions` | Filters case law by judicial instance (`first_instance`, `appellate_regional` — Appellate Courts (Апелативни съдилища), `supreme_constitutional`) or a sub-portal key. |
| `list_court_hierarchy` | Returns the complete 3-tier court structure and official sub-portal keys for Bulgaria. |
| `get_legal_document_markdown` | Fetches full statutory or judgment text (HTML or `.pdf`) and converts it to clean paginated Markdown. |
| `verify_citation` | Verifies legal citations against live sources, returning `VERIFIED_OFFICIAL_RECORD` only for official registry API hits, `UNCONFIRMED_WEB_MATCH` for web fallback hits, or `NOT_FOUND`. |

### Built-in MCP Prompts (3 Native Prompts)

- `verify_citations_in_draft` — Extract and audit every Bulgaria citation in a legal brief, memo, or contract.
- `research_statute_and_precedent` — Research controlling statutes and multi-tier case law for a legal issue.
- `map_court_hierarchy` — Map the 3-tier court escalation path and locate appellate decisions.

### Run Directly with `uvx` (No Git Required)

```bash
uvx --from https://github.com/jurisatlas/bg-legal-mcp/archive/refs/heads/main.zip bg-legal-mcp
```

### Remote HTTPS / Streamable HTTP Mode (ChatGPT Desktop / Web & Claude Web)

```bash
uvx --from https://github.com/jurisatlas/bg-legal-mcp/archive/refs/heads/main.zip bg-legal-mcp --transport streamable-http --host 127.0.0.1 --port 8000
```

### Manual JSON Configuration

**Claude Desktop / Cursor / Windsurf / Antigravity / LM Studio (`mcpServers`):**

```json
{
  "mcpServers": {
    "bg-legal-mcp": {
      "command": "uvx",
      "args": [
        "--from",
        "https://github.com/jurisatlas/bg-legal-mcp/archive/refs/heads/main.zip",
        "bg-legal-mcp"
      ],
      "env": {
        "PYTHONIOENCODING": "utf-8"
      }
    }
  }
}
```

**VS Code (`Code/User/mcp.json` — uses `"servers"` + `"type": "stdio"`):**

```json
{
  "servers": {
    "bg-legal-mcp": {
      "type": "stdio",
      "command": "uvx",
      "args": [
        "--from",
        "https://github.com/jurisatlas/bg-legal-mcp/archive/refs/heads/main.zip",
        "bg-legal-mcp"
      ],
      "env": {
        "PYTHONIOENCODING": "utf-8"
      }
    }
  }
}
```

</details>

---

> **Не е правен съвет:** JurisAtlas е инструмент за правно проучване. Винаги проверявайте текстовете в Държавен вестник и официалните регистри. Само `VERIFIED_OFFICIAL_RECORD` идва от официален API. ([MIT License](../LICENSE))
