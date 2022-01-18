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

## Welche Rolle spielt SHA256 im Bitcoin System? 
Lösung: Im Bitcoin System wird der SHA256 (= Secure-Hashing-Algorithmus) für das Erstellen neuer Bitcoin Wallet Adressen und das Mining von Blöcken für die Blockchain (also der Validierung von Transaktionen) verwendet. Beim Mining von Blöcken muss das Nonce so lange hochgezählt werden, bis der Block-Hash, der das Nonce enthält, kleiner als das Taget ist. Hierin besteht die Schwierigkeit des Minings. Im Prinzip gibt das Target an, wie viele 0en am Anfang des validen Block-Hashes stehen müssen.

## Welche 3 Bedingungen müssen erfüllt sein, damit eine Hashfunktion als kryptographisch sicher gilt?
- Sie kann jede beliebige Bit- oder Bytefolge verarbeiten und erzeugt daraus einen Hash von fixer Länge.
- Sie ist stark kollisionsresistent: Es ist praktisch nicht möglich, zwei unterschiedliche Eingabewerte zu finden, die einen identischen Hash ergeben.
- Sie ist eine Einwegfunktion: Es ist praktisch nicht möglich, aus dem Hash den Eingabewert zu rekonstruieren.

## Wie läuft eine Transaktion im Bitcoin System ab?
Lösung: Es werden 3 Informationen benötigt: 
- Einen Input: dies ist eine Aufzeichnung darüber, welche Sender-Adresse zuvor Alice diese Bitcoins geschickt hat (sie hat sie von ihrer Freundin Eve erhalten).
- Eine Menge: dies ist die (Teil-)Menge an Bitcoins, die Alice Bob schickt.
- Einen Output: dies ist die Bitcoin-Adresse von Bob (Empfängeradresse).
Anschließend werden diese Informationen mit dem eigenen Private-Key signiert und an das Bitcoin Netzwerk gesendet. Im Netzwerk greifen Bitcoin-Miner die Transaktion auf, erstellen mit ihr einen Transaktionsblock und lösen sie eventuell auf.

## Wie wird eine Bitcoin Wallet Adresse generiert?
Public-Private-Key -> zuerst SHA-256 dann RIPEMD-160 => So entstehen kürzere Adressen als 256 Bit
öffentlicher Schlüssel ist 256 Bit lang, die gehashte Version, also die Bitcoin Adresse ist 160 Bit lang 
K = der öffentliche Schlüssel     A = Bitcoin-Adresse:
A = RIPEMD160(SHA-256(K))

## Was versteht man unter dem Double-/Over-Spending-Problem?

## Was müsste passieren, damit ein 51%-Attack zustande kommt und welche Folgen hätte dies?

## Begründen Sie den Vorzug von Patricia Tries im Gegensatz zu Tries im Ethereum Netzwerk
Lösung: Effizienz bei der Speichernutzung, Schnelligkeit im Gebrauch, wichtig durch ständige Änderungen
Bietet sämtliche Funktionen, die Trie auch bietet: Suchen/Ersetzen/Löschen
An den Kanten können Teilstrings gespeichert werden und nciht nur einzelne Zeichen -> Effizienz
Patricia ist besonderer Radix 2 Trie

## Wie werden im Ethereum Netzwerk globale Daten gespeichert?
Lösung: Patricia Tries: Im World State Trie werden Adressen und Kontostände abgebildet. Dieser wird ständig aktualisiert. Der Storage Root zeigt auf den Account Storage Trie, bei dem die Konten mit den zugehörigen Daten verbunden sind. Vertragsdaten, Transkaktionszahlen etc. Transaktionen sind im Transaction tRie gespeichert: alle Transktionen mit Weltzustand (Kontostand), nicht mehr änderbar. Transaction Receipt Trie zeichnet Ergebnisse der Transaktionen auf und hat als Quittung den Hash der Transaktion mit Mapping auf Transction Trie.



