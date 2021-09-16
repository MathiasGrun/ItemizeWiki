# RSA

<!-- TODO: Skrive mer om RSA, gjerne noen eksempler fra CTF-->

Nødvendige forkunskaper: "Intro", "Tallteori i assymmetrisk kryptering", "Modulær aritmetikk"

RSA er en form for Public Key Cryptography (Offentlig Nøkkel Kryptering eller Assymmetrisk Kryptering). 

Slik fungerer det:
- Vi har to primtall p og q. (Disse er i praksis veldig store, flere 100 sifre hver).
- Tallet n er gitt ved n=pq
- Vi velger en e tilfeldig, men slik at gcd(e, phi(n)) = 1
- Vi finner tallet d ved d = e<sup>-1</sup> mod phi(n)
- Den offentlige nøkkelen for kryptering er parret n og e, Vi får at K<sub>E</sub> = (n,e)
- Den private/hemmelige delen er p, q og d. Selve nøkkelen er bare K<sub>D</sub>=d

Si vi altså har en melding (oversatt til tall), M. Denne meldingen må være mindre enn n. For å kryptere denne meldingen, har vi da:
- C = E(M, K<sub>E</sub>)) = M<sup>e</sup> mod n
  
For å dekryptere, bruker vi inversen, d, vi kalkulerte tidligere:
- M = D(C, K<sub>D</sub>)) = C<sup>d</sup> mod n

eks: <!--(Fra Colins forelesning 9)-->
- p = 43, q = 59 da er n = pq = 2537 
- φ(n) = (p − 1)(q − 1) = 2436
- Velger e = 5 
- d = e<sup>−1</sup> mod φ(n) = 5<sup>−1</sup> mod 2436 = 1949
- Hvis vi har f.eks. M = 50 så bli C = M<sup>e</sup> mod n = 50<sup>5</sup> mod 2537 = 2488
- Vi bruker hjelpemidler på nettet for å finne d = 5<sup>-1</sup> mod 2463 = 1949.
- Dekrypering blir da M = C<sup>d</sup> mod n = 2488<sup>1949</sup> mod 2537 som gir M=50.