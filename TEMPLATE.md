# NNN. Attack title

English | [한국어](docs/ko/TEMPLATE.md)

*Italic lines are fill instructions. They come out before the entry ships, and so does the language line above them.*

| | |
|---|---|
| **Date** | when this was reproduced, not when the source was published |
| **Class** | reentrancy, oracle manipulation, access control, and so on |
| **Source** | [Author, Venue or publication, Year](link) |
| **Source artifact** | published and it runs / published and it does not / nothing published |
| **Target** | fork of the original deployment, testnet deploy, or minimal reimplementation |
| **Chain / fork block** | Ethereum mainnet at 14684307, or local |
| **solc / EVM version** | 0.6.12 / istanbul |
| **Status** | Reproduced / Partially reproduced / Could not reproduce |
| **Effort** | rough hours, reading included |

*Source artifact gets its own row. On any one entry it is a throwaway field, but collect twenty and it starts being useful.*

*Pin `solc_version` and `evm_version` in `foundry.toml` first, then copy them into the table. A 2021 target run under a post-Cancun EVM has different SELFDESTRUCT semantics after EIP-6780, so a reproduction on the wrong EVM is a wrong answer with a passing test behind it.*

## What the source claims

*Two or three sentences, in plain words, written with the source closed. If that is not possible yet, the reading is not finished.*

## What I did

*Setup and sequence. Which fork block and why that one. Tooling. Every simplification made, each with the reason it does not change the outcome.*

```bash
forge test --match-contract <TestContract> -vvv
```

*Paste the command that actually produced the result below, not a tidied version of it.*

## The vulnerable pattern

```solidity
// the smallest snippet that still shows the bug
```

*One paragraph on why this is exploitable. What the attacker walks away holding, and what the contract assumed while handing it over.*

## Result

*Numbers. Balances before and after, transaction count, gas where it decides whether the attack is worth running. The result is the quantity the test measured, not the green checkmark.*

## Where I diverged from the source

*Assumptions that stopped holding. Parameters that moved in the years since publication. A contract that was quietly upgraded under the call path the source describes goes here too, and so does any step that is written clearly and still does not work when you follow it.*

*If everything matched, write that down. That is a result too.*

## What I did not verify

*The limits, stated plainly. What got simplified, what was taken on faith, and what would take a bigger setup to confirm. Anything guessed at belongs here rather than up in Result.*

## Notes to self

*Open questions, dead ends, things that looked wrong but never got chased down. Keep this section even when it reads like filler.*

## Running it

This directory is a standalone Foundry project. Nothing above it is needed to build or run it.

```bash
forge install   # pulls the forge-std commit pinned for this entry
forge test -vvv
```

Fork tests read `ETH_RPC_URL` from the environment. The block number is pinned inside the test, so no flags are needed. Old blocks need archive access; the README describes what that failure looks like.
