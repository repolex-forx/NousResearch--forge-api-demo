# Repolex Knowledge Graph of NousResearch/forge-api-demo

RDF knowledge graph data for [NousResearch/forge-api-demo](https://github.com/NousResearch/forge-api-demo), parsed by [repolex](https://repolex.ai).

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
rlex download NousResearch/forge-api-demo
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 99852c17bff8bc4a2bb7a051b50f90a2d07614eb
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 99852c17bff8bc4a2bb7a051b50f90a2d07614eb
│           └── chunk-001.nq.gz
├── blob
│   ├── 13d69902fbeaae23a982dbdec8f526a2e6ce6fb6.nq.gz
│   ├── 25c36e26bbcea5f4d3295d8d0c6eef3294446a60.nq.gz
│   ├── 82f927558a3dff0ea8c20858856e70779fd02c93.nq.gz
│   ├── ad0b99d7664b8379d413a6dff17fce282bc62657.nq.gz
│   ├── b5bdfa67b0a6074850b73224a5a7364c5fddbdb0.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 99852c17bff8bc4a2bb7a051b50f90a2d07614eb.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
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

[NousResearch/forge-api-demo](https://github.com/NousResearch/forge-api-demo)

---
*Parsed on 2026-10-09 by [repolex](https://repolex.ai)*
