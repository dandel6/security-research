# Security research

English | [한국어](docs/ko/README.md)

I take a smart contract attack that has already been published, rebuild it from the paper or the post-mortem, and try to make it fire in a local test. Each entry is a writeup plus a Foundry project you can clone and run. The writeup covers what the source claimed and what my version actually did.

Failed reproductions stay in the index with the reason.

## Reproductions

Nothing has landed yet.

| # | Attack | Class | Source | Status | Date |
|---|---|---|---|---|---|

Status is one of three: **Reproduced**, **Partially reproduced**, **Could not reproduce**.

## How each entry is structured

Every writeup follows [TEMPLATE.md](TEMPLATE.md): the source's claim, the setup I ran including the fork block and EVM version, the vulnerable pattern, the numbers, then where I diverged and what I did not verify.

Each entry also records whether the source shipped code and whether that code still runs today.

## Scope

Everything here targets attacks that are already public, usually a paper, an audit report, or a disclosed post-mortem. I run all of it against local forks and testnet deploys, never against a live contract holding funds.

I am not hunting for zero-days. A reproduction still turns one up now and then, usually an unpatched fork of the original code. When that happens the affected team hears about it first, and the entry stays out of this repo until it is fixed and disclosed. If you think something already here points at live unpatched code, [SECURITY.md](SECURITY.md) has the address.

## Running an entry

Each `reproductions/NNN-slug/` is a standalone Foundry project with no root build above it.

```sh
cd reproductions/001-slug
forge install
forge test -vvv
```

Fork tests need an archive node. Most of these attacks happened at blocks that are years old by now, and a free-tier endpoint will not serve state at that height; it fails on the state lookup, which looks like a broken PoC rather than a missing node. Copy `.env.example` to `.env` and fill in `ETH_RPC_URL`, or whichever chain the entry names. `ETHERSCAN_API_KEY` is there because pulling victim source with `cast etherscan-source` is most of the setup work.

Every project pins `solc_version` and `evm_version` in its own `foundry.toml` instead of taking the defaults. That is deliberate: a 2021 attack replayed under a Cancun EVM is not the same attack, since SELFDESTRUCT changed under EIP-6780 and PUSH0 did not exist yet. If an entry only reproduces under one specific EVM version, that goes in the writeup.

## About

Independent researcher, based in Korea. Before this I built [Perp DEX](https://github.com/dandel6/dex), a hybrid perpetual futures exchange: Rust matching engine off-chain, Solidity settlement on Arbitrum Sepolia, EIP-712 verification and margin re-checks written by hand with no OpenZeppelin underneath. Spending a year on contracts that hold collateral is what got me interested in breaking them.

Working through the smart contract security literature now. If you want another reader on something before it goes to audit, or you think an entry here is wrong, email me.

Contact: a31323916@gmail.com

Issues are welcome. I would rather not take PRs on the reproductions themselves.

## License

[MIT](LICENSE)
