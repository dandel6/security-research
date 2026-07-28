# Security policy

English | [한국어](docs/ko/SECURITY.md)

This repository is a research log. Public attacks only, no user data, nothing deployed.

## Reporting a vulnerability in this repository

Everything under `reproductions/` is exploit code on purpose, written to run against local forks and testnet deploys. Worth reporting anyway: an entry that reaches past its fork, a script that touches anything outside its own directory, or anything that would leak the RPC key a reader puts in `.env`.

## If an entry points at something still live

This is the report I want.

Reproducing an old attack occasionally turns up code that is still deployed and still unpatched, usually a fork of the original that never took the fix. If you think an entry here gives a working path against a live contract holding funds, mail me at a31323916@gmail.com before opening an issue. I will take the entry down and get in touch with the team. A takedown is not an erasure, since the commit stays in the history and in any fork, and that is the reason nothing goes up here until a fix is live.

Anything I run into that way follows the same rule. The affected team hears about it first, and the entry stays out of this repo until it is fixed and disclosed.

## Scope

Attacks with a public paper, audit report, or post-mortem behind them. Execution against local forks and testnet deploys. Never against a live contract holding funds, and not a zero-day hunt.
