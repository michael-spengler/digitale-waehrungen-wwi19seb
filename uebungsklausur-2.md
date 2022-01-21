# Übungsklausur 2 - Under Construction

## Grundlagen zur Blockchaintechnologie

### Distributed Ledgers / Verteilte Logbücher
Unter welchen Umständen ist die Nutzung von verteilten Logbüchern im Vergleich zu zentral verwalteten Logbüchern aus Ihrer Sicht empfehlenswert?

### Einwegfunktionen
https://deno.land/x/hash

Welche Einwegfunktion spielt im Bitcoin System eine wesentliche Rolle bzw. zwei wesentliche Rollen? Bitte erläutern Sie dies.

### Asynchrone Verschlüsselung / Public Key Verschlüsselung 
1. Digitale Signaturen (Authentizität)   
2. Verschlüsselung an sich (Privacy)  

Bitte beschreiben Sie ein Szenario welches typisch ist für die Kombination aus 1 & 2 im Detail.

Inwiefern spielen digitale Signaturen bei Cryptowährungen wie Bitcoin & Ether eine wesentliche Rolle?  

### Datenstrukturen 
#### Bloomfilter
https://deno.land/x/bloomfilter  

Bitte erläutern Sie mindestens einen Anwendungsfall von Bloomfilters.    

Welche Vor- und Nachteile hat die Erhöhung der Anzahl an Bits im Bitset & welche Vor- und Nachteile hat die Erhöhung der Anzahl an genutzten Hash Funktionen bei Bloomfilters im Allgemeinen. Warum ist das so?  
(https://hur.st/bloomfilter/?n=100000&p=0.6&m=&k=1)

Welchen Output erwarten Sie bei der Ausführung des folgenden Codes?

```ts
import { BloomFilter } from "https://deno.land/x/bloomfilter/mod.ts"

const numberOfExpectedItemsInArray = 10000
const falsePositiveRate = 0.1 // 10 percent

const numberOfBitsInBitset = BloomFilter.getOptimalNumberOfBits(numberOfExpectedItemsInArray, falsePositiveRate)
const numberOfHashFunctions = BloomFilter.getOptimalNumberOfHashFunctions(numberOfBitsInBitset, numberOfExpectedItemsInArray))

const bloomFilter = new BloomFilter(numberOfBitsInBitset, numberOfHashFunctions)

const testArray = ["dog", "chicken", "cat"]

for (const entry of testArray) {
    bloomFilter.add(entry)
}

let actualTestResult = bloomFilter.test("horse")
console.log(actualTestResult) 

actualTestResult = bloomFilter.test("cat")
console.log(actualTestResult)
```

Angenommen Sie nutzen einen Bloomfilter mit einem Bitset der Länge 10 mit den Bloombits 0 bis 9 sowie den folgenden Einwegfunktionen zur Belegung der Bits:  
h(1)=(x * 2)%10  
h(2)=(x * 3)%10  
h(3)=(x * 4)%10  

Wie sieht das Bitset jeweils nach dem Hinzufügen der folgenden Zahlen aus?  
const exampleArray = [6, 9, 10]

h(1)=12%10=2  
h(2)=18%10=8  
h(3)=24%10=4  
--> Bitset nach dem Hinzufügen der 6: 0010100010  

h(1)=18%10=8  
h(2)=27%10=7  
h(3)=36%10=6  
--> Bitset nach dem Hinzufügen der 9: 0010101110  

h(1)=20%10=0  
h(2)=30%10=0  
h(3)=40%10=0  
--> Bitset nach dem Hinzufügen der 10: 1010101110  

Würde der Bloomfilter für die folgenden Zahlen false positives liefern?  
const entriesToBeValidated = [11, 3]  
h(1)=22%10=2  
h(2)=33%10=3  
h(3)=44%10=4  
Die 11 würde die Positionen 2, 3 und 4 belegen. Das zuvor errechnete Bitset (1010101110) hat an Position 3 eine 0. Daher würde sich aus der Prüfung der 11 kein false Positive ergeben.  

h(1)=6%10=6  
h(2)=9%10=1  
h(3)=12%10=2  
Die 3 würde die Positionen 6, 1 und 2 belegen. Das zuvor errechnete Bitset (1010101110) hat an Position 1 eine 0. Daher würde sich aus der Prüfung der 3 ebenso kein false Positive ergeben.  


#### Merkletrees
https://deno.land/x/merkletrees  
Bitte erstellen Sie einen Merkletree für die Einträge im untenstehenden Beispiel Array unter Nutzung der darunter stehenden Einwegfunktion:   
const exampleArray = [2,4,8,1]  
h(x)=(x * 2)%10  

h(leafNode1)=(2 * 2)%10=4
h(leafNode2)=(4 * 2)%10=8
h(leafNode3)=(8 * 2)%10=6
h(leafNode4)=(1 * 2)%10=2

h(lN12)=(48 * 2)%10=6
h(lN34)=(62 * 2)%10=4

h(root)=(64 * 2)%10=8

Angenommen jemand behauptet im Beispielarray wäre eine 9 (anstelle der 1) enthalten. Welche Nodes innerhalb des MerkleTrees würden sich dadurch wie ändern?

1. h(leafNode4) - wäre dann eine 8
2. h(lN34) - wäre dann (68 * 2) % 10=6
3. h(root) - wäre dann (66 * 2) % 10=2


Bitte erläutern Sie mindestens einen Anwendungsfall von Merkletrees.   


#### Tries
https://deno.land/x/tries   

Bitte skizzieren Sie einen klassischen Trie sowie einen PATRICIA Trie für die folgenden Buchstabensequenzen: 
ape, apple, organ, organism


<img width="1344" alt="Screenshot 2022-01-20 at 21 46 51" src="https://user-images.githubusercontent.com/43786652/150440646-71d5f137-ab8e-4d42-905d-3dff469827b2.png">



### Konsensalgorithmen 

Bitte erläutern Sie die Notwendigkeit von Konsensalgorithmen in einem verteilten System wie z.B. der Ethereum Blockchain.  

Aus welchen Gründen plant Vitalik Buterin & Friends aus Ihrer Sicht den Umstieg von Proof of Work auf Proof of Stake?

Bitte erläutern Sie wie ein "51% Angriff" auf die Bitcoin Blockchain gestaltet werden könnte und wie ein potentieller Angreifer davon beispielsweise profitieren könnte.


## Anwendungsgebiete der Blockchaintechnologie
### Digitale Währungen 
CBDCs vs. Ether

### Decentralized Finance

### Decentralized Governance 
Votingpower hängt z.B. von der Anzahl der gesammelten governance tokens ab... 
https://github.com/distributed-ledger-technology/airdrop

### Decentralized Web
Distributed Deployments & DDNS- see https://ens.domains  

### NFTs - Kunst / Collectibles
```sol
tbd
```

### Implementierungen 
#### TypeScript
https://deno.land/x/web3  
https://deno.land/x/airdrop  

Welche Informationen und Module benötigen Sie wenn Sie einen Airdrop für Ihre Early Adopters gestalten möchten, welchen Sie über ein TypeScript Programm lancieren?

1. Empfänger Wallet Adressen
2. ABI
3. https://deno.land/x/web3
4. provider url (e.g. von infura.io oder zu einer eigenen Ethereum node,...)


```ts
tbd
``` 

#### Solidity
### ERC20 Basics
Ziel: Der folgende SC soll eine Währung namens QuinoaCoin mit den folgenden Eigenschafte definieren:  
1. Nachkommastellen: 18
2. Gesamtzahl an Tokens (fixed supply): 2000000

Bitte streichen Sie fehlerhafte Zeilen und ersetzen Sie diese durch korrekte Anweisungen:   

```sol
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.8.0 < 0.9.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v4.4/contracts/token/ERC20/ERC20.sol";


contract QuinoaCoin is ERC20 { 


    constructor () ERC20("QuinoaCoin", "QNC") { 
    
        
        _mint(msg.sender, 2000*10**17);
    
    
    }
    
}
```


## On-Chain / Off-Chain Verbindungen
Example: https://deno.land/x/airdrop@v0.1.0/example-airdrops/launch-airdrop-for-wwi19seb.ts ... via TypeScript programm
Application Binary Interfaces Usage Example: https://deno.land/x/airdrop@v0.1.0/src/airdrop-service.ts#L16 ... um eine Repräsentation des Smart Contracts (der z.B. auf der Ethereum Blockchain deployed ist) im TypeScript Programm zu erhalten und damit Funktionen dieses Smart Contracts vom TypeScript Programm aus zu triggern.


### Implementierungen
#### TypeScript
https://deno.land/x/airdrop@v0.1.0/example-abis/ropsten-0x7910f84868488da3377833ccaa0e5b2b42edd9a6.ts


#### Solidity


## Eigeninitiative / Eigeninteresse
Describe you own favorite topic wrt. the Blockchain space (4 Punkte)    








