<p align="center">
  <img src="L.png" alt="Konstellation" width="96" height="96">
</p>

<h1 align="center">Konstellation</h1>

<p align="center">
  A sovereign, EVM-compatible Layer 1 built on the Cosmos SDK.
</p>

---

Konstellation is a Layer 1 blockchain with its own validator set and its own
consensus. It is not a rollup, a sidechain or an appchain secured by another
network.

- **For Solidity developers and wallet users**, it behaves like an
  Ethereum-family chain. Contracts compile and deploy unchanged. The node serves
  the standard Ethereum JSON-RPC over HTTP and WebSocket. MetaMask, Rabby and
  other EVM wallets work as they do on any EVM chain, and Blockscout provides
  the block explorer.
- **For Cosmos operators**, it is a standard Cosmos SDK application: one Go
  binary (`konstellationd`), upgrades coordinated by on-chain governance, and
  IBC for interoperability.

Blocks are final as soon as they are committed. CometBFT consensus gives
deterministic finality, so there are no reorganisations and no confirmation
window to wait out.

> **Status: pre-launch.** No Konstellation network is live yet. The details
> below describe the chain as designed and may change before launch.

## Networks

| | Mainnet | Testnet | Devnet |
|---|---|---|---|
| Network (Cosmos chain-id) | `konstellation-1` | `testnet-1` | `devnet-1` |
| EVM chain ID | **5667** | **56671** | **56672** |
| Purpose | the public network | validator and upgrade rehearsal | building and testing dapps |
| Status | not launched | not launched | not launched |

| Token | |
|---|---|
| Symbol | **KASH**, the gas, staking and governance token |
| Decimals | 18 (base unit `esp`; 1 KASH = 10¹⁸ esp) |
| Address prefix (Cosmos) | `kons` |

RPC endpoints, the explorer and the devnet faucet will be listed here when the
networks launch. Dapp developers should start on **devnet**: it runs the same
software release that mainnet is about to run, one to two weeks ahead of
mainnet.

## Built for smart accounts

- **ERC-4337.** EntryPoint v0.7 and v0.8 are in the genesis state at their
  canonical addresses, so existing bundlers and wallet SDKs work without
  redeployment.
- **Passkeys.** The P-256 signature precompile (RIP-7212) is available, so
  WebAuthn and passkey-based accounts are cheap to verify on-chain.
- **EIP-7702.** Externally owned accounts can delegate to smart-account code.
  The EVM runs the Prague fork.

## Security first

Konstellation is designed to hold real value from its first block, and its
defaults are conservative:

- **No forks of core infrastructure.** The Cosmos SDK, CometBFT, IBC and the
  EVM module are used as unmodified upstream dependencies, so upstream security
  fixes can be applied as soon as they are released.
- **No bridge at launch.** Bridges come later, one at a time, each audited,
  rate-limited and soaked first.
- **A careful start for the validator set.** The network launches with a
  small, professionally operated validator set. There is a published roadmap
  for opening it to more operators over time.
- **Audits before value.** Audits and a bug bounty come before launch.

## Repositories

| Repository | What it is |
|---|---|
| [`konstellation`](https://github.com/Konstellation-Network/konstellation) | the chain: source for the `konstellationd` node |
| [`networks`](https://github.com/Konstellation-Network/networks) | genesis files, peers and upgrade instructions for each network |
| [`contracts`](https://github.com/Konstellation-Network/contracts) | contracts in the genesis state, with verification |
| [`chain-config`](https://github.com/Konstellation-Network/chain-config) | chain definitions for dapps (viem, wagmi, wallet add-network) |
| [`docs`](https://github.com/Konstellation-Network/docs) | developer documentation |
| [`whitepaper`](https://github.com/Konstellation-Network/whitepaper) | the whitepaper, as versioned releases |
| [`explorer`](https://github.com/Konstellation-Network/explorer) | Blockscout explorer deployment |
| [`faucet`](https://github.com/Konstellation-Network/faucet) | test-token faucet for devnet and testnet |

## Learn more

- **Whitepaper:** design, token economics and the launch plan, in the
  [`whitepaper`](https://github.com/Konstellation-Network/whitepaper) repo
  (currently a draft).
- **Security:** please report vulnerabilities privately through
  [GitHub's private vulnerability reporting](https://github.com/Konstellation-Network/konstellation/security/advisories/new),
  not in a public issue. See [SECURITY.md](https://github.com/Konstellation-Network/.github/blob/main/SECURITY.md).

---

<sub>Nothing on this page is an offer of, or investment advice about, any
token. Konstellation is pre-launch software and the details above may change.</sub>
