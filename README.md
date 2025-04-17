# CryptoDevs DAO

Fully on-chain, NFT-gated DAO where CryptoDevs holders can propose, vote, and execute treasury decisions to purchase NFTs.

## 🧠 What is this?
A decentralized autonomous organization (DAO) that allows any CryptoDevs NFT holder to:

- Create proposals to buy NFTs from a marketplace
- Vote with their NFTs (1 NFT = 1 vote)
- Execute passed proposals automatically using DAO treasury ETH

Everything is on-chain. No multisigs, no off-chain voting.

## 🧩 Tech Stack

### Smart Contracts (Foundry)
- `CryptoDevsNFT.sol` – Simple ERC721Enumerable NFT collection
- `FakeNFTMarketplace.sol` – Simulates NFT purchases with fixed price logic
- `CryptoDevsDAO.sol` – Proposal creation, voting, execution, and treasury control

### Frontend (Next.js + Tailwind CSS + Ethers.js)
- Uses `ethers@6` directly (no wagmi)
- DAO dashboard with live data: proposals, votes, execution buttons
- NFT balance and treasury shown on load
- Fully responsive and dark-themed

## ⚙️ How it works
1. Any holder of a CryptoDevs NFT can create a proposal to buy an NFT from the marketplace.
2. Voting is open for 5 minutes.
3. Each NFT gives one vote. No double voting allowed.
4. If more "YAY" votes than "NAY" by the deadline, the DAO contract auto-purchases the NFT.
5. The DAO treasury is stored in the DAO contract itself. Only proposals or the owner can move ETH.

## 📦 Installation
```bash
# Clone repo
https://github.com/your-username/cryptodevs-dao.git

# Frontend setup
cd frontend
npm install
npm run dev

# Contracts (optional)
cd ../foundry
forge install
forge build
```

## 📄 Contracts
| Name | Address | Network |
|------|---------|---------|
| CryptoDevsNFT | `0x...` | Sepolia |
| FakeNFTMarketplace | `0x...` | Sepolia |
| CryptoDevsDAO | `0x...` | Sepolia |

## 🔗 Etherscan
- [CryptoDevsNFT](https://etherscan.io/address/0x...)
- [FakeNFTMarketplace](https://etherscan.io/address/0x...)
- [CryptoDevsDAO](https://etherscan.io/address/0x...)
