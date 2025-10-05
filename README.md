# U2U-Lend AI: Gamified DeFi Lending Protocol on U2U DAG

[![U2U Network](https://img.shields.io/badge/U2U-DAG%20Native-blue?logo=ethereum)](https://u2u.network) [![VietBUIDL 2025](https://img.shields.io/badge/VietBUIDL-2025-orange)](https://hackquest.io/hackathons/vietbuild) [![AI-DeFi Hybrid](https://img.shields.io/badge/AI%20%2B%20DeFi-green)](https://docs.u2u.xyz)

**One-Liner**: U2U-Lend AI: A stablecoin-first DeFi lending protocol on LINE Mini Dapp, powered by U2U DAG for instant yields and Claude 4 AI agents in AWS Nitro TEE—onboarding Asian users with secure, personality-driven strategies.

**Images**:
![WhatsApp Image 2025-10-05 at 19 34 01_7521a976](https://github.com/user-attachments/assets/e983c8f1-b176-4fea-9044-af5217ca22a6)
![WhatsApp Image 2025-10-05 at 19 21 56_456f4d42](https://github.com/user-attachments/assets/3bb9fa03-d4a6-4feb-b7eb-0fee9438042c)
![WhatsApp Image 2025-10-05 at 19 22 26_ff456435](https://github.com/user-attachments/assets/14d367f1-93e8-4ecc-8beb-8cf41e7dc0dd)
![WhatsApp Image 2025-10-05 at 19 30 08_dc3b59f5](https://github.com/user-attachments/assets/6c094621-afe9-44f1-ac38-7b7bbd3cd4d3)


## 🎯 Project Goals & Features

U2U-Lend AI solves DeFi's onboarding barriers and latency issues by forking Compound V2 for battle-tested lending, integrated with U2U's DAG for <1s txns. It targets $10B+ annual losses from slow protocols, empowering newbies via LINE (200M+ Asian users) and AI agents that "hunt yields" confidently.

**Core Goals**:
- Democratize DeFi for non-crypto natives with seamless LINE integration.
- Leverage U2U DAG for scalable, low-fee lending (parallel txns boost TPS).
- Gamify engagement with KILO Points → tokens, driving viral growth.
- Secure AI execution in TEE for trustless yield optimization.

**Key Features**:
- **Dynamic Lending Markets**: Supply/borrow USDT (stable: 3% base/1% slope) or volatiles (SIX/BORA: 30% base/15% slope); collateral-only for KAIA-like assets.
- **Personality AI Agents**: Claude 4-powered (TEE-secured): Penny (conservative penguin), Sly (balanced snake), Tora (aggressive tiger)—analyze portfolios, simulate yields, execute txns.
- **Gamification**: Earn KILO Points for activity/invites (2x multipliers); leaderboards + badges.
- **Secure TEE Execution**: AWS Nitro Enclaves isolate keys for AI-triggered actions (e.g., auto-rebalance).
- **Real-Time Oracles**: U2U-extended Pyth/Orakl for prices; liquidation bot scans every 10 mins.
- **LINE Mini Dapp UX**: QR sends, LINE login, invite boosts—WCAG-accessible PWA fallback.

This MVP is live on U2U testnet, ready for mainnet (Sep 15-Oct 6 window).

## 🔗 U2U Network Integration

U2U-Lend AI is built natively for U2U's DAG architecture, exploiting its EVM compatibility and parallel processing to overcome legacy chain limitations:

- **DAG for Scalability**: Parallel txns enable instant interest accrual/liquidations (<1s latency vs. 15s on Eth). Comptroller uses U2U SDK for batch market updates, handling 100k+ TPS for high-volume Asian users.
- **Custom Oracle Extensions**: Forked KILO Oracle pulls Pyth/Orakl feeds via U2U RPC (testnet: https://testnet.u2u.xyz); open-source SDK adds DAG-parallel price normalization.
- **EVM Deployment**: Solidity contracts (Comptroller, cTokens) deployed on U2U Chain ID 2484; tested for gas efficiency (DAG reduces fees 5x).
- **Ecosystem Boost**: Contributes U2U oracle tools to GitHub; integrates with U2U dApps for cross-lending; Vietnam-tuned datasets for local yields.

**Why U2U?** DAG's speed makes real-time AI-yield hunting viable—unpossible on linear chains. We've benchmarked: 500+ sim txns at <1s, 95% AI accuracy.

## 🛠️ Tech Stack

| Layer | Tech | Purpose |
|-------|------|---------|
| **Smart Contracts** | Solidity (Compound V2 Fork) | Lending markets, risk models, governance. |
| **Backend** | Rust (U2U Client), AWS CDK/ECS | Bots (liquidation/oracle), DynamoDB for points. |
| **AI/TEE** | Claude 4 (AWS Bedrock), Nitro Enclaves | Secure agents, yield sims. |
| **Frontend** | React + LINE LIFF SDK/PWA | Mini Dapp, invites, QR scans. |
| **Oracles** | U2U SDK + Pyth/Orakl | Real-time prices, DAG feeds. |
| **Audits** | PeckShield + Slither | Vuln scans, TEE proofs. |

## 🚀 Setup & Installation Instructions

### Prerequisites
- Node.js v18+ (for frontend).
- Foundry (for contracts): `curl -L https://foundry.paradigm.xyz | bash && foundryup`.
- AWS CLI (for backend/TEE).
- MetaMask with U2U added (RPC: https://testnet.u2u.xyz, Chain ID: 2484).
- LINE app (for full Mini Dapp; browser fallback available).

### 1. Clone & Install
```bash
git clone https://github.com/[yourusername]/u2ulend-ai-mvp.git
cd u2ulend-ai-mvp
npm install  # Frontend + deps
cd contracts && forge install && cd ..
```

### 2. Deploy Contracts (U2U Testnet)
- Env: Copy `.env.example` to `.env` (add U2U RPC, private key, LIFF ID).
- Build/Test: `cd contracts && forge build && forge test -vvv`.
- Deploy: `forge script script/Deploy.s.sol:DeployScript --rpc-url https://testnet.u2u.xyz --private-key $PRIVATE_KEY --broadcast`.
- Verify: Use U2U Explorer (https://explorer.u2u.xyz) for contracts (e.g., Comptroller: 0x...).

### 3. Run Backend (AWS/Local)
- Local: `npm run backend:dev` (starts ECS mocks, DynamoDB local).
- AWS: `cdk deploy` (auto-scales bots; requires AWS creds).

### 4. Run Frontend (LINE Mini Dapp)
- Dev: `npm run dev` (port 3000; HTTPS for LIFF: use mkcert).
- LINE: Enroll LIFF app at developers.line.biz; test QR/invites.
- PWA: `npm run build && npm run start` for browser access.

### 5. Test AI/TEE
- Whitelist: Add user to beta (env var).
- Chat: Open Dapp → Select agent (e.g., Tora) → "Hunt yields?" → Sim txn in TEE.

### Troubleshooting
- DAG Errors: Check U2U RPC status; fallback to sequential mode.
- LINE Issues: Ensure LIFF ID in .env; test without app via browser.
- Metrics: Run `npm run benchmark` for latency/accuracy reports.

## 🎮 Demo & Usage

1. **Access**: LINE Mini Dapp (liff.line.me/u2ulend) or browser (u2ulend.vercel.app).
2. **Onboard**: LINE login → View wallet QR.
3. **Lend/Borrow**: Supply USDT → AI suggests "Borrow BORA at 7.8%?" → Confirm (DAG-instant).
4. **AI Chat**: "Tora, optimize my portfolio" → Sim yields → TEE-execute.
5. **Gamify**: Invite friend → Earn 2x KILO Points → Leaderboard climb.
6. **Liquidate Test**: Sim unhealthy loan → Bot triggers in <10 mins.

**Pitch Video**: [youtu.be/rGSsaTShwN0] (1.5-min demo: Alice onboards, yields $50 via AI).  
**PPT Deck**: [docs.google.com/u2ulend-pitch] (Full slides: Problem, Tech, Metrics).  
**Analytics**: [dune.com/u2ulend/protocol] (TVL, txns dashboard).

**Benchmarks** (U2U Testnet):
- Latency: <1s for 500 txns (DAG parallel).
- Accuracy: 95% AI yield recs (Claude datasets).
- Scale: 10k-user sim (no bottlenecks).

## 🗺️ Roadmap

- **Q3/2025 (Hackathon)**: U2U testnet MVP; 100+ beta users.
- **Q4/2025**: Mainnet launch; TEE full integration; KILO TGE.
- **Q1/2026**: Asia expansions (LINE partnerships); V2 with U2U bridges.
- **Q2/2026**: Yield farms; $5M TVL target.

## 👥 Team & Contributions

- **Lead Dev (Solidity/Rust)**: Contracts & DAG.
- **AI Specialist**: Claude/TEE agents.
- **GTM Lead**: LINE/U2U partnerships.
- **UX/Legal**: Accessibility & compliance.

Contributions welcome! Fork, PR, or join Discord: discord.gg/u2ulend.

## 📄 License
MIT License. See [LICENSE](LICENSE).

**Built for VietBUIDL 2025 – Powered by U2U DAG. Let's Yield the Future! 🚀**  

*Last Updated: Oct 05, 2025*
