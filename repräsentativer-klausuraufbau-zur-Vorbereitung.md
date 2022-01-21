# In Etwa Repräsentativer Klausuraufbau

## Grundlagen zur Blockchaintechnologie

### Distributed Ledgers / Verteilte Logbücher
Unter welchen Umständen ist die Nutzung von verteilten Logbüchern im Vergleich zu zentral verwalteten Logbüchern aus Ihrer Sicht empfehlenswert?

Was ist für Sie das revolutionär Neue an der Blockchaintechnologie?

Inwiefern können wir eine Blockchain als öffentliche, verteilte Datenbank betrachten?

Inwiefern ermöglicht die Blockchain Technologie Peer 2 Peer Geschäfte ohne zentralisierte Mittelsmänner / Institutionen?


### Einwegfunktionen

Welche Einwegfunktion spielt im Bitcoin System eine wesentliche Rolle bzw. zwei wesentliche Rollen? Bitte erläutern Sie dies.

Bitte nennen Sie 3 Bedingungen, die erfüllt sein müssen, damit eine Hashfunktion aktuell als kryptographisch sicher gilt.


### Asynchrone Verschlüsselung / Public Key Verschlüsselung 
1. Digitale Signaturen (Authentizität)   
2. Verschlüsselung an sich (Privacy)  

Bitte beschreiben Sie ein Szenario welches typisch ist für die Kombination aus 1 & 2 im Detail.

Inwiefern spielen digitale Signaturen bei Cryptowährungen wie Bitcoin & Ether eine wesentliche Rolle?  

Beschreiben Sie ein Szenario, in welchem Alice an Bob eine vertrauliche Nachricht senden möchte und Bob sicher sein möchte, dass die Nachricht tatsächlich von Alice kommt. Hilfestellung: Was wird wann mit welchem Key verschlüsselt / entschlüsselt? 


### Datenstrukturen 
#### Bloomfilter


Angenommen Sie nutzen einen Bloomfilter mit einem Bitset der Länge 11 mit den Bloombits 0 bis 10 sowie den folgenden Einwegfunktionen zur Belegung der Bits:  
h(1)=(x * 2)%11  
h(2)=(x * 3)%11  
h(3)=(x * 4)%11  

Wie sieht das Bitset jeweils nach dem Hinzufügen der folgenden Zahlen aus?  
const exampleArray = [2, 5, 6]

--> Bitset nach dem Hinzufügen der 2:   

--> Bitset nach dem Hinzufügen der 5:  

--> Bitset nach dem Hinzufügen der 6:   

Würde der Bloomfilter für die folgenden Zahlen false positives liefern?  
const entriesToBeValidated = [3, 34]  

Lösungscheck siehe Unit Test des bloomfilter moduls

Welche Vor- und Nachteile hat die Erhöhung der Anzahl an Bits im Bitset & welche Vor- und Nachteile hat die Erhöhung der Anzahl an genutzten Hash Funktionen bei Bloomfilters im Allgemeinen. Warum ist das so?  
(https://hur.st/bloomfilter/?n=100000&p=0.6&m=&k=1)

Bitte erläutern Sie mindestens einen Anwendungsfall von Bloomfilters.    


#### Merkletrees
Bitte erstellen Sie einen Merkletree für die Einträge im untenstehenden Beispiel Array unter Nutzung der darunter stehenden Einwegfunktion:   
const exampleArray = [2,7,8,1]  
h(x)=(x * 2)%10  

h(leafNode1)=  
h(leafNode2)=  
h(leafNode3)=  
h(leafNode4)=  

h(lN12)=  
h(lN34)=  
 
h(root)=  
  
Angenommen jemand behauptet im Beispielarray wäre eine 9 (anstelle der 1) enthalten. Welche Nodes innerhalb des MerkleTrees würden sich dadurch wie ändern?
Lösungscheck siehe merkletrees deno modul.

Bitte erläutern Sie mindestens einen Anwendungsfall von Merkletrees.   

Wie werden Merkle Trees im Kontext von Kryptowährungen eingesetzt?


#### Tries
https://deno.land/x/tries   

Bitte skizzieren Sie einen klassischen Trie sowie einen PATRICIA Trie für die folgenden Buchstabensequenzen: 
ape, apple, organ, organism


<img width="1344" alt="Screenshot 2022-01-20 at 21 46 51" src="https://user-images.githubusercontent.com/43786652/150440646-71d5f137-ab8e-4d42-905d-3dff469827b2.png">



### Konsensalgorithmen 

Bitte erläutern Sie die Notwendigkeit von Konsensalgorithmen in einem verteilten System wie z.B. der Ethereum Blockchain.  

Was ist das Kernprinzip hinter Proof of Work?  

Was ist das Kernprinzip hinter Proof of Stake?  

Bitte erläutern Sie wie ein "51% Angriff" auf die Bitcoin Blockchain gestaltet werden könnte und wie ein potentieller Angreifer davon beispielsweise profitieren könnte. 

Was ist eine 51%-Attacke und wie unterscheiden sie sich bei unterschiedlichen Blockchain-Technologien (PoW, PoS)?
Musterlösungen laut Kommilitonen: https://github.com/michael-spengler/digitale-waehrungen-wwi19seb/pull/14/files - bitte stets kritisch prüfen. 

Jemand behauptet dass die Ethereum Blockchain eine Stromverschwendung darstellt und viele der Anwendungen lieber zentral auf einem Server laufen sollten, um Strom zu sparen. Was sagen Sie?


## Anwendungsgebiete der Blockchaintechnologie
### Digitale Währungen 
Was sind für Sie die Hauptunterschiede zwischen einer Central Bank Digital Currency und einer Cryptowährung wie Ether? Was halten Sie von der potentiellen Einführung von Central Bank Digital Currencies? (ca. 7 Sätze)

Was halten Sie davon, dass Richard Nixon 1971 den Goldstandard aufgehoben hat? Warum?   

Der folgende SC soll eine Währung namens QuinoaCoin mit den folgenden Eigenschafte definieren:  
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

Hat eine Währung wie Bitcoin mit einem fixed / max. supply von 21.000.000 aus Ihrer Sicht eher eine inflationäre oder eine deflationäre Tendenz. Bitte erläutern Sie kurz ihre Einschätzung.

Inwiefern könnte der Zeitraum der Veröffentlichung des Bitcoin Whitepapers (31.10.2008 in einer Kryptographie-Mailingliste der Cypherpunks) und der Zeitraum der globalen Finanzkrise 2008 miteinander zusammenhängen?


### Decentralized Finance
Stichworte: Smart Contract based Lending, Borrowing, Yield Farming, Zahlungsverkehr, Investing
Was verstehen Sie unter dem Begriff DeFi? Wie wahrscheinlich ist es aus Ihrer Sicht, dass dieser Ansatz insgesamt an Bedeutung gewinnt? Warum?

### Decentralized Governance 
Stichwort: DAO  
Votingpower hängt z.B. von der Anzahl der gesammelten governance tokens ab... 
https://github.com/distributed-ledger-technology/airdrop

### Decentralized Web
Permanent Deployment / Censorship resistant deployment
Distributed Deployments / File Servers --> IPFS & DDNS- see https://ens.domains  

Beschreiben Sie ein Szenario, in welchem Sie eine dApp anstelle einer klassischen web app implementieren würden.

Welche Browserextension können Sie z.B. für google chrome nutzen, damit Besucher Ihrer dApp mit Smart Constracts der Ethereum Blockchain interagieren können? Bitte nennen Sie eine alternative zu dieser Browserextension.


### Kunst / Collectibles / GamingAssets - Non Fungible (ERC721) & Semi Fungible (ERC1155) Tokens 

## Smart Contracts
Bitte beschreiben Sie das Wesen eines Smart Contracts. Inwiefern kann ein Smart Contract als smarte Vereinbarung bezeichnet werden?

## Wallets
Vergleichen Sie Custodial Wallets vs. Non-Custodial Wallets und nenne Sie dabei mindestens ein Beispiel für ein non-custodial wallet.

Vergleichen Sie Paperwallets und Browserwallets? In welchem der beiden würden Sie eher eine sehr große Summe an Ether speichern? Warum?

## Stable Coins
Was verstehen Sie unter einem Stable Coin? Auf welche Arten können Stable Coins implementiert werden? Kennen Sie Beispiele?


## Exchanges / Börsen
Was sind für Sie Unterschiede zwischen zentralen Exchanges (e.b. binance.com, coinbase.com etc.) und dezentralen Exchanges (e.g. uniswap.org)? 

## On-Chain / Off-Chain Verbindungen
Example: https://deno.land/x/airdrop@v0.1.0/example-airdrops/launch-airdrop-for-wwi19seb.ts ... via TypeScript programm
Application Binary Interfaces Usage Example: https://deno.land/x/airdrop@v0.1.0/src/airdrop-service.ts#L16 ... um eine Repräsentation des Smart Contracts (der z.B. auf der Ethereum Blockchain deployed ist) im TypeScript Programm zu erhalten und damit Funktionen dieses Smart Contracts vom TypeScript Programm aus zu triggern.

## Mining
Wofür steht die Abkürzung "ASIC" im Bezug auf Mininghardware?  
[ ] Application Specific Integrated Circuit  
[ ] Asset Specific Integrated Circuit   
[ ] Altcoin Specific Integrated Circuit  
[ ] Application Specific Initial Coin  

## Airdrops
Warum werden AirDrops durchgeführt? (Multiple Choice)
- [x] Early Adopters belohnen
- [x] Voting Power verteilen
- [ ] Währung deployen
- [ ] Denial of Service Angriffe durchführen


## Layer 2 Scaling
Inwiefern könnte Arbitrum die Adoption der Ethereum Technologie beschleunigen?   


### Implementierungen
#### TypeScript
https://deno.land/x/airdrop@v0.1.0/example-abis/ropsten-0x7910f84868488da3377833ccaa0e5b2b42edd9a6.ts


Welche Informationen und Module benötigen Sie wenn Sie einen Airdrop für Ihre Early Adopters gestalten möchten, welchen Sie über ein TypeScript Programm lancieren?

1. Empfänger Wallet Adressen
2. ABI
3. https://deno.land/x/web3
4. provider url (e.g. von infura.io oder zu einer eigenen Ethereum node,...)



## Eigeninitiative / Eigeninteresse
Describe you own favorite topic wrt. the Blockchain space (4 Punkte)    








