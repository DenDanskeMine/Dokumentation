# eBGP
Der er intet internet uden eBGP.
Så her ville jeg gå i dybden med denne dejlige protokol.

## 

## Basic opsætning 
Her ses en meget simpel topologi, med 3 ISP'er der har 1 router i deres AS.<br>
Dette ville aldrig være tilfældet i virkeligheden. Dette er blot for at vise en simple config.

![](../../../Vedhæftet/BGP%20-%20Mini%20(1).png)

### R1:
```
router bgp 3292
neighbor 10.10.10.2 remote-as 209424
neighbor 10.10.10.9 remote-as 34705
```
### R2:
```
router bgp 209424
neighbor 10.10.10.1 remote-as 3292
neighbor 10.10.10.6 remote-as 34705
```
Nu burde vi se at R1 og R2 har formet et naboskab:

```
R1# %BGP-5-ADJCHANGE: neighbor 10.10.10.2 Up
```
```
R2# %BGP-5-ADJCHANGE: neighbor 10.10.10.1 Up
```
### R3:
```
router bgp 34705
neighbor 10.10.10.10 remote-as 3292
neighbor 10.10.10.5 remote-as 209424
```

Nu burde vi også kunne se at R3 har formet naboskab med de 2 andre routere:

```
R3# %BGP-5-ADJCHANGE: neighbor 10.10.10.10 Up
```
```
R3# %BGP-5-ADJCHANGE: neighbor 10.10.10.5 Up
```

## Forklaring af konfigurationen
Får vi går vidre med noget lidt sjovere, skal vi først lige tjekke, om vi faktisk fatter det vi lige har lavet.

`router bgp <AS-nummer>` er her vi giver routeren dens AS-Nummer (ASN)<br>

AS-nummrene kan man se som ID'et på ISP'ernes områder. Så meningen med BGP er altså at forbinde de her områder.

Det gør vi ved at skrive `neighbor <peer-ip> remote-as <Peer-AS>` 

Dette skal gøres på begge routere for at forme et naboskab.


## eBGP & iBGP:
Nu kobler vi 3 routere på i hver sky.<br>
Dette vil betyde at vi skal bruge iBGP inde i skyerne, og eBGP udenfor.
![](/Vedhæftet/BGP%20-%20Ibgp&ebgp.png)

---

### FASTSPEED:

#### R1:
```
router bgp 209424
neighbor 1.1.1.2 remote-as 209424
```
#### R2:
```
router bgp 209424
neighbor 1.1.1.1 remote-as 209424
neighbor 1.1.1.6 remote-as 209424
neighbor 10.10.10.1 remote-as 3292
```
#### R3:
```
router bgp 209424
neighbor 1.1.1.5 remote-as 209424
neighbor 10.10.10.6 remote-as 34705
```
![](/Vedhæftet/BGP%20-%20Ibgp&ebgp%20(1).png)
---
### STOFA:

#### R4:
```
router bgp 34705
neighbor 2.2.2.2 remote-as 34705
neighbor 10.10.10.5 remote-as 209424
```
#### R5:
```
router bgp 34705
neighbor 2.2.2.1 remote-as 34705
neighbor 2.2.2.6 remote-as 34705
neighbor 10.10.10.10 remote-as 3292
```
#### R6:
```
router bgp 34705
neighbor 2.2.2.5 remote-as 34705
```
![](/Vedhæftet/BGP%20-%20Ibgp&ebgp%20(2).png)
---
### TDC:

#### R7:
```
router bgp 3292
neighbor 3.3.3.2 remote-as 3292
neighbor 10.10.10.9 remote-as 34705
```
#### R8:
```
router bgp 3292
neighbor 3.3.3.1 remote-as 3292
neighbor 3.3.3.6 remote-as 3292
```
#### R9:
```
router bgp 3292
neighbor 3.3.3.5 remote-as 3292
neighbor 10.10.10.2 remote-as 209424
```
![](/Vedhæftet/BGP%20-%20Ibgp&ebgp%20(3).png)
  ![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/t/dendanskemine/dokumentation?logo=github&color=susscess) ![GitHub last commit (branch)](https://img.shields.io/github/last-commit/dendanskemine/dokumentation/main)
