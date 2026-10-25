# OP_PILL / PILL_VERSE

Bitcoin-native Web3 game and NFT prototype built around **OP_NET on Bitcoin L1**.

This repository combines an NFT minting experience, wallet/network handling, an arcade game, leaderboard/dashboard flows, and an OP_NET smart-contract implementation in one project.

## What this project demonstrates

- Bitcoin / OP_NET application architecture
- NFT minting UX with wallet-aware flows
- Testnet/mainnet network separation
- Smart-contract development with AssemblyScript
- Browser-based game logic and state management
- Leaderboard and player dashboard flows
- Supabase-backed application integration
- Responsive UI built without a frontend framework

## Current status

The project is currently structured as a **testnet-first prototype**. Testnet is enabled in the frontend configuration, while mainnet activation is intentionally locked in code until launch readiness.

## Core product pieces

### NFT minting

The frontend supports an OP_PILL collection concept with:

- total supply: 5,000
- per-wallet and per-transaction mint limits
- rarity tiers: Common, Rare, Mythical
- Bitcoin-denominated mint pricing
- wallet/network validation before mint flows

### PILL_CATCHER

A skill-based browser arcade experience connected to the broader PILL_VERSE concept. NFT rarity is designed to affect in-game lives, score multipliers, and reward weighting.

### Dashboard and leaderboard

The repository includes separate player dashboard and leaderboard logic, plus Supabase integration code for server-backed application state and validation flows.

### Smart contract

`contracts/OPPill.ts` contains the OP_NET smart-contract implementation. The project uses AssemblyScript and the BTC Vision runtime/tooling, with scripts for build and deployment workflows.

## Tech stack

| Area | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| Smart contract | AssemblyScript |
| Contract tooling | `@btc-vision/btc-runtime`, `@btc-vision/transaction` |
| Deployment scripts | TypeScript / ts-node |
| Backend integration | Supabase |
| Network | Bitcoin L1 / OP_NET |

## Repository structure

```text
.
├── index.html          # Main minting/product UI
├── app.js              # Wallet, network and minting application logic
├── game.js             # PILL_CATCHER game logic
├── dashboard.js        # Player dashboard
├── leaderboard.js      # Leaderboard UI/logic
├── supabase.js         # Supabase integration
├── contracts/
│   ├── OPPill.ts       # OP_NET smart contract
│   └── deploy.ts       # Contract deployment script
├── assets/             # Visual assets
├── LIGHTPAPER.md       # Product model and roadmap
└── package.json        # Contract build/deploy tooling
```

## Contract commands

Install dependencies:

```bash
npm install
```

Build the contract:

```bash
npm run build
```

Build a debug version:

```bash
npm run build:debug
```

Deploy to testnet:

```bash
npm run deploy:testnet
```

A mainnet deploy command exists in the project tooling, but the application itself currently keeps mainnet activation disabled by default.

## Engineering notes

A few implementation choices were deliberate:

- **No frontend framework:** the client is intentionally implemented in vanilla JavaScript to keep the runtime small and make application state explicit.
- **Network separation:** testnet and mainnet configuration are isolated so production activation is not accidental.
- **Wallet-aware UX:** connection state, network state, balance, mint quantity, limits and modal flows are tracked separately.
- **Accessibility details:** modal focus handling and keyboard escape behavior are implemented in the client logic.
- **Contract/application split:** smart-contract code and browser application code are kept as distinct layers.

## Product documentation

See [`LIGHTPAPER.md`](./LIGHTPAPER.md) for the collection model, game mechanics, reward concept and roadmap.

## Portfolio note

This repository is published as a technical portfolio project showing end-to-end product implementation across frontend, Web3 integration, game logic and smart-contract tooling. Mainnet operation should be treated separately from the prototype code shown here.
