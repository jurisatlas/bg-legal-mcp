# Bulgaria Legal Research MCP Server (`bg-legal-mcp`)

**[Български](#lang-bg) | [English Documentation](#english-documentation)**

---

<a id="lang-bg"></a>
## Правен MCP сървър за законодателство и съдебна практика (`bg-legal-mcp`) — Български

### За това хранилище

Това хранилище съдържа Model Context Protocol (MCP) сървър, който свързва вашето AI приложение (Claude Desktop, Cursor, Windsurf, VS Code / Copilot, Cline или Antigravity) директно с Държавен вестник (`dv.parliament.bg`) и Централния уеб интерфейс за съдебни актове (`legalacts.justice.bg` — 113 районни, 28 окръжни, 28 административни и 5 апелативни съдилища, ВКС, ВАС и Конституционен съд).

### Бърза инсталация (Избор на AI приложение)

1. **Изтегляне:** Кликнете върху **`<> Code` -> `Download ZIP`** горе вдясно и разархивирайте папката.
2. **Стартиране:** Кликнете два пъти върху **`Click_Here_To_Install_Windows.bat`** (Windows) или **`Click_Here_To_Install_Mac.command`** (macOS).
3. **Избор на AI клиент:** Маркирайте AI програмите, които използвате (Claude, Cursor, Windsurf, VS Code, Antigravity), натиснете инсталиране и рестартирайте избраното приложение.

**Бележка за сигурност:** Инсталаторът работи само в режим на четене (read-only) и няма достъп до личните ви файлове на компютъра.

### Съдебни инстанции и официални източници

| Съдебна инстанция | Обхванати съдилища |
|:---|:---|
| **Първа инстанция (Районни, окръжни и административни съдилища)** | 113 Районни съдилища (District Courts), 28 Окръжни съдилища (Regional Courts in 1st instance) & 28 Административни съдилища |
| **Втора инстанция (5 Апелативни съдилища)** | 5 Апелативни съдилища (Sofia, Plovdiv, Varna, Burgas, Veliko Tarnovo) |
| **ВКС, ВАС и Конституционен съд** | Върховен касационен съд (ВКС), Върховен административен съд (ВАС) & Конституционен съд |

- **State Gazette of Bulgaria (dv.parliament.bg) & Lex.bg:** [https://dv.parliament.bg](https://dv.parliament.bg) (`pravko.bg`, `dv.parliament.bg`, `parliament.bg`, `lex.bg`)
- **Централен уеб интерфейс за публикуване на съдебните актове (legalacts.justice.bg — All District, Regional, Appellate & Supreme Courts):** [https://legalacts.justice.bg](https://legalacts.justice.bg) (`vks.bg`, `constcourt.bg`, `portalpravo.bg`, `legalacts.justice.bg`, `sac.government.bg`)

---

<a id="english-documentation"></a>
## English Documentation

Model Context Protocol (MCP) server providing live, read-only access to **Bulgaria (BG)** legislation, official gazettes, multi-tier judicial decisions (First Instance, Regional/Cantonal/Appellate, and Supreme/Constitutional courts, including HTML and PDF full-text extraction), and statutory citation verification across all major AI clients (**ChatGPT Desktop, OpenAI Codex CLI, Claude Desktop, Claude Code CLI, Cursor, Windsurf, VS Code / GitHub Copilot / Cline / Roo Code, Google Antigravity / Gemini CLI, Perplexity, and Continue.dev**).

---

### Interactive Desktop Setup (Select Your AI Assistant)

This package includes a graphical installer for legal practitioners and non-technical users that lets you select which AI application(s) you use:

1. **Download:** Click **`<> Code`** at the top right of this repository, select **`Download ZIP`**, and extract the folder to your computer.
2. **Run the Setup Utility:**
   - **Windows:** Double-click `Click_Here_To_Install_Windows.bat`
   - **macOS:** Double-click `Click_Here_To_Install_Mac.command`
3. **Select Your AI Client(s) & Connect:** Check the box(es) for the AI assistant(s) installed on your computer (**ChatGPT Desktop & OpenAI Codex CLI**, **Claude Desktop & Claude Code CLI**, **Cursor**, **Windsurf**, **VS Code / GitHub Copilot / Cline / Roo Code**, **Google Antigravity / Gemini CLI**, or **Perplexity / Continue.dev**), click **Install to Selected AI Clients**, and restart your selected AI application.

**System Integrity Note:** The setup utility operates strictly in read-only mode with respect to your personal files and documents. It installs an isolated Python runtime inside the extracted folder and registers the server entry only in the AI client configuration files you select.

---

### Multi-Tier Judicial Hierarchy & Live Indexed National Archives

This server performs live queries across the full judicial hierarchy and official legal archives of **Bulgaria**, extracting full text from both HTML pages and official court/gazette PDF judgments:

| Judicial Tier | Covered Courts & Tribunals |
|:---|:---|
| **Tier 1 — First Instance** | 113 Районни съдилища (District Courts), 28 Окръжни съдилища (Regional Courts in 1st instance) & 28 Административни съдилища |
| **Tier 2 — Regional / Cantonal / Appellate** | 5 Апелативни съдилища (Sofia, Plovdiv, Varna, Burgas, Veliko Tarnovo) |
| **Tier 3 — Supreme & Constitutional** | Върховен касационен съд (ВКС), Върховен административен съд (ВАС) & Конституционен съд |

#### Official Portals & Live Indexed Domains

- **National Legislation & Official Gazette:** State Gazette of Bulgaria (dv.parliament.bg) & Lex.bg — [https://dv.parliament.bg](https://dv.parliament.bg)
  - *Indexed Legislation Domains:* `pravko.bg`, `dv.parliament.bg`, `parliament.bg`, `lex.bg`
- **Court Decisions & Jurisprudence Archives:** Централен уеб интерфейс за публикуване на съдебните актове (legalacts.justice.bg — All District, Regional, Appellate & Supreme Courts) — [https://legalacts.justice.bg](https://legalacts.justice.bg)
  - *Indexed Judicial & Open Case Law Domains:* `vks.bg`, `constcourt.bg`, `portalpravo.bg`, `legalacts.justice.bg`, `sac.government.bg`

---

### Available MCP Tools

| Tool | Description |
|:---|:---|
| `search_legislation` | Searches enacted statutes, codes, decrees, and official gazette publications in Bulgaria. |
| `search_case_law` | Searches national jurisprudence and open judicial archives for Bulgaria. |
| `search_tiered_court_decisions` | Filters case law specifically by judicial instance (`first_instance`, `appellate_regional`, `supreme_constitutional`) or specific regional/cantonal/district court. |
| `list_court_hierarchy` | Returns the complete 3-tier court structure and supported regional court filters for Bulgaria. |
| `get_legal_document_markdown` | Retrieves full statutory or judicial texts (both HTML and official `.pdf` court judgments) and converts them into clean Markdown. |
| `verify_citation` | Validates statutory and case law citations against official registries. |

---

<details>
<summary><b>Manual Configuration for Developers (Optional)</b></summary>

```json
{
  "mcpServers": {
    "bg-legal-mcp": {
      "command": "uvx",
      "args": [
        "--from",
        "https://github.com/jurisatlas/bg-legal-mcp/archive/refs/heads/main.zip",
        "bg-legal-mcp"
      ]
    }
  }
}
```
</details>
