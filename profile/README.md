<div align="center">

<br />

```
██████╗  █████╗ ██╗  ██╗ ██████╗ ███╗   ██╗███╗   ██╗███████╗
██╔══██╗██╔══██╗╚██╗██╔╝██╔═══██╗████╗  ██║████╗  ██║██╔════╝
██║  ██║███████║ ╚███╔╝ ██║   ██║██╔██╗ ██║██╔██╗ ██║█████╗  
██║  ██║██╔══██║ ██╔██╗ ██║   ██║██║╚██╗██║██║╚██╗██║██╔══╝  
██████╔╝██║  ██║██╔╝ ██╗╚██████╔╝██║ ╚████║██║ ╚████║███████╗
╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝╚═╝  ╚═══╝╚══════╝
```

**Schema → Code. Any database. Any language.**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Discord](https://img.shields.io/badge/discord-join-5865F2.svg)](https://discord.gg/daxonne)
[![Status](https://img.shields.io/badge/status-early%20development-orange.svg)]()

</div>

---

## What is Daxonne?

**Daxonne** is an open-source, language-agnostic code generation tool that reads your database schema and generates all the boilerplate you hate writing — DTOs, queries, repository methods, models — in any language, with any ORM or data access pattern.

Connect your database. Pick your templates. Get production-ready code.

```bash
daxonne init
daxonne pull              # reads your schema
daxonne add csharp-dapper # install a template
daxonne generate          # outputs your code
```

---

## Why Daxonne?

Every project has the same problem: your database has 40 tables, and you need DTOs, queries, and data access methods for all of them. You write the first one by hand, copy-paste the rest, tweak names, miss a field, start over.

Existing tools are either too opinionated (tied to a single ORM or language), too basic (just raw model generation), or simply don't support your database (Oracle, we're looking at you).

Daxonne solves this with a **plugin + template architecture**:

- **Database plugins** read your schema (Oracle, PostgreSQL, MySQL, SQLite, and more via community plugins)
- **Templates** generate code in your language and style (C# + Dapper, Java + Hibernate, Python + SQLAlchemy, TypeScript + Prisma...)
- **You stay in control** — configure naming conventions, output structure, and code style

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                   Daxonne Core (Go)                 │
│                                                     │
│  ┌─────────────┐    ┌──────────────┐    ┌────────┐  │
│  │ DB Plugins  │───▶│ Internal AST │───▶│ Engine │  │
│  │             │    │   (schema)   │    │        │  │
│  │ • Oracle    │    └──────────────┘    └───┬────┘  │
│  │ • Postgres  │                            │        │
│  │ • MySQL     │                            ▼        │
│  │ • ...       │                    ┌──────────────┐ │
│  └─────────────┘                    │  Templates   │ │
│                                     │              │ │
│                                     │ • csharp-... │ │
│                                     │ • java-...   │ │
│                                     │ • python-... │ │
│                                     │ • ...        │ │
│                                     └──────────────┘ │
└─────────────────────────────────────────────────────┘
         │                                    │
    ┌────┴─────┐                     ┌────────┴───────┐
    │   CLI    │                     │    Desktop     │
    │  (Go)    │                     │ (Tauri + React)│
    └──────────┘                     └────────────────┘
```

---

## Repositories

| Repo | Description |
|------|-------------|
| [`daxonne`](https://github.com/daxonne/daxonne) | Core CLI — the engine that powers everything |
| [`daxonne-templates`](https://github.com/daxonne/daxonne-templates) | Official & community templates, curated by the team |
| [`daxonne-desktop`](https://github.com/daxonne/daxonne-desktop) | Desktop app (Tauri + React) with visual schema explorer |
| [`daxonne-docs`](https://github.com/daxonne/daxonne-docs) | Documentation |

---

## Supported Databases

| Database | Status |
|----------|--------|
| Oracle | ✅ Official |
| PostgreSQL | 🚧 In progress |
| MySQL | 📋 Planned |
| SQLite | 📋 Planned |
| SQL Server | 💡 Community welcome |

---

## Template Ecosystem

Templates live in [`daxonne-templates`](https://github.com/daxonne/daxonne-templates) and are reviewed by the Daxonne team before being made available.

Want to contribute a template? Check out the [template authoring guide](https://github.com/daxonne/daxonne-docs).

**Official templates**

| Template | Language | Pattern |
|----------|----------|---------|
| `csharp-dapper` | C# | Dapper + record DTOs |
| `csharp-efcore` | C# | EF Core + class models |
| `csharp-vanilla` | C# | ADO.NET raw |

**Planned community templates**

- `java-hibernate`, `python-sqlalchemy`, `typescript-prisma`, `go-sqlx`, `kotlin-exposed`...

---

## Contributing

Daxonne is in early development. Contributions are very welcome.

- 🐛 Found a bug? [Open an issue](https://github.com/daxonne/daxonne/issues)
- 💡 Have an idea? [Start a discussion](https://github.com/daxonne/daxonne/discussions)
- 🧩 Want to write a template? See the [template guide](https://github.com/daxonne/daxonne-docs)
- 🔌 Want to add a database? See the [plugin guide](https://github.com/daxonne/daxonne-docs)

---

## License

MIT © Daxonne Contributors

---

<div align="center">
  <sub>Built with ❤️ for developers who are tired of writing boilerplate.</sub>
</div>