# Uniswap V4 — The Hooks Revolution

![Stars](https://img.shields.io/github/stars/Uniswap/v4-core?style=social)
![Language](https://img.shields.io/github/languages/top/Uniswap/v4-core)

> **Next-gen AMM engine.** V4 replaces the monolithic pool contract with a singleton architecture and programmable "hooks" — custom logic that runs at every step of the swap lifecycle.

---

## What Changed From V3

| Feature | V3 | V4 |
|---------|-----|-----|
| **Architecture** | One contract per pool | One singleton for ALL pools |
| **Custom Logic** | None — fixed behavior | Hooks — programmable at every swap step |
| **Gas Efficiency** | High per-pool creation | 99% cheaper pool creation |
| **Fees** | Static tiers (0.05%, 0.30%, 1%) | Dynamic fees via hooks |
| **Native ETH** | WETH only | Native ETH support |

## Hooks: The Game Changer

Hooks are external contracts that "hook into" pool actions:

```
Swap Lifecycle:
  beforeSwap() → swap executes → afterSwap()
  beforeAddLiquidity() → addLiq executes → afterAddLiquidity()
  beforeRemoveLiquidity() → removeLiq executes → afterRemoveLiquidity()
```

### What Hooks Enable

- **TWAMM** — Time-Weighted Average Market Maker (large orders broken into pieces)
- **Dynamic fees** — adjust based on volatility, volume, or any oracle
- **Limit orders** — on-chain, trustless, non-custodial
- **Custom oracles** — geometric mean, median, TWAP variants
- **LVR mitigation** — Loss-Versus-Rebalancing protection for LPs
- **MEV-aware routing** — hooks that detect and counter sandwich attacks

## Architecture

```
UniswapV4PoolManager (singleton)
  ├── Pool 1: USDC/ETH  (hook: dynamic fee)
  ├── Pool 2: ETH/WBTC  (hook: TWAMM)
  └── Pool 3: DAI/USDC  (hook: limit orders)
```

One contract manages all pools. New pool creation is just writing to a mapping — no deployment cost.

## Key Technical Changes

1. **ERC-6909** — New token standard for pool claims (more gas-efficient than ERC-1155)
2. **Flash accounting** — Net balance tracking instead of per-step transfers
3. **Donate()** — Direct fee injection for external incentive systems

## For Developers

```solidity
// A minimal hook contract
contract MyHook is BaseHook {
    function afterSwap(
        address sender,
        PoolKey calldata key,
        uint256 amount0,
        uint256 amount1
    ) external override returns (bytes4) {
        // Custom logic after every swap
        return BaseHook.afterSwap.selector;
    }
}
```

## Why It Matters

V4 turns Uniswap from a DEX into a **platform**. Anyone can build custom AMM logic without forking the core contracts. It's the "app store" moment for DeFi.

---

**Repo:** [github.com/Uniswap/v4-core](https://github.com/Uniswap/v4-core)

**Category:** [DeFi & Trading](../README.md#defi--trading)
