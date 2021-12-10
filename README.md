# Digitale Währungen WWI19SEB

## 26.11.21
### Brainstorming
Todo Spengler Infos vom Chat hierher / Mindmap übertragen

### Wallets
#### Browser Wallets
brave.com 
metamask.io

Per default connected dieses auf die Ethereum Blockchain. Wir nutzen - um Gas Fees zu sparen - die Layer 2 Scaling Solution Arbitrum oder das Ropsten Testnet:

![Screenshot 2021-11-26 at 11 12 33](https://user-images.githubusercontent.com/43786652/143564681-e2531e37-8c48-410c-829c-54be46d48d1f.png)


#### Paper Wallets
recommended for big money

#### Hardware Wallets
e.g. ledger nano s / trezor etc.


### Stichwortsammlung
Wallets   
Double Spending   
SHA256 Hash   
Konsensalgorithmen    
Proof of Work / Proof of Stake    
https://ethereum.stackexchange.com/  
Smart Contracts = Programme auf einer Blockchain z.B. auf der Ethereum Blockchain    
Solidity = Programmiersprache für Smart Contracts auf der Ethereum Blockchain   
remix.ethereum.org (Online IDE zur Entwicklung, Test & Deployment von Smart Contracts)   
ERC20 Währungen  
ERC721 NFT (unique collictables)   
Web1 (static html pages mit links - internet in den 90 ern)  
Web2 (dynamic pages mit javascript (Brendan Eich))  
Web3 (decentralized web)  
https://coinmarketcap.com/  

### Exkurs Gas Fees
Gas Fees kommen typischerweise bei Ethereum zustande für: 1. Konsensfindung 2. Storage 3. CPU für EVM Smart Contract Executions
Sidechain (Polygon) 
Layer 2 Scaling vs. Sidechains
Arbitrum nutzt zk proofs / rollups um die Vertrauenswürdigkeit / Immutability hochzuhalten ohne die Notwendigkeit die o.g. 3 Punkte auf jeder Node zu executen.



## Open Source Implementierungen 
https://deno.land/x/merkletrees



## 10.12.2021
### Quoinoa Coin on Ropsten Testnet
1. get some test ether via https://faucet.ropsten.be/
2. go to remix.ethereum.org
3. add the following solidity code
```sol
// SPDX-License-Identifier: MIT
pragma solidity >=0.8.0 < 0.9.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v4.4/contracts/token/ERC20/ERC20.sol";

contract QuoinoaCoin is ERC20 { 
    
    constructor () ERC20("Quoinoa", "QNA") { 
        _mint(msg.sender, 280000 * (18 ** uint256(decimals())));
    }
    
}
```
4. deploy this smart contract while being connected to the ropsten testnet
5. check the deployed contract - e.g. https://ropsten.etherscan.io/address/0x0cd57ce21d19b9af6f1b9efda419b17b71e49460


### Programmatische Interaktion mit der Ethereum Blockchain
#### Solidity (on chain)
siehe oben - z.B. Smart Contract for QuoinoaCoin...

#### TypeScript (off chain <-> on chain interaction)
```ts 
require('dotenv').config() // this ensures process.env. ... contains your .env file configuration values

const { DeFiService } = require("decentralized-finance-defi")

const fromWalletAddress = process.env.SENDER_WALLET_ADDRESS
const amountOfQNToBeTransferred = 100000
const amountOfEtherToBeTransferredForPayingGasFees = 0.01
const senderPrivateKey = process.env.SENDER_WALLET_PRIVATE_KEY

const recipients = [
    "0x1513D4cCaC767d9510947cd8A0411b3A8E2c31AF",
    "0x944Cd9E2a19C84FA3DfbcFF7F0cbDAC5d335406c",
    "0x5ebde6A2B67274847F8B509B5e51adb0F1c17515",
    "0xF3BC6baD1F682e45D150E93e0446e1C05444BE0A",
    "0x7Ea947Cd95B262ee405634e9F745e144926b9Dc6",
    "0xBC789270f670b86cf438f722A7Ef8F4F87663053",
    "0xBc51b93F958763E6B3A765bF5165a4181CdE6679",
    "0x48568970C24a9eDD4C774C1d896719ba39F03117",
    "0xC0A243687218f11fF1B515c45697c7c459F1Bf75",
    "0x230144D7E750ec1bbCCa3b22fE993457C8d52e5B",
    "0xB5f5Ebf222Fa2Ae3Ca827E24BEFa7eB50Bf8a10F",
    "0x251D21e03E49174960F3230bDA31B83aaCB26969",
    "0xF9E854E7c18f0CE7c2f0EE994F4A8a0ff7157562",
    "0x7e5c8d73b1a5caF1F7Fe31DAbA41b8D310CC25Be",
    "0xF3BC6baD1F682e45D150E93e0446e1C05444BE0A",
    "0xDcDf541545F4A8E5FD6A996E911246A4267A9D51",
    "0x8CAc96dfe186231fa965193FE2537296bA79FCF6",
    "0xa6306C28AF7aaB9E052faAFB27CBa729811EbcA0",
    "0x20a156521EEC90eafAE8Ed1342dB4d9f8E270B21",
    "0x3B98f143f7b521646DF42A847F9d0cAE2C299eF7",
    "0xFC0Cc4e4E913cd95c3980F2ec2Cb72287aaedaCD",
    "0x96FD355847401D77c6F00be4663DAC5C47eeE94E",
    "0xa572f251DDF9E56F6217CF1c337b245B004F7fB3",
    "0xD0E879Dd9F37aD2db610D424Af4450c69001c0ba",
    "0x35B00640dF68489856c94c618A0F9fE7db383250",
]

setTimeout(async () => {

    // for (const recipient of recipients) {

    await transferEthersToHappyStudent(recipients[0])

    // await transferQNsToHappyStudent(recipients[0])
    // }

}, 1)

async function transferEthersToHappyStudent(recipient: string) {
    console.log(`transferring ${amountOfEtherToBeTransferredForPayingGasFees} Ether from ${fromWalletAddress} to ${recipient} using pk ${senderPrivateKey}`)
    await DeFiService.transferEther(fromWalletAddress, recipient, amountOfEtherToBeTransferredForPayingGasFees, senderPrivateKey)
}

async function transferQNsToHappyStudent(recipient: string) {
    console.log(`transferring ${amountOfQNToBeTransferred} QN from ${fromWalletAddress} to ${recipient}`)

    throw new Error("to be implemented")
}


```


### Bitcoin basics & Proof of Work
[Bitcoin basics & PoW](https://www.youtube.com/watch?v=bBC-nXj3Ng4)   

### Seedphrases
[BIP39 Seedphrases](https://github.com/danfinlay/mnemonic-account-generator)  

### Liquidity Pools  
Using uniswap.org as decentralized exchange  

### Zapper.FI
https://zapper.fi/  

We can enhance this approach by adding a feature to paste a seedphrase and get the overall Ether value on all potentially connected accounts  


### Klausurfragen Sammlung

