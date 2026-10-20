# Repolex Knowledge Graph of falconry/updraft

RDF knowledge graph data for [falconry/updraft](https://github.com/falconry/updraft), parsed by [repolex](https://repolex.ai).

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
rlex download falconry/updraft
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d34bc8a35bebc898dd71d026ea742635805841bb
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── d34bc8a35bebc898dd71d026ea742635805841bb
│           └── chunk-001.nq.gz
├── blob
│   ├── 46a449a007533f5450e4de93309f09105cb41e9a.nq.gz
│   ├── 4df2d682936c78d0693817c06b512f0681ca8fd3.nq.gz
│   ├── 9214a9fd48f6d552d20f21ce41b8d8538f6487d1.nq.gz
│   ├── b8023d8bc0ca413584a729e5106f86ba8fe65400.nq.gz
│   ├── e1a5a5e007ee496cc823363540ab0b8ec1b27801.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f1a2a16dc584b6d60802d4a9e2125652bd68cc9f.nq.gz
│   ├── f22eb6587b1db289f57a6cfbf2110dc5ba381da2.nq.gz
│   └── fabca811e34e8b748367f21d646db7d6c035e7a1.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── d34bc8a35bebc898dd71d026ea742635805841bb.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
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

[falconry/updraft](https://github.com/falconry/updraft)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
