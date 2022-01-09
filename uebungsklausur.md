
# Digitale Währungen Übungsklausur (60 Punkte)

## 1. Praktischer Teil (30 Punkte)
### 1.1 Bitte vervollständigen Sie den folgenden Smart Contract so dass dieser eine Währung mit den folgenden Eigenschaften auf der Ethereum Blockchain definiert (5 Punkte):  
a) Fixed Supply von 1.000.000 Tokens  
b) 18 Nachkommastellen  
c) Name der Währung: MannheimCoin  
d) Abkürzung der Währung: MC  

```sol
// SPDX-License-Identifier: MIT
pragma solidity >=0.8.0 < 0.9.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v4.4/contracts/token/ERC20/ERC20.sol";

// ...

```

### 1.2 Bitte beschreiben Sie den Prozess, der nach dieser Implementierung notwendig ist, um diese Währung auf der Ethereum Blockchain zu "deployen" (5 Punkte).

### 1.3 Bitte vervollständigen Sie den folgenden TypeScript (Backend) Programmcode so dass dieser alle 10 Minuten 1 Token Ihrer neuen Währung an 0xa59a1e45a880504fc8a4D947702AaB6067DFEa71 sendet bis nur noch 500.000 Tokens im Senderwallet verfügbar sind (5 Punkte).

```ts
... to be done ...
```

### 1.4 Bitte vervollständigen Sie den folgenden TypeScript (Frontend) Programmcode so, dass dieser beim klick auf den transfer button das metamask Browserwallet öffnet, um dem User die digitale Signatur und damit das Absenden der Transaktion zu ermöglichen (5 Punkte).

```ts
... to be done ...
```

### 1.5 Bitte vervollständigen Sie den folgenden TypeScript so, dass dieser einen Liquidationbot für das Aave Protokol definiert (5 Punkte).
```ts
... to be done ...
```

### 1.6 Bitte fügen Sie im folgenden Solidity Code Kommentare ein, welche genau beschreiben warum die einzelnen Schritte durchgeführt werden (5 Punkte).
```sol

// SPDX-License-Identifier: MIT
pragma solidity >=0.8.0 <0.9.0;

contract MerkleProof {
    function verify(
        bytes32[] memory proof,
        bytes32 root,
        bytes32 leaf,
        uint256 index
    ) public pure returns (bool) {
        bytes32 hash = leaf;

        for (uint256 i = 0; i < proof.length; i++) {
            bytes32 proofElement = proof[i];

            if (index % 2 == 0) {
                hash = keccak256(abi.encodePacked(hash, proofElement));
            } else {
                hash = keccak256(abi.encodePacked(proofElement, hash));
            }

            index = index / 2;
        }

        return hash == root;
    }
}


// SPDX-License-Identifier: MIT
pragma solidity >=0.8.0 <0.9.0;

import "./merkle-proof.sol";

contract TestMerkleProof is MerkleProof {
    bytes32[] public hashes;

    constructor() {
        string[4] memory transactions = [
            "alice -> bob",
            "bob -> dave",
            "carol -> alice",
            "dave -> bob"
        ];

        for (uint256 i = 0; i < transactions.length; i++) {
            hashes.push(keccak256(abi.encodePacked(transactions[i])));
        }

        uint256 n = transactions.length;
        uint256 offset = 0;

        while (n > 0) {
            for (uint256 i = 0; i < n - 1; i += 2) {
                hashes.push(
                    keccak256(
                        abi.encodePacked(
                            hashes[offset + i],
                            hashes[offset + i + 1]
                        )
                    )
                );
            }
            offset += n;
            n = n / 2;
        }
    }

    function getRoot() public view returns (bytes32) {
        return hashes[hashes.length - 1];
    }

}
```


## 2. Theoretischer Teil (30 Punkte)

### 2.1 Angenommen niemand interessiert sich für die von Ihnen unter 1.1 bereitgestellte Währung. Inwiefern könnte sich dies durch die Definition eines Liquidity Pools für Ihre Währung bei Uniswap ändern (3 Punkte)?

### 2.2 Wie würden Sie den in 1.3 angesprochenen Liquiditypool gestalten (2 Punkte)?

### 2.3 Woraus ergeben Sich aus Ihrer Sicht Unterschiede im Hinblick auf die Capital Efficiency zwischen dem CeFi und dem DeFi system (2 Punkte)?

### 2.4 Bitte stellen Sie Cryptowährungen wie Ether und CBDCs (als Fiat Money) gegenüber und erläutern Sie jeweils deren Mehrwert und potentielle Risiken (3 Punkte)?

### 2.5 Bitte erläutern Sie in welchen Situationen die Nutzung von Bloomfilters sinnvoll sein kann (2 Punkte).

### 2.6 Bitte erläutern Sie in welchen Situationen die Nutzung von Merkletrees sinnvoll sein kann (2 Punkte).

### 2.7 Bitte erläutern Sie welche Rolle Einwegfunktionen im Kontext des Bitcoin Systems spielen (2 Punkte).

### 2.8 Bitte erläutern Sie welche Rolle Digitale Signaturen im Kontext des Bitcoin Systems spielen (2 Punkte).

### 2.9 Angenommen Sie möchten eine censorship resistant web app bereitstellen. Wie gehen Sie vor (2 Punkte)?

### 2.10 Bitte beschreiben Sie die aus Ihrer Sicht vielversprechendsten DeFi Protokolle und gehen Sie dabei besonders darauf ein weshalb Ihnen gerade diese vielversprechend erscheinen (2 Punkte).

### 2.11 Wozu dienen Chaninlink basierte Oracles (2 Punkte)?

### 2.12 Bitte erläutern Sie inwiefern ein Airdrop hilfreich sein kann um eine faire Verteilung von Governance Tokens zu initiieren (2 Punkte). 

### 2.13 Bitte stellen Sie eine DAO einer klassischen Rechtsform wie z.B. einer Aktiengesellschaft gegenüber (2 Punkte).

### 2.14 Inwiefern wäre das von der BaFin ausgesprochene Verbot des Shortsellings von Wirecard Aktien in der Blockchain Welt schwer umsetzbar / kontrollierbar gewesen? Welche Rolle könnten Protokolle wie synthetix.io und tornado.cash in solchen Kontexten spielen? (2 Punkte)


