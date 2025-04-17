# 🚀 CryptoDevs DAO

A **fully on‑chain, NFT‑gated DAO** where every CryptoDevs NFT equals one vote. Members propose NFT purchases, vote, and—if the proposal passes—the DAO contract spends treasury ETH autonomously.

---

## ✨ Features

| Layer | Highlights |
|-------|-----------|
| **Smart‑contracts** | `CryptoDevsNFT` (ERC‑721 Enumerable)  
`FakeNFTMarketplace` – fixed‑price mock shop  
`CryptoDevsDAO` – proposals, voting & ETH treasury |
| **Frontend** | Next .js 14 · Tailwind CSS · `ethers` v6 (no wagmi) |
| **UX** | Native MetaMask connect, live on‑chain data, responsive dark UI |
| **Tooling** | Foundry (compile + deploy), Vercel (CI/CD) |

---

## 🏗️ Architecture

```mermaid
graph TD
  subgraph On‑chain
    A(CryptoDevsNFT) -->|1 NFT = 1 vote| C[CryptoDevsDAO]
    B(FakeNFTMarketplace) -->|purchase()| C
  end
  C -->|executeProposal| B
  D(User wallet) -->|vote / propose| C
  D -->|mint| A
```

---

## ⚙️ Tech stack

* **Solidity 0.8.x** + OpenZeppelin Contracts
* **Foundry** for testing & deployment
* **Next .js 14** (App Router)
* **Tailwind CSS** for styling
* **ethers v6** for RPC interactions
* **Vercel** for hosting

---

## 🚀 Quick start

### 1 — Clone & install

```bash
git clone https://github.com/YOUR_HANDLE/cryptodevs-dao.git
cd cryptodevs-dao
```

### 2 — Contracts (Foundry)

```bash
cd foundry
cp .env.example .env   # fill PRIVATE_KEY, RPC_URL, ETHERSCAN_API_KEY

forge test             # run tests

# deploy on Sepolia
forge script script/Deploy.s.sol:Deploy --broadcast --verify -vvvv \
  --rpc-url $RPC_URL --private-key $PRIVATE_KEY
```

Save the three printed addresses (NFT, Marketplace, DAO).

### 3 — Frontend

```bash
cd ../frontend
npm i

cp src/constants/index.example.js src/constants/index.js   # paste addresses & ABIs
npm run dev   # http://localhost:3000
```

---

## 📂 Project structure

```
cryptodevs-dao/
├─ foundry/               # Solidity contracts & scripts
│  ├─ src/
│  ├─ script/
│  └─ test/
├─ frontend/              # Next.js dashboard
│  ├─ src/
│  └─ public/
└─ README.md
```

---

## 🔐 .env template (foundry)

```dotenv
PRIVATE_KEY="0x…"
RPC_URL="https://sepolia.infura.io/v3/…"
ETHERSCAN_API_KEY="…"
```

---

## 📝 License

MIT © 2025 CryptoDevs DAO contributors

