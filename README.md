# Repolex Knowledge Graph of canonical/pylego

RDF knowledge graph data for [canonical/pylego](https://github.com/canonical/pylego), parsed by [repolex](https://repolex.ai).

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
rlex download canonical/pylego
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 971f6ecec368171f6bc44f5baa92a0b92255ccee
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 971f6ecec368171f6bc44f5baa92a0b92255ccee
│           └── chunk-001.nq.gz
├── blob
│   ├── 0124f27d851dca57886af88a15fd715ac2be2ca6.nq.gz
│   ├── 09f168534122538ba63cdfc4a40dd861ea68a273.nq.gz
│   ├── 0b9281a62292826967d7913b298db1a3e11c7054.nq.gz
│   ├── 13af703428e23ce7d56cf7a1bc7061b64a8f6a18.nq.gz
│   ├── 15e8e95b43d4d19d718ffea0330290bf3cb9da3d.nq.gz
│   ├── 1adcaad4890c04b1bf7f53b851f0cf5e3af6eeb3.nq.gz
│   ├── 1dd841e162272b8ad1196c950bf29628aa9c4b5a.nq.gz
│   ├── 2975bd2a618e6d0ca9024b0bfd1514df81837af5.nq.gz
│   ├── 2d59c0fd9c04129d9b1e44c9f77e76af55dc0ddf.nq.gz
│   ├── 40e1703c60042cc2827f9a8da14379e5e5156b37.nq.gz
│   ├── 4605b1954f59309080432cdb9e4c163af0d5a186.nq.gz
│   ├── 5cfaa8aedaeef7374ab0a33794460d7da41a291b.nq.gz
│   ├── 5f8fe246293de96bfa5033ace27907df08211a7f.nq.gz
│   ├── 672d266015aeb5add75df0ea366a12472031125f.nq.gz
│   ├── 6d4780637b7776064b337b0dd95fd88f275625fc.nq.gz
│   ├── 7815c2761e256518ee4448c3aa199eb5aead1ba5.nq.gz
│   ├── 79dbb11db079151dd48013a9bf6f13bf09f59013.nq.gz
│   ├── 8683c92b6eeea1ad8c0a28420454ca08f178f1f5.nq.gz
│   ├── 8becc9c65c1adc9e39ea6be426735bf1ca7fd985.nq.gz
│   ├── 966541f83a34f54b6214c2a8d235a4aa79b34a63.nq.gz
│   ├── aaf40e4edd650bc35e240ab85729a2d2c8b98bbb.nq.gz
│   ├── c0fc65f95f6046d8a6abddfe423253a425150ae3.nq.gz
│   ├── c64d700a489c73f3d00adbea190ca31c93b49879.nq.gz
│   ├── d016f149071d5ac85c4d7f016e99dd89e4f16aef.nq.gz
│   ├── d31c6e3ca6fa5f86966158976da30034555e181f.nq.gz
│   ├── dbad5c43486603be7c034541e8f1e5d5386ae7cb.nq.gz
│   ├── f0a134f7e06d2b83edb2236962f4b815058ff117.nq.gz
│   ├── f15cb5b68dfba9f37bf5bc1ff6b46f7032d8a42e.nq.gz
│   ├── f549bbe42b1241e360b926fc1de73c161c74f13b.nq.gz
│   ├── fbbf4caee883abda797acaafd4b7be12a8101306.nq.gz
│   └── fc64d62350db03e0329ae4ea10da687fe6debba7.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 971f6ecec368171f6bc44f5baa92a0b92255ccee.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 39 files
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

[canonical/pylego](https://github.com/canonical/pylego)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
