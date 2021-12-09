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

