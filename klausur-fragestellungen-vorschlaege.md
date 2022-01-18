# Klausurfragen

## Worin liegt der Unterschied zwischen Ether und Ethereum?

## Was verstehen Sie unter einem Smart Contract?

## Was sind Liquidity Pools?

## Wie verdient man mit Liquidity Pools Geld?

## Welche Szenarien können dafür sorgen, dass ich als Liquidity Provider 1. Verlust mache 2. anderweitig (durch long term hoddling) mehr verdienen würde?
<z.B. am Beispiel ETH <-> DAI (algorithmic stable coin) erläutern>

## Was sind Opportunitätskosten? 
... sind diejenigen Kosten, die dadurch entstehen, dass ich eine bestimmte Investmentoption NICHT gewählt habe... 

## Wie kann man allgemein im Krypto-Space Geld verdienen?
Yield Farming (ich krieg halt Zinsen dafür dass ich Kohle bereitstelle)  
NFTs erstellen und verkaufen 
Algorithmic Trading

## Was verstehen Sie unter einem Non Fungible Token? Kennen Sie ein template dafür?
... unique ... 
... ERC721 ...

## Was verstehen Sie unter einem Fungible Token? Kennen Sie ein template dafür?
Currencies sind typischerweise als fungible tokens implementiert... austauschbar... 
ERC20

## Programmable Money

## Exchanges
### Decentralized Exchanges
z.B. Uniswap

### Centralized Exchanges
Coinbase
Binance.com 
Bybit

## Warum sind diese Pools wichtig für den Erfolg einer Währung?

## Worin liegen die Unterschiede zwischen Web 1, Web 2, Web 3? 

## Was sind Gasfees und warum sind diese nötig?

## Was halten Sie von der potentiellen Einführung von Central Bank Digital Currencies?
Vorteile:
Kostensenkung für Einzelpersonen
Komfortsteigerung für Einzelpersonen
Transparenz zur Vermeidung von Geldwäsche & allgemein Transaktionen mit kriminellem Hintergrund (kann halt auch ein Nachteil sein - Stichwort totalitäre Systeme...)
Kein Falschgeld
Effizienzsteigerung im Bereich Zahlungsverkehr 
Bessere Inflationskontrolle / Geldmengenkontrolle
https://www.ecb.europa.eu/euro/html/digitaleuro-report.en.html


Nachteile: 
Freiheitseinschränkung 
potentiell kein Bargeld mehr (kann ein Komfortnachteil sein)


Zentralisierung vs. Dezentralisierung


Sonstige Stichworte...
Auswirkungen auf die Stabilität des Geldsystems... hier gibt es m.E. stabilisierende und potentiell destabilisierende Elemente... 


## Auswirkungen von CBDCS auf Geschäftsmodelle von Geschäftsbanken

Aktiva (Mittelverwendung) 
...Immobiliendarlehen an Moritz 100.000 EUR = Forderung aus Sicht der Geschäftsbank

Passiva (Mittelherkunft) 
Eigenkapital 
Fremdkapital (Zentralbankmoney (wird es das noch geben bei CBDCs?) oder Anlegermoney)


## Was ist das Kernprinzip hinter Proof of Work?

## Vergleichen Sie Custodial Wallets vs. Non-Custodial Wallets

## Angenommen Sie sind bei Warren Buffet zum Abendessen eingeladen - Worüber sprechen Sie? Würden Sie probieren Ihn von einem Investment in Ihr Ethereum based startup zu begeistern? Wenn ja wie?

# Lernen Durch Lehren Referatsvorschläge: 
## Welche Rolle spielen Merkle Trees im Bitcoin System? (3-4 Leute)

## Welche Rolle spielen Patricia Tries im Ethereum Network? (4-6 Leute)

## Repräsentiert der folgende Solidity Code eine valide Implementierung eines Merkle Trees? Wenn nein - was fehlt? (4-6 Leute)
Vorlage TypeScript Code https://deno.land/x/merkletrees@v1.3.0

## Welche Rolle spielt SHA256 im Bitcoin System? (3-4 Leute)

## Was versteht man unter dem Double-/Over-Spending-Problem?

## Was müsste passieren, damit ein 51%-Attack zustande kommt und welche Folgen hätte dies?

## Begründen Sie den Vorzug von Patricia Tries im Gegensatz zu Tries im Ethereum Netzwerk
Lösung: Effizienz bei der Speichernutzung, Schnelligkeit im Gebrauch, wichtig durch ständige Änderungen
Bietet sämtliche Funktionen, die Trie auch bietet: Suchen/Ersetzen/Löschen
An den Kanten können Teilstrings gespeichert werden und nciht nur einzelne Zeichen -> Effizienz
Patricia ist besonderer Radix 2 Trie

## Wie werden im Ethereum Netzwerk globale Daten gespeichert?
Lösung: Patricia Tries: Im World State Trie werden Adressen und Kontostände abgebildet. Dieser wird ständig aktualisiert. Der Storage Root zeigt auf den Account Storage Trie, bei dem die Konten mit den zugehörigen Daten verbunden sind. Vertragsdaten, Transkaktionszahlen etc. Transaktionen sind im Transaction tRie gespeichert: alle Transktionen mit Weltzustand (Kontostand), nicht mehr änderbar. Transaction Receipt Trie zeichnet Ergebnisse der Transaktionen auf und hat als Quittung den Hash der Transaktion mit Mapping auf Transction Trie.

# Fragen zu Merkle-Trees
## Wie funktionieren Merkle Trees?
Lösung:
Im ersten Schritt werden die untersten Werte (z.B. Namen) gehasht. Danach werden immer die Hashwerte die nebeneinander stehen konkateniert und im Anschluss erneut gehasht. Dieser Ablauf wird so oft durchgeführt, bis der Root Hash berechnet wurde. 

## Wie werden Merkle Trees im Kontext von Kryptowährungen eingesetzt?
Lösung:
Alle Transaktionen werden gehasht und mit ihrem Nachbarn konkateniert. Danach werden diese erneut gehasht und dies wird solange durchgeführt, bis ein Root-Hash(Hash des Blocks) entsteht

## Welche Probleme können durch Merkle-Trees gelöst werden?
Lösung: 
Die Merkle-Trees ermöglichen sicheres agieren in einer dezentralen no-trust environment durch die voll oder teilverifikation einzelner Daten.

## Warum werden AirDrops durchgeführt? (Multiple Choice)
- [x] Early Adapters belohnen
- [x] Voting Power verteilen
- [ ] Währung deployn
- [ ] Denial of service Angriffe durchführen


