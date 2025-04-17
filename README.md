🐱‍🚀 CryptoDevs DAO – on‑chain, NFT‑gated treasury

A fully on‑chain Decentralized Autonomous Organization where each CryptoDevs NFT equals one governance vote. Members propose purchases of NFTs, vote in real time, and—if a proposal passes—the DAO contract buys the target asset autonomously using treasury ETH.

✨ Features

Layer

Highlights

Smart Contracts

• CryptoDevsNFT – ERC‑721 Enumerable demo collection

• FakeNFTMarketplace – minimal fixed‑price NFT shop used for testing

• CryptoDevsDAO – proposal / voting / execution logic + ETH treasury

Frontend

Next .js 14, React Server Components, Tailwind CSS, ethers v6 (no wagmi)

Wallet UX

Native MetaMask connect; live chain data (balances, deadlines, votes) via JSON‑RPC

Deployment

Foundry for compilation, testing & Sepolia deployment; Vercel for hosting

🏗 Contract Architecture

          +----------------------+
          |  CryptoDevsDAO.sol   |
          |----------------------|
          |  proposals mapping   |
          |  treasury (ETH)      |
          +-----^-----------^----+
                |           |
      vote() / execute()  purchase()
                |           |
+---------------+           +--------------------+
|                                 |
|                         FakeNFTMarketplace.sol
|                         (0.1 ETH fixed price)
|
CryptoDevsNFT.sol  (ERC‑721 – 1 token = 1 vote)

⚙️ Stack

Solidity 0.8.x with OpenZeppelin Contracts

Foundry – forge build & deploy scripts

Next .js 14 (App Router)

Tailwind CSS for styling

ethers v6 – reads, writes & event listening

Vercel – one‑click CI/CD

🚀 Quick start

1 — Clone & install

git clone https://github.com/YOUR_HANDLE/cryptodevs-dao.git
cd cryptodevs-dao

2 — Smart‑contracts

cd foundry
cp .env.example .env   # fill PRIVATE_KEY, RPC_URL, ETHERSCAN_API_KEY

# compile & test
a
forge test

# deploy (Sepolia)
forge script script/Deploy.s.sol:Deploy --broadcast --verify -vvvv \
  --rpc-url $RPC_URL --private-key $PRIVATE_KEY

Save the three addresses printed (CryptoDevsNFT, FakeNFTMarketplace, CryptoDevsDAO).

3 — Frontend

cd ../frontend
npm i

# add constants
cp src/constants/index.example.js src/constants/index.js
# ➜ paste the contract addresses & ABIs

npm run dev   # http://localhost:3000

📂 Project structure

cryptodevs-dao/
├─ foundry/               # Solidity contracts & scripts
│  ├─ src/
│  ├─ script/
│  └─ test/
├─ frontend/              # Next.js + Tailwind dashboard
│  ├─ src/
│  └─ public/
└─ README.md

🔐 .env reference (foundry)

PRIVATE_KEY="0x…"
RPC_URL="https://sepolia.infura.io/v3/…"
ETHERSCAN_API_KEY="…"

🖼 Screenshots

Dashboard

Proposal modal





📝 License

MIT © 2025 CryptoDevs DAO contributors

