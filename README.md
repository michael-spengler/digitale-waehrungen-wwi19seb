# Digitale Währungen WWI19SEB

## 10.12.2021:
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

### Bitcoin basics & Proof of Work
[Bitcoin basics & PoW](https://www.youtube.com/watch?v=bBC-nXj3Ng4)   

### Seedphrases
[BIP39 Seedphrases](https://github.com/danfinlay/mnemonic-account-generator)  

### Liquidity Pools  
Using uniswap.org as decentralized exchange  


### Klausurfragen Sammlung

