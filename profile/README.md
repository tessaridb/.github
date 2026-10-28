<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/tessaridb-lockup-white-1024.png">
  <img src="assets/tessaridb-lockup-1024.png" alt="TessariDB" width="360">
</picture>

## The stack around the model, in one store.

Records, search, vectors, graphs, queues, topics, files, geometry and sealed secrets:
eleven engines over one transactional store, in one Rust binary, on its own storage engine.

[![engine](https://img.shields.io/badge/engine-0.39.2-6B5FD1?style=flat-square)](https://github.com/tessaridb/tessaridb)
[![tessarikv](https://img.shields.io/badge/tessarikv-0.2.0-2E9E6B?style=flat-square)](https://github.com/tessaridb/tessarikv)
[![s3](https://img.shields.io/badge/s3-0.8.1-2FB5B0?style=flat-square)](https://github.com/tessaridb/tessaridb-s3)
[![oauth](https://img.shields.io/badge/oauth-0.3.0-D9A733?style=flat-square)](https://github.com/tessaridb/tessaridb-oauth)
[![agent memory](https://img.shields.io/badge/agent%20memory-0.5.0--beta-6B5FD1?style=flat-square)](https://am.tessaridb.com)
[![clients](https://img.shields.io/badge/clients-rust%20·%20python%20·%20ts%20·%20go%20·%20kotlin-6B5FD1?style=flat-square)](#clients)
[![docker](https://img.shields.io/badge/docker-tessaridb%2Ftessaridb-D98E33?style=flat-square)](https://hub.docker.com/r/tessaridb/tessaridb)

**[tessaridb.com](https://tessaridb.com) · [docs](https://docs.tessaridb.com) ·
[kv.tessaridb.com](https://kv.tessaridb.com) · [s3.tessaridb.com](https://s3.tessaridb.com) ·
[am.tessaridb.com](https://am.tessaridb.com) · [oauth.tessaridb.com](https://oauth.tessaridb.com)**

</div>

An AI product usually ends up running a database, a search engine, a vector index, a cache, a queue, an
event log and somewhere for files, with no transaction across any of them. TessariDB is one store that does
all of those jobs on the same records, under one snapshot, in one language. Not the fastest at any single
job; enough at all of them, and nothing to keep in step.

## Products

### <img src="assets/tessaridb-mark-128.png" width="28" alt=""> TessariDB

The database. Eleven engines, one transaction, a flexible cluster — sharding, multi-master, automatic failover — on its own engine, TessariKV.

**[Repository](https://github.com/tessaridb/tessaridb) · [Site](https://tessaridb.com) ·
[Docs](https://docs.tessaridb.com)** · `0.39.2`

### <img src="assets/tessarikv-mark-128.png" width="28" alt=""> TessariKV

The heart of TessariDB: an embedded key-value storage engine in pure Rust, lock-free first, with a stable file
format. TessariDB runs on it from 0.36.0.

**[Repository](https://github.com/tessaridb/tessarikv) · [Site](https://kv.tessaridb.com) ·
[Docs](https://docs.tessaridb.com/kv)** · `0.2.0`

### <img src="assets/tessaridb-s3-mark-128.png" width="28" alt=""> TessariDB S3

S3-compatible object storage in Rust. Metadata in TessariDB, bytes erasure-coded across nodes. Its console signs in
through TessariDB OAuth, and the settings its nodes share are kept in TessariDB.

**[Repository](https://github.com/tessaridb/tessaridb-s3) · [Site](https://s3.tessaridb.com) ·
[Docs](https://docs.tessaridb.com/s3)** · `0.8.1`

### <img src="assets/tessaridb-oauth-mark-128.png" width="28" alt=""> TessariDB OAuth

Sign-in for your own applications: an OAuth 2.1 authorization server and OpenID provider in Rust, with every piece
of its state in TessariDB. Passkeys, passwords with an authenticator app, consent, and an account page where users
see and end their sessions and grants, in one binary with its admin panel.

**[Repository](https://github.com/tessaridb/tessaridb-oauth) · [Site](https://oauth.tessaridb.com) ·
[Docs](https://docs.tessaridb.com/oauth)** · `0.3.0`: the admin API answers the subject a sector knows an account by

### <img src="assets/agent-memory-mark-128.png" width="28" alt=""> Agent Memory

Goals, plans, tasks and what each agent remembers, as queryable records. CLI, REST and MCP.

**[Site](https://am.tessaridb.com) · [Docs](https://docs.tessaridb.com/am)** · `0.5.0-beta`

## Clients

Apache-2.0, all checked against one [protocol and conformance corpus](https://github.com/tessaridb/tessaridb-protocol):

- **[Rust](https://github.com/tessaridb/tessaridb-sdk-rust)**: `tessaridb-client` `0.13.0`
- **[Python](https://github.com/tessaridb/tessaridb-sdk-python)**: `tessaridb-client` `0.13.0`
- **[TypeScript](https://github.com/tessaridb/tessaridb-sdk-js)**: `@tessaridb/client` `0.13.0`
- **[Go](https://github.com/tessaridb/tessaridb-sdk-go)**: `github.com/tessaridb/tessaridb-sdk-go` `0.13.0`
- **[Kotlin](https://github.com/tessaridb/tessaridb-sdk-kotlin)**: `com.tessaridb:tessaridb-client` `0.13.0`
- **[S3 SDK and CLI](https://github.com/tessaridb/tessaridb-s3-client)**: `tessaridb-s3-client` `0.2.1`, for S3-compatible storage
- **[Agent plugins](https://github.com/tessaridb/tessaridb-agent-plugins)**: for Claude Code and Codex

## Start

```bash
docker run -d --name tessaridb \
  -p 9080:9080 -p 8000:8000 \
  -v tessaridb-data:/var/lib/tessaridb \
  -e TESSARIDB_INITIAL_USER=owner \
  -e TESSARIDB_INITIAL_PASSWORD='choose-a-real-one' \
  tessaridb/tessaridb
```

The console is at `http://localhost:8000`. Next: [the docs](https://docs.tessaridb.com).

Production use is free, commercial included (BUSL-1.1, each release converts to Apache-2.0 after four years).
Clients, protocol and TessariKV are Apache-2.0. hello@tessaridb.com

© 2026 [@boogvar](https://github.com/boogvar)
