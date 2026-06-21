# Foundry — The Ethereum Dev Powerhouse

![Stars](https://img.shields.io/github/stars/foundry-rs/foundry?style=social)
![Language](https://img.shields.io/github/languages/top/foundry-rs/foundry)

> **Blazing-fast Ethereum development toolkit written in Rust.** Compile, test, fuzz, deploy, and interact with smart contracts — all in one tool.

---

## Why Foundry?

Foundry replaced Truffle/Hardhat for serious Solidity devs because:

- **Tests in Solidity, not JavaScript** — write tests in the same language as your contracts
- **Built-in fuzzing** — property-based testing catches edge cases automatically
- **Rust speed** — compiles and tests 10-50x faster than Hardhat
- **Cast** — command-line Ethereum Swiss Army knife

## The Toolchain

| Tool | What It Does |
|------|-------------|
| **forge** | Compile, test, deploy, verify contracts |
| **cast** | Interact with contracts, send txs, decode calldata |
| **anvil** | Local Ethereum node for development (like Ganache but faster) |
| **chisel** | Solidity REPL — experiment in real-time |

## Quick Start

```bash
# Install
curl -L https://foundry.paradigm.xyz | bash
foundryup

# New project
forge init my-project
cd my-project

# Write a test in Solidity (not JS!)
forge test        # Run tests
forge test -vv    # Verbose output
forge coverage    # Code coverage

# Deploy
forge create --rpc-url $RPC_URL \
  --private-key $PRIV_KEY \
  src/MyContract.sol:MyContract

# Verify on Etherscan
forge verify-contract <address> src/MyContract.sol:MyContract \
  --etherscan-api-key $ETHERSCAN_KEY
```

## Fuzz Testing

Foundry's killer feature — it generates random inputs to find bugs you'd never think of:

```solidity
function testTransfer(uint256 amount) public {
    vm.assume(amount <= token.balanceOf(alice)); // constrain
    token.transfer(bob, amount);
    assertEq(token.balanceOf(bob), amount);
}
```

Run with `forge test` and Foundry tries hundreds of random `amount` values.

## Invariant Testing

Even more powerful — test that properties hold through ANY sequence of actions:

```solidity
function invariant_totalSupplyEqualsSumOfBalances() public {
    assertEq(token.totalSupply(), sumOfAllBalances());
}
```

## Cast: The CLI Swiss Army Knife

```bash
# Check ETH balance
cast balance 0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045

# Call a contract
cast call 0xContract "balanceOf(address)" 0xAddress

# Decode calldata
cast 4byte-decode 0xa9059cbb...

# Estimate gas
cast estimate 0xContract "transfer(address,uint256)" 0xTo 1000
```

## Why Devs Are Switching

- **Tests in Solidity** — no context-switching between contract code and JS tests
- **Fork testing** — test against mainnet state with `forge test --fork-url`
- **Gas snapshots** — `.gas-snapshot` files track optimization wins
- **Scripting in Solidity** — deployment scripts are Solidity, not JS

---

**Repo:** [github.com/foundry-rs/foundry](https://github.com/foundry-rs/foundry)

**Category:** [Smart Contracts & Infrastructure](../README.md#smart-contracts--infrastructure)
