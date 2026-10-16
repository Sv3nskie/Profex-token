# Profex token

A single-file Solidity contract (`PROFEX.sol`) for a BEP-20 token named "Professor Exchange" (symbol `Profex`, 18 decimals, 1,000,000,000 total supply). It is a reflection-style token with transfer fees. On deployment it creates a PancakeSwap V2 pair against WBNB.

## What the contract does

- Mints 60% of the supply to the deployer and 40% to a hard-coded development wallet.
- Charges these fees on transfers that are not exempt: 2% liquidity, 3% burn (sent to `0x...dEaD`), 5% development wallet and 0% reflection. The owner can change the reflection and liquidity percentages.
- Swaps and adds liquidity automatically once the contract holds 1,000,000 tokens.
- Has a max transaction amount of 100,000,000 tokens, which the owner can adjust.
- Lets the owner set fee exclusions, reward exclusions and `lock`/`unlock` ownership.

## Stack

- Solidity `>=0.8.13`, with no external imports (SafeMath, Address, Ownable and the Uniswap V2 interfaces are inlined)
- PancakeSwap V2 router `0x10ED43C718714eb63d5aA57B78B54704E256024E` (BSC mainnet)

## Building it

The repository has no build tooling. Compile `PROFEX.sol` with solc 0.8.13 or later, for example in Remix. The constructor calls the PancakeSwap router, so you have to deploy to BSC or to a fork of it.
