# Repolex Knowledge Graph of uraimo/Awesome-Swift-Playgrounds

RDF knowledge graph data for [uraimo/Awesome-Swift-Playgrounds](https://github.com/uraimo/Awesome-Swift-Playgrounds), parsed by [repolex](https://repolex.ai).

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
rlex download uraimo/Awesome-Swift-Playgrounds
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── fed28248bd31ff829c2223233da2e53dc77b6581
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── fed28248bd31ff829c2223233da2e53dc77b6581
│           └── chunk-001.nq.gz
├── blob
│   ├── 03c9caa236b02e481f27e52c1f9b1c7d7a416e47.nq.gz
│   ├── 10468b29eaa6c7a5cbd07f46477313c3846f71ec.nq.gz
│   ├── 5c2bcf5923d51890427dce826c39845167eb13bf.nq.gz
│   ├── 7be359a1a5d92a54601726196c9a8caba8fcf74d.nq.gz
│   ├── b0ed802765498c4315dd534a955a2aa982e84bd7.nq.gz
│   ├── d630e159ab23fac1df2fb8259033ddfc0314870d.nq.gz
│   └── d6bc77fd569ecfce88a528d43d907c9e18fee795.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── fed28248bd31ff829c2223233da2e53dc77b6581.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 15 files
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

[uraimo/Awesome-Swift-Playgrounds](https://github.com/uraimo/Awesome-Swift-Playgrounds)

---
*Parsed on 2026-11-10 by [repolex](https://repolex.ai)*
