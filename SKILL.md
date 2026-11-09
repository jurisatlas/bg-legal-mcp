---
name: bg-legal-mcp-skill
description: Official Bulgaria (BG) legislation, multi-tier court precedent research, and citation verification skill.
version: 2.0.0
author: JurisAtlas
license: MIT
---

# Bulgaria Legal Research & Multi-Tier Case Law Skill (`bg-legal-mcp`)

Use this skill whenever the user asks a legal question, drafts a pleading or contract, or researches case law across any judicial instance in **Bulgaria (BG)**.

## Verification & Research Rules

1. **Citation Verification:** Never fabricate a statutory provision or case citation. Query `search_legislation`, `search_case_law`, `search_tiered_court_decisions`, or `verify_citation` before citing any authority (e.g., `ECLI:BG:SC001:2024:001 or ДВ бр. 10`).
2. **Multi-Tier Judicial Coverage:**
   - **First Instance (Trial / Municipal / District):** 113 Районни съдилища (District Courts), 28 Окръжни съдилища (Regional Courts in 1st instance) & 28 Административни съдилища
   - **Second Instance (Cantonal / Regional / Appellate):** 5 Апелативни съдилища (Sofia, Plovdiv, Varna, Burgas, Veliko Tarnovo)
   - **Supreme & Constitutional Instance:** Върховен касационен съд (ВКС), Върховен административен съд (ВАС) & Конституционен съд
   - **Primary Tiered Database:** Централен уеб интерфейс за публикуване на съдебните актове (legalacts.justice.bg — All District, Regional, Appellate & Supreme Courts) (`https://legalacts.justice.bg`)
