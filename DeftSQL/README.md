# DeftSQL for SSMS 22

**DeftSQL** is a productivity extension for **SQL Server Management Studio 22**. It helps you write,
format, check, refactor and navigate T-SQL faster, right inside the SSMS query editor.

**Download:** [DeftSQL.vsix](https://github.com/qasimshah0321/Setups/raw/main/DeftSQL/DeftSQL.vsix) (version 2.5.2)

SHA-256: `B17B8822F63BA4B293BBFAB2F6CB655EBFA2869D84E6F16F03F9456A31C6AB9F`

**Product guide:** [DeftSQL-Product-Guide.docx](https://github.com/qasimshah0321/Setups/raw/main/DeftSQL/DeftSQL-Product-Guide.docx) (Word, every feature with its menu path and screenshots)

> **Previously called QueryCraft.** DeftSQL 2.0 is the same product under a new name. If you installed QueryCraft, uninstall it first (close SSMS, then run in Command Prompt):
>
> ```
> "C:\Program Files\Microsoft SQL Server Management Studio 22\Release\Common7\IDE\VSIXInstaller.exe" /uninstall:QueryCraft.SSMS.4b8f2c1e-7a3d-4e5f-9c6b-2d1a0e9f8b7c
> ```
>
> Your settings, snippets and history are carried over automatically.

---

## What DeftSQL can do

### Smart code completion
- Suggests tables, views, functions and stored procedures as you type, and adds a short alias after `FROM` / `JOIN`.
- Suggests the columns of the tables in your query, qualified with the right alias.
- Builds complete **`JOIN … ON`** conditions from your foreign keys.
- Adds a parameter template after `EXEC`.
- **Parameter info:** while you type a call to a stored procedure or function, a tooltip shows its parameters and highlights the one you are typing.
- Also completes variables, CTEs, temp tables, data types, `INSERT` column lists and keywords.
- While the list is open:
  - **Ctrl+Up / Ctrl+Down** filter it: tables, columns, procedures, variables, schemas, keywords or snippets.
  - **Ctrl+Right** opens a column picker. Tick the columns you need and press Enter to insert them.
- Put the caret after `SELECT *` and press **Tab** to **expand the wildcard** into the full column list.

### Snippets
- About 50 built-in snippets: type a shortcut and press **Tab**.
  - For example, `ssf` gives `SELECT * FROM`, `st100` gives `SELECT TOP 100`, and `cte` gives a CTE template.
  - Others cover transactions (`bt`), try/catch (`tc`) and `MERGE` (`mrg`).
- Placeholders fill themselves in: cursor position, selected text, date and time, user, server, database, a new GUID, and the clipboard.
- A Snippet Manager creates and edits snippets and imports or exports them. *Surround with snippet* wraps your selection.
- A shared snippets folder lets a whole team use one set of snippets.

### SQL formatting
- **Ctrl+K, Ctrl+Y** formats the whole script or just the selection.
- Six built-in styles plus a fully custom style, with a live preview window.
- Styles can be imported and exported, and format-on-paste is optional.
- A safety check refuses any formatting that would change the meaning of your code.

### Code analysis
- About 36 rules check your SQL as you type and underline problems:
  - risky statements,
  - best-practice issues,
  - performance problems,
  - deprecated syntax,
  - style issues,
  - security concerns.
- **Ctrl+.** applies quick fixes, one at a time or all at once.
- **Find Unused Variables and Parameters** lists them in the current script.
- **Find Invalid Objects** finds procedures, views and functions that refer to objects that no longer exist.

### Refactoring
- **Smart rename (F2):**
  - Renames aliases, variables, CTEs and temp tables everywhere in the script.
  - For tables, views, procedures, functions and columns, it generates a reviewable script that renames the object and updates every dependent object in one transaction.
- **Qualify object names:** adds schema prefixes everywhere.
- **Insert semicolons:** ends every statement with one.
- **Add or remove square brackets.**
- **Uppercase or lowercase keywords.**
- **Encapsulate as stored procedure.**
- **Script query results as `INSERT`, `UPDATE` or `DELETE` (Ctrl+B, Ctrl+D):**
  - Run a SELECT, then turn its rows into statements in a new query window.
  - Works through aliases and joins: columns are mapped back to their real table, and the primary key is ticked for you.
  - **Several tables at once:** tick every table of a join; parents and children are put in foreign-key order.
  - **Join-based UPDATE / DELETE:** one statement per table that reuses your query's own joins and `WHERE`,
    instead of one statement per row. Alias a value with the target column's name to set it, e.g. `p.LastName AS JobTitle`.
  - Primary keys you didn't select are fetched automatically, so each table can still be matched.
  - You can also target another table, such as an archive copy.
  - Computed and rowversion columns are skipped, identity values are kept.
  - The script is wrapped in a transaction; you choose `COMMIT` or `ROLLBACK`.

### Navigation
- **Find Object:** search every table, view, procedure and column, with wildcards.
- **F12:** script the object under the caret as `ALTER`.
- **Ctrl+F12:** select that object in Object Explorer.
- **Shift+F5:** run just the statement under the caret.
- **Script Summary:** an outline of every statement in a long script.
- Hover over a table or column to see its details, including where a column is used: procedures, keys, indexes and constraints.

### Query and tab history
- **Query History** records every query you run. You can search it and mark favorites.
- **Tab History (Ctrl+Q)** saves your query tabs every 30 seconds, so you can reopen tabs you closed or lost in a crash.
- Optionally, the tabs that were open when SSMS closed are reopened on startup.

### Environment tab coloring and safety
- A colored bar above each query window shows which environment you are on: **Production**, **Staging**, **Test** or **Dev**.
- DeftSQL asks for confirmation before running:
  - `DELETE` or `UPDATE` without a `WHERE` clause,
  - `DROP` or `TRUNCATE`,
  - anything on a production connection.

### AI assistant (optional)
- **Text to SQL:** describe what you want in plain English and get the query.
  - DeftSQL sends the model only the tables your question needs (matched on table and column names and the
    database's own column descriptions), how they join, and a ready-made `FROM … JOIN` clause.
  - The generated SQL is compiled on the server without running it. If a column or table is wrong, DeftSQL tells
    the model which table really has that column and how to join it, and lets it correct itself (up to three times).
  - If a problem remains, it is listed in a comment above the query so you know to review it.
- **Explain SQL**, **Optimize**, **Fix errors** and **Index analysis**.
- An **Assistant chat** window.
- Choose the AI engine:
  - **Claude:** your own Anthropic API key, stored encrypted on your PC.
  - **Local and fully offline:** install [Ollama](https://ollama.com), run `ollama pull qwen2.5-coder:7b` (or `qwen2.5-coder:3b` on 8 GB PCs), then set **Provider = Ollama** in Tools ▸ Options ▸ DeftSQL ▸ AI. Nothing leaves your computer.
- Table data is never sent. Offline explain and index analysis work without any AI.

---

## Keyboard shortcuts

| Shortcut | Command |
|---|---|
| Ctrl+K, Ctrl+Y | Format SQL |
| Tab | Expand snippet / expand `*` |
| Ctrl+Space | Show suggestions |
| Ctrl+. | Quick fixes & refactorings |
| F2 | Smart rename |
| F12 | Script object as ALTER |
| Ctrl+F12 | Select in Object Explorer |
| Shift+F5 | Execute current statement |
| Ctrl+Q | Tab history |
| Ctrl+Shift+D | Refresh suggestions |
| Ctrl+Shift+P | Suggestions on/off |
| Ctrl+B, Ctrl+W | Expand wildcards |
| Ctrl+B, Ctrl+Q | Qualify object names |
| Ctrl+B, Ctrl+B | Add/remove square brackets |
| Ctrl+B, Ctrl+C | Insert semicolons |
| Ctrl+B, Ctrl+E | Encapsulate as stored procedure |
| Ctrl+B, Ctrl+D | Script query results as INSERT / UPDATE / DELETE |
| Ctrl+B, Ctrl+U / Ctrl+L | Keywords upper / lower case |
| Ctrl+B, Ctrl+S | Script summary |
| Ctrl+B, Ctrl+F | Find unused variables and parameters |
| Ctrl+B, Ctrl+O | Find object |
| Ctrl+B, Ctrl+G | Select current statement |
| Ctrl+B, Ctrl+H | Query history |
| Ctrl+B, Ctrl+N | Code analysis |
| Ctrl+B, Ctrl+A | Text to SQL |
| Ctrl+B, Ctrl+X | Explain SQL |
| Ctrl+B, Ctrl+I | AI assistant |

---

## Installation

1. Download **DeftSQL.vsix**.
2. Close SSMS.
3. Double-click `DeftSQL.vsix` and follow the installer.
4. Start SSMS. You'll find everything under **Extensions ▸ DeftSQL**, in the query editor's right-click menu,
   and on the **DeftSQL toolbar** (Format, Snippets, Find Object, Code Analysis, Script Results, Text to SQL,
   Explain, Optimize, AI Assistant, Query and Tab History, Refresh, Options, and a label showing which AI model
   answers). Show or hide the toolbar with **View ▸ Toolbars ▸ DeftSQL**.
5. Recommended: turn off SSMS's built-in IntelliSense list so you don't get two popups.
   It's under **Tools ▸ Options ▸ Text Editor ▸ Transact-SQL ▸ IntelliSense**.

Settings are under **Tools ▸ Options ▸ DeftSQL**.

**Requirements:**
- SQL Server Management Studio 22 (any 22.x release).
- SQL Server 2008 or later. Generated rename scripts use `CREATE OR ALTER`, which needs SQL Server 2016 SP1 or later.

**To uninstall:** close SSMS, then run in Command Prompt:
```
"C:\Program Files\Microsoft SQL Server Management Studio 22\Release\Common7\IDE\VSIXInstaller.exe" /uninstall:DeftSQL.SSMS.4b8f2c1e-7a3d-4e5f-9c6b-2d1a0e9f8b7c
```

---

Developed by **Syed Muhammad Qasim**.

DeftSQL is an independent product. It is not affiliated with, endorsed by or sponsored by any other
software vendor. All product names are trademarks of their respective owners.
