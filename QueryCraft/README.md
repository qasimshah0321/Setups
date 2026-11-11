# QueryCraft for SSMS 22

**QueryCraft** is a productivity extension for **SQL Server Management Studio 22**. It helps you write,
format, check, refactor and navigate T-SQL faster, right inside the SSMS query editor.

**Download:** [QueryCraft.vsix](https://github.com/qasimshah0321/Setups/raw/main/QueryCraft/QueryCraft.vsix) (version 1.1.8)

SHA-256: `4C739E0793D994CEE227CBB6012E71F5F04FDDBA76B0175FE448B7A57FE8A24D`

---

## What QueryCraft can do

### Smart code completion
- Suggests tables, views, functions and stored procedures as you type, and adds a short alias after `FROM` / `JOIN`.
- Suggests the columns of the tables in your query, qualified with the right alias.
- Builds complete **`JOIN … ON`** conditions from your foreign keys.
- Adds a parameter template after `EXEC`.
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
- **Script query results as `INSERT` statements.**

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
- QueryCraft asks for confirmation before running:
  - `DELETE` or `UPDATE` without a `WHERE` clause,
  - `DROP` or `TRUNCATE`,
  - anything on a production connection.

### AI assistant (optional)
- **Text to SQL:** describe what you want in plain English and get the query.
- **Explain SQL**, **Optimize**, **Fix errors** and **Index analysis**.
- An **Assistant chat** window.
- Uses your own Anthropic (Claude) API key, which is stored encrypted on your PC. Table data is never sent.
- Offline explain and index analysis work without a key.

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

1. Download **QueryCraft.vsix**.
2. Close SSMS.
3. Double-click `QueryCraft.vsix` and follow the installer.
4. Start SSMS. You'll find everything under **Extensions ▸ QueryCraft**, and in the query editor's right-click menu.
5. Recommended: turn off SSMS's built-in IntelliSense list so you don't get two popups.
   It's under **Tools ▸ Options ▸ Text Editor ▸ Transact-SQL ▸ IntelliSense**.

Settings are under **Tools ▸ Options ▸ QueryCraft**.

**Requirements:**
- SQL Server Management Studio 22 (any 22.x release).
- SQL Server 2008 or later. Generated rename scripts use `CREATE OR ALTER`, which needs SQL Server 2016 SP1 or later.

**To uninstall:** use **Extensions ▸ Manage Extensions** in SSMS.

---

Developed by **Syed Muhammad Qasim**.

QueryCraft is an independent product. It is not affiliated with, endorsed by or sponsored by any other
software vendor. All product names are trademarks of their respective owners.
