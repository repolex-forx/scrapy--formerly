# Repolex Knowledge Graph of scrapy/formerly

RDF knowledge graph data for [scrapy/formerly](https://github.com/scrapy/formerly), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download scrapy/formerly
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1286733c171d2138bc6dcb59b49ee4df5228fd40
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1286733c171d2138bc6dcb59b49ee4df5228fd40
│           └── chunk-001.nq.gz
├── blob
│   ├── 2aac90a9f878b93a4c7a05509e83a4143498f0a7.nq.gz
│   ├── 5354adcb5239e267e02affc6d5326bc6243f8dcc.nq.gz
│   ├── 6ead05eced18b8703d19b6b5fb1860da86843cd4.nq.gz
│   ├── 77458ed17470646be5aa28dcd75bec084f1a16fb.nq.gz
│   ├── 7d7442433401d13dc969e6e0e361ff11c05b5bb1.nq.gz
│   ├── 7f08d7a1a8960f4521462840a843870fc90f5afe.nq.gz
│   ├── 993fba75ae7506d4b733164b5f3722c6131f8cce.nq.gz
│   ├── ac8f4cb26e091718c33483bf66be03e776cbe4da.nq.gz
│   ├── c76beec7ae28d9ff9df36284627b7d5fb5931dd2.nq.gz
│   ├── d8aa6b984fa2c4c4891f114100d205ad99801b34.nq.gz
│   ├── ddfac8ab62cbc9bf0c2f6f386d4afd2672b94518.nq.gz
│   ├── e5b389cdb224a0e125866d3a7c83320efde097bc.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1286733c171d2138bc6dcb59b49ee4df5228fd40.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 20 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[scrapy/formerly](https://github.com/scrapy/formerly)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
