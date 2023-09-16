
BGP (Border Gateway Protocol) er en routingprotokol, der bruges til at styre routing og udveksling af ruteinformation på internettet og i store private netværk.

## Vigtigste funktioner:

- **Routingprotokol:** BGP er en path-vector-protokol, der bestemmer de bedste ruter til dataoverførsel.

- **Autonome systemer (AS):** Internettet er opdelt i autonome systemer, og BGP bruges til at udveksle ruteinformation mellem disse.

- **Politikbaseret routing:** BGP tillader netværksadministratorer at implementere politikker for at styre rutevalg.

- **Stabilitet og pålidelighed:** BGP er designet til at være meget stabil og pålidelig.

- **Peer-til-peer-forbindelser:** BGP bruger TCP-baserede peer-til-peer-forbindelser mellem routere.

- **Internetudbydere og store organisationer:** BGP er afgørende for internetudbydere og store organisationer til styring af deres netværk og ruteopdateringer.

BGP spiller en central rolle i at sikre effektiv og pålidelig dataoverførsel på internettet.


### Autonome systemer (AS):

Hele BGP er bygget op på de her Autonome systemer (autonomous systems).
Man kan se et AS som sin egen sky, eller udbyder.


![eBGP](/Vedhæftet/AS%201.png)
På billedet oven over ses [eBGP](/Routing%20Protocols/EGP/BGP/EBGP.md).<br>


**eBGP:** Dette er en del af BGP, hvor internetudbydere udveksler routingtabeller med hinanden. Dette gør det muligt for dem at sende trafik på tværs af deres AS'er og til andre AS'er på internettet. eBGP spiller en afgørende rolle i at sikre, at internettrafikken når sin destination effektivt.

For at se hvordan man opsætter eBGP [klik her](EBGP.md#basic-opsætning)

Forskellen på [eBGP](/Routing%20Protocols/EGP/BGP/EBGP.md) og [iBGP](/Routing%20Protocols/EGP/BGP/IBGP.md) er enlig bare at eBGP bliver brugt imellem skyerne, og iBGP bliver brugt inde i skyerne.<br>
Med iBGP har alle neighbors det samme AS nummer. 
![iBGP](/Vedhæftet/iBGP.png)

  
  
  
  ![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/t/dendanskemine/dokumentation?logo=github&color=susscess) ![GitHub last commit (branch)](https://img.shields.io/github/last-commit/dendanskemine/dokumentation/main)
