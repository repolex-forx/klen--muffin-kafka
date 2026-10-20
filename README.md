# Repolex Knowledge Graph of klen/muffin-kafka

RDF knowledge graph data for [klen/muffin-kafka](https://github.com/klen/muffin-kafka), parsed by [repolex](https://repolex.ai).

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
rlex download klen/muffin-kafka
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f5e8bf63a8efd4b95ea4666ea157806291a30cd7
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f5e8bf63a8efd4b95ea4666ea157806291a30cd7
│           └── chunk-001.nq.gz
├── blob
│   ├── 00e576ca0d086c658e4614a54ca6f5b65ab96d12.nq.gz
│   ├── 070cea9582b40e2376e1066cd4ae0b955971e269.nq.gz
│   ├── 0a6ee958310ca78a98bf4803c291d5898c7fd5b4.nq.gz
│   ├── 1150fa2567aee2b6bee2300695e565097dd67e59.nq.gz
│   ├── 16ff402cd659e576ed3eb0580716703adb59aefc.nq.gz
│   ├── 1fc2edd33ecad2907f9520e79600ff3dbe7f04ad.nq.gz
│   ├── 23c5c150f58bdd129447223d88288e859f8cccb1.nq.gz
│   ├── 282d563f3ccda866cfaa5c8d9b05919df433e9d5.nq.gz
│   ├── 3b3fa4e2568de917830db12f8de7cdc0d711619f.nq.gz
│   ├── 3b71fd1204ac038c9bc13b7e2a6a6ab7de7cd5c3.nq.gz
│   ├── 3d3de9177b065ccd2b82e03a2cd70dd8b0e5323a.nq.gz
│   ├── 419d5cc058bf616a7dcd26c7e945826230033184.nq.gz
│   ├── 4571b3f9402458ce4bc7c6b210f000f4823a0482.nq.gz
│   ├── 47d96f97c822d862fa3767205a2fba65d3428d16.nq.gz
│   ├── 4a060cc8ce501e4a5b9157c2f5ed52285582dd60.nq.gz
│   ├── 589e6e718508039b52257b9ad2846ebb481848ad.nq.gz
│   ├── 5ab8e07291122efcbed1fcc55d11b7794ec565b7.nq.gz
│   ├── 5f1d5686f3dc12105665875988bbe0b90d32c2bc.nq.gz
│   ├── 666ce2a519fd8f0c3599a11f968422b82612ca92.nq.gz
│   ├── 78df056a6afd6b2f7c5a8695635380a19f30acd9.nq.gz
│   ├── 7a3f07ab83552f47a8705fa5d22729a324a2f71a.nq.gz
│   ├── 853e4d1d41872205e559c43a95a0f6deb1242d6a.nq.gz
│   ├── 887b7705cc31d5b723d57a5a1c1b24236bea6219.nq.gz
│   ├── 8a8942776681b65148b77651beca70924fe42530.nq.gz
│   ├── a500c94b9a640ca5a47df32d530ad4c85899c43d.nq.gz
│   ├── a605f571c79d06d486dfd6f4c12a6011da0c6417.nq.gz
│   ├── bedd27b20c2c091bf28006a787e691286a9c8ec6.nq.gz
│   ├── ce48f87110f5a00c4f3320f9ed0c8e630cb23daf.nq.gz
│   ├── d063574d7f82f53b73cccb989fc0dc1b523251e9.nq.gz
│   ├── e4c9ee04e447944b4ea878d28bfa86df84bf827e.nq.gz
│   ├── e5a794a881f4f76ae2b54a734d586d77184bfdab.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e728d03676c20ba87a39556e60b642f5df17ebde.nq.gz
│   ├── f451f18d82171b32e33a913d0e74a9f31960d702.nq.gz
│   ├── f5e6aaa71bdf24950426a65d8ea23666b69e546e.nq.gz
│   └── faaec896fb3a54fdfbb850a5096253a9945547f8.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f5e8bf63a8efd4b95ea4666ea157806291a30cd7.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 42 files
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

[klen/muffin-kafka](https://github.com/klen/muffin-kafka)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
