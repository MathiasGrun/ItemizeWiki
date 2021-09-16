# Kryptografi

<!--https://ctf101.org/cryptography/overview/-->

Kryptografi handler om å bruke matematikk for å skjule et innhold i en tekst. Fra ung alder av, er det mange som har forsøkt å lage en form for “røverspråk”. Dette er i teorien et kryptert språk. 

Kryptografi brukes i dag absolutt hele tiden. Når passord blir lagret, når du sender informasjon over nettet, når du har låst din PC, kryptert din harddrive, osv. 

Grunnen til at kryptografi er viktig, er for å sørge for at personer som ikke har tilgang til noe ikke kan få det. I kryptografi bruker vi gjerne begrepene kryptere og dekryptere, eller chiffrere og dechiffrere. Et "chiffer" ("cipher" på engelsk) betyr en måte å kryptere på, f.eks. _Ceasar Cipher_. Kryptering betyr å gjøre meldingen uleselig og dekryptere betyr å gjøre kryptert melding leselig. Vi bruker gjerne en _nøkkel_ for å kryptere og dekryptere meldinger. Hvis du og din venn hadde et røverspråk på barneskolen, så hadde dere antakeligvis et mønster, slik at dere kunne forstå hverandre. Da er det dette mønsteret som er _nøkkelen_.

## Terminologi

Siden kryptografi handler mye om matematikk, er det vanlig å ha noen enkle begreper klare. Notasjonen her kan variere litt fra sted til sted, men i denne artikkelen skal vi være konsistent på denne måten. <!--(Slides fra Colin)-->

- M = En melding i _klartekst_. Klartekst betyr at det er leselig for alle sammen. Det kan være f.eks. “Hallo”. Mange bruker og _p_ eller _P_ for klartekst, eller _plaintext_ på engelsk. 
- C = Den krypterte meldingen. Det er ikke leselig for oss, og kan se f.eks. sånn her ut: “Ibmmp”. 
- K = nøkkel (key). Denne kan se veldig forskjellig ut, avhengig av hva slags kryptering som er brukt på meldingen (M). I de fleste tilfeller skal denne nøkkelen være hemmelig. Finner man nøkkelen, kan man dekryptere C. 
- E = krypteringsfunksjonen (encryption function). Dette betegner funksjonen som brukes for å kryptere.
- D = Dekrypteringsfunksjonen (decryption function). Betegner funksjonen som brukes for å dekryptere. 
- Kryptering: C = E(K, M). Her ser vi hvordan vi får C, altså vår krypterte tekst, på venstresiden. C er lik krypteringsfunksjonen E som tar inn nøkkelen, K, og klartekstmeldingen, M. 
- Dekryptering: M = D(K, C). Her får vi klartekstmeldingen, M, på venstresiden. M er lik dekrypteringsfunksjonen, D, som tar inn nøkkelen, K, og den krypterte meldingen, C. 

Merk at vi og gjerne bruker notasjonen at D = E<sup>-1</sup>, altså at D er lik _inversen_ av E. Inversen av en funksjon, betyr bare det motsatte av en funksjon.
De to største hovedformene for kryptografi kalles symmetrisk og asymmetrisk kryptografi. 
_Symmetrisk kryptografi_ betyr at nøkkelen kun er kjent mellom avsender og mottaker. Dette er den enkleste formen for kryptering. 
_Asymmetrisk kryptografi_ handler om at begge parter av kommunikasjonen har en privat nøkkel og en offentlig nøkkel. 

NB!
Det er mange forskjellige måter å kryptere på. "PicoCTF oppg. 5, 6 og 7" er eksempler på oppgaver som ikke direkte er chiffere, men andre måter å skjule en melding på. 
