
# Ref

Voting Application using Smart Contract
https://nhancv.medium.com/voting-application-using-smart-contract-185e16dbfa35

Issue your ERC20 token with Solidity on Ethereum Blockchain
https://nhancv.medium.com/issue-your-token-with-solidity-on-ethereum-blockchain-6e640eb613ff

SmartContract ICO Crowdsale simple
https://nhancv.medium.com/smartcontract-ico-crowdsale-simple-35dc5ff02459

Example
https://github.com/nhancv/nc-blockchain-netday

ERC20 & TRC20 Token template
https://gist.github.com/nhancv/58997e9a6e7f896627339d122e5671bf

Remix online IDE
https://remix.ethereum.org/#optimize=true&runs=200&evmVersion=null&version=soljson-v0.8.3+commit.8d00100c.js

# Install 

TRUFFLE CLI
```
npm install truffle -g
```

GANACHE

https://www.trufflesuite.com/ganache

# Structure

```
mkdir truffle && cd truffle
mkdir frontend // <-- frontend application
mkdir smartcontracts && cd smartcontracts
npm init -y
npm install truffle-hdwallet-provider --save
npm install bip39 dotenv --save
npm install @openzeppelin/contracts --save
truffle init
```

## Build and Deploy Contract
```
# Setup local Blockchain
Install Ganache
Open Ganache -> New workspace -> Add Project -> Point to truffle/smartcontracts/truffle-config.js -> Save

# Prepare wallet
cd truffle/smartcontracts
cp .env.example .env
Copy MNEMONIC generated by Ganache ACCOUNTS and paste to MNEMONIC value in .env created previous step

# Compile only 
truffle compile

# Or Compile and deploy contract to local test
truffle migrate

# Check success output
Compiling your contracts...
===========================
> Compiling ./contracts/CryptoLott.sol
> Compiling ./contracts/Migrations.sol
> Artifacts written to ../truffle/frontend/src/Contract/abi
> Compiled successfully using:
   - solc: 0.5.16+commit.9c3226ce.Emscripten.clang



Starting migrations...
======================
> Network name:    'development'
> Network id:      5777
> Block gas limit: 6721975 (0x6691b7)


1_initial_migration.js
======================

   Replacing 'Migrations'
   ----------------------
   > transaction hash:    0x5285171ea479d985aa5086f26b37060012ba408ec852d555b2556fc34420c7b8
   > Blocks: 0            Seconds: 0
   > contract address:    0x55DBfe6239AAC6b9927fe9c37166C87F943e787e
   > block number:        1
   > block timestamp:     1616777661
   > account:             0x6918C8D2a75abfA5Afca786EFAF60BefDBDD8d24
   > balance:             99.99616114
   > gas used:            191943 (0x2edc7)
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.00383886 ETH


   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.00383886 ETH


2_deploy_contracts.js
=====================

   Replacing 'CryptoLott'
   ----------------------
   > transaction hash:    0x6501e8edec15ba4d15dc3ad78e8a5458e6d1f07cb4923747ff273e2b5597d0bf
   > Blocks: 0            Seconds: 0
   > contract address:    0x716103d7CfC4D353Ba1a9a1D6D06bE1C0F803275
   > block number:        3
   > block timestamp:     1616777661
   > account:             0x6918C8D2a75abfA5Afca786EFAF60BefDBDD8d24
   > balance:             99.94754624
   > gas used:            2388407 (0x2471b7)
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.04776814 ETH


   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.04776814 ETH


Summary
=======
> Total deployments:   2
> Final cost:          0.051607 ETH

# Validate
Check on Ganache in Blocks, Transactions, Contracts, Events, Logs, ...
```


## Intergrate contract with Frontend React App
```
## Prerequisite
- Node: 8.16.0
- Npm: 6.4.1
- Web3: 1.0.0-beta.33

## Install Metamask Extension and Unlock
https://metamask.io/

Open Metamask -> Switch network -> Custom RPC -> (fill local Blockchain network info)
Network name: Localhost 7545
New RPC URL: http://127.0.0.1:7545
Chain ID: 1337

## Updated built contract data to frontend
Copy contract address deployed in previous step
> contract address:    0x716103d7CfC4D353Ba1a9a1D6D06bE1C0F803275

Update new contract address to `truffle/frontend/src/Contract/CryptoLottContract.ts` at `initContract` method

## Build Frontend
cd truffle/frontend
npm install --legacy-peer-deps
npm start

Go to: http://localhost:3000/

```

------
# BONUS: Deploy TRON TOKEN

Create TRC10 Token on TRON network with nodejs
https://nhancv.medium.com/create-trc10-token-on-tron-network-with-nodejs-9970116d5284

Create TRC20 Token on TRON network with nodejs
https://nhancv.medium.com/create-trc20-token-on-tron-network-with-nodejs-5eb2b6115a4f

-----
# Create Testing Solidity token: 

- Install Metamask
- The ETH wallets generated automatically


## Ropsten ETH Token

- Open Metamask -> Switch env to `Ropsten Test Network`
```
Network Name: Ropsten Test Network
New RPC URL: https://ropsten.infura.io/v3/undefined
Chain ID: 3
Currency Symbol (optional): ETH
Block Explorer URL (optional): https://ropsten.etherscan.io
```
- Get some ETH coin to deploy smart contract: https://faucet.ropsten.be/
- Access: https://remix.ethereum.org/#optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.1+commit.df193b15.js
    + Create contracts/ERC20Token.sol
    + Fill `ERC20Token.sol` with source code at: [./truffle/smartcontracts/contracts/ERC20Token.sol](./truffle/smartcontracts/contracts/ERC20Token.sol)
    + Modify `ERC20Token.sol` to your token info
    + Compile tab: Compile `ERC20Token.sol`
    + Deploy tab: Select Environment -> Injected Web3 -> Select Contract `your contract class name` -> Deploy

## Binance Smart Chain BEP20 Token

https://academy.binance.com/en/articles/connecting-metamask-to-binance-smart-chain

- Open Metamask -> Custom RPC

```
# Testnet
Network Name: Binance Smart Chain - Testnet
New RPC URL: https://data-seed-prebsc-1-s1.binance.org:8545/
ChainID: 97
Symbol: BNB
Block Explorer URL: https://testnet.bscscan.com

# Mainnet
Network Name: Binance Smart Chain
New RPC URL: https://bsc-dataseed.binance.org/
ChainID: 56
Symbol: BNB
Block Explorer URL: https://bscscan.com
```
- Get some BNB coin to deploy smart contract: https://testnet.binance.org/faucet-smart
- Access: https://remix.ethereum.org and do the same with Ropsten ETH Token


## Avalanche (AVAX) Chain Token

https://docs.avax.network/build/tutorials/smart-contracts/deploy-a-smart-contract-on-avalanche-using-remix-and-metamask

- Open Metamask -> Custom RPC

```
# FUJI Testnet Settings
Network Name: Avalanche FUJI C-Chain
New RPC URL: https://api.avax-test.network/ext/bc/C/rpc
ChainID: 0xa869
Symbol: AVAX
Explorer: https://cchain.explorer.avax-test.network

# Avalanche Mainnet Settings
Network Name: Avalanche Mainnet C-Chain
New RPC URL: https://api.avax.network/ext/bc/C/rpc
ChainID: 0xa86a
Symbol: AVAX
Explorer: https://cchain.explorer.avax.network/
```
- AVAX address info: 

> AVAX tokens exist on the X-Chain, where they can be traded, on the P-Chain, where they can be provided as a stake when validating the Primary Network, and on the C-Chain, where they can be used in smart contracts or to pay for gas. In this tutorial, we’ll send AVAX tokens between the X-Chain and C-Chain.

- Get some AVAX coin to deploy smart contract: https://faucet.avax-test.network/

```
- Copy ETH address generated by Metamask -> Now this address will be C-Chain AVAX address
- Access https://wallet.avax.network/ -> Switch env to Fuji network
- Import wallet with private key of above C-Chain AVAX address
- Now you can see, we have 3 wallet address types with 3 address: 
    + Available (X) = 0 (X-fuji1hjfdc8hsqtfju27lzfn8zyztlrdr9220ucura6)
    + Available (P) = 0 (P-fuji1hjfdc8hsqtfju27lzfn8zyztlrdr9220ucura6)
    + Available (C) = 0 (0xfd0c67edd5e4ce03cd8397dc748b19b0a5c0f645 <- reused eth address in Metamask)
- Access https://faucet.avax-test.network/ -> fill specific address to get test coin
- You can move you coin from X-Chain to C-Chain and vice versa with 'Cross Chain' at https://wallet.avax.network/wallet/cross_chain 
```

- Access: https://remix.ethereum.org and do the same with Ropsten ETH Token

