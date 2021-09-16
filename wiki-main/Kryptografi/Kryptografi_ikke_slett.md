# Kryptografi

https://ctf101.org/cryptography/overview/

Kryptografi handler om å bruke matematikk for å skjule et innhold i en tekst. Fra ung alder av, er det mange som har forsøkt å lage en form for “røverspråk”. Dette er i teorien et kryptert språk. 

Kryptografi brukes i dag absolutt hele tiden. Når passord blir lagret, når du sender informasjon over nettet, når du har låst din PC, kryptert din harddrive, osv. 

Grunnen til at kryptografi er viktig, er for å sørge for at personer som ikke har tilgang til noe ikke kan få det. I kryptografi bruker vi gjerne begrepene kryptere og dekryptere, eller chiffrere og dechiffrere. Kryptering betyr å gjøre meldingen uleselig og dekryptere betyr å gjøre kryptert melding leselig. Vi bruker gjerne en _nøkkel_ for å kryptere og dekryptere meldinger. Hvis du og din venn hadde et røverspråk på barneskolen, så hadde dere antakeligvis et mønster, slik at dere kunne forstå hverandre. Da er det dette mønsteret som er _nøkkelen_.

## Terminologi

Siden kryptografi handler mye om matematikk, er det vanlig å ha noen enkle begreper klare. Notasjonen her kan variere litt fra sted til sted, men i denne artikkelen skal vi være konsistent på denne måten. (Slides fra Colin)

- M = En melding i _klartekst_. Klartekst betyr at det er leselig for alle sammen. Det kan være f.eks. “Hallo”. Mange bruker og _p_ eller _P_ for klartekst, eller _plaintext_ på engelsk. 
- C = Den krypterte meldingen. Det er ikke leselig for oss, og kan se f.eks. sånn her ut: “Ibmmp”. 
- K = nøkkel (key). Denne kan se veldig forskjellig ut, avhengig av hva slags kryptering som er brukt på meldingen (M). I de fleste tilfeller skal denne nøkkelen være hemmelig. Finner man nøkkelen, kan man dekryptere C. 
- E = krypteringsfunksjonen (encryption function). Dette betegner funksjonen som brukes for å kryptere.
- D = Dekrypteringsfunksjonen (decryption function). Betegner funksjonen som brukes for å dekryptere. 
- Kryptering: C = E(K, M). Her ser vi hvordan vi får C, altså vår krypterte tekst, på venstresiden. C er lik krypteringsfunksjonen E som tar inn nøkkelen, K, og klartekstmeldingen, M. 
- Dekryptering: M = D(K, C). Her får vi klartekstmeldingen, M, på venstresiden. M er lik dekrypteringsfunksjonen, D, som tar inn nøkkelen, K, og den krypterte meldingen, C. 

Merk at vi og gjerne bruker notasjonen at D = E<sup>-1</sup>, altså at D er lik _inversen_ av E. Inversen av en funksjon, betyr egentlig bare det motsatte av en funksjon.
De to største hovedformene for kryptografi kalles symmetrisk og asymmetrisk kryptografi. 
_Symmetrisk kryptografi_ betyr at nøkkelen kun er kjent mellom avsender og mottaker. Dette er den enkleste formen for kryptering. 
_Asymmetrisk kryptering_ handler om at begge parter av kommunikasjonen har en privat nøkkel og en offentlig nøkkel. Dette kommer vi tilbake til senere.

## Substitusjon 

Substitusjon betyr å bytte ut. Det betyr at vi bytter ut en bokstav med en annen. Hvordan vi velger å bytte ut bokstaven, avhenged av hva slags kryptering vi ønsker å bruke. I _Ceasar Cipher_, ser vi på alfabetet vårt og velger hvor mange plasser bort vi ønsker å hoppe. Da blir nøkkelen antall plasser. I _Random Simple Substitution Cipher_, er nøkkelen vår et annet valgt ord. Poenget er at det finnes mange måter å velge å bytte ut bokstaver på, og det er det substitusjonskryptering handler om. Når vi "plusser" sammen bokstaver og forflytter oss i alfabetet, kaller vi dette et _shifted alphabet (skiftet alfabet)_. 

For å enkelt plusse sammen bokstaver, kan det og være greit å bruke en tabell som dette (bare husk at denne ikke har med mellomrom):

Når vi snakker om et _Simple substitution cipher_, mener vi at det kun bruker ett alfabet kombinert med én nøkkel. 

### Ceasar Cipher
Den simpleste formen for kryptering innenfor substitusjon kalles _Ceasar Cipher_. 
Dersom vi bruker oversettelsen at A=1, B=2 osv, så plusser vi på et gitt tall (nøkkelen) og får en kryptert melding ut. Dersom vi f.eks. har bokstaven A(=1) og plusser på 5, får vi tallet 6. Dette blir da representert som F. For å dekryptere vil vi da kun trekke fra tallet 5. Det som er viktig å huske på, er at dersom vi plusser på et tall og havner over 26, begynner vi på nytt i alfabetet. (Se "Modulær aritmetikk" under "Tall og Alfabet")

![Ceasar Cipher med K=3](bilder/ceasar_cipher.PNG)

eks: 
Melding, M = "HEISANN" = 8 5 9 19 1 14 14
Nøkkel, K = 8
Krypteringsfunksjon, E = Ceasar Cipher

Kryptert tekst:
 C = E(K, M) = Ceasar Cipher(8, "HEISANN") = 8+8 5+8 9+8 19+8 1+8 14+8 14+8 = 16 13 17 27 9 22 22 = "PMQAIVV". 

Dekryptert tekst:
M = D(K, C) = Ceaser Cipher<sup>-1</sup>(8, "PMQAIVV") = 16-8 13-8 17-8 1-8 9-8 22-8 22-8 = 8 5 9 (-7) 1 14 14 = "HEISANN"

Kommentar: Legg merke til at vi  får tallet 27 (S=19 så plusser vi på 8) når vi krypterer. I vårt tilfelle er Z=26, så 27 blir da A=1. Vi har altså, så vidt, gått en runde rundt klokka og havner på A igjen, som er 1. Hvis vi skulle ha brukt modulær beregning direkte, ville A vært 0, og Z vært 25. Derfor er det viktig å ha tunga rett i munn og være sikker på hvordan du har tallfestet bokstavene. Ved en runde rundt klokka, er dette ikke noe problem, fordi da kan vi egentlig bruke vanlig modulær aritmetikk og trekke fra 1 og få riktig svar. Men dersom vi f.eks. går 17 ganger rundt klokka, må vi eventuelt trekke fra 17 og da begynner det å bli litt kronglete. Derfor er det enklest å ha det på måten A=1 hvis vi jobber med små tall, men heller bruke A=0 hvis vi jobber med store tall.

Hvis vi bruker A=0, B=1, ... Z=25, får vi følgene: 
C = E(K,M) = M + K mod26 der M er hver enkelt bokstav og K er nøkkelen, i dette tilfellet. 
M = D(K,M) = M - K mod26


### ROT13
En svært vanlig form for _Ceasar Cipher_, er _ROT13_. Dette er helt vanlig _Ceasar Cipher_, men nøkkelen er 13. _ROT13_ står egentlig for "rotate by 13 places", som vi nå har sett er hele definisjonen på _Ceasar Cipher_. Det betyr at _ROT13_ flytter hver bokstav 13 plasser i alfabetet. _ROT13_ er spesielt mye brukt fordi den splitter det engelske alfabetet i to. Det medfører faktisk at funksjonen for å kryptere er helt lik funksjonen for å dekryptere. Dermed er det en svært enkel form for kryptering. 

![rot13](bilder/rot13.PNG)

I terminalen på Unix, altså i _bash_, har Ceasar Cipher og ROT13 fått en egen kommande innebygd, ettersom den er såpass vanlig brukt:

```bash
 mathias@kali:~$ tr A-Za-z N-ZA-Mn-za-m
 ``` 
Det som skjer her, er at vi bruker kommandoen _tr_, "translate". Delen _A-Za-z_ er det vi kaller _set1_ her definerer vi hvlke bokstaver som skal byttes ut med noe annet. Siden vi både har _A-Z_ og _a-z_, betyr det at alle de store bokstavene og alle de små bokstavene skal byttes ut. Den andre delen, _N-ZA-Mn-za-m_, er det vi kaller _set2_. Her forteller vi hva som skal skje med _set1_. Hvis vi kun ser på de store bokstavene først, blir det enklere. Vi ser at A-Z er _set1_. _N-ZA-M_ er _set2_. _set2_ sier egentlig at alfabetet er splittet på midten og de to delene av alfabetet har byttet plass, hvilket faktisk er det samme som _ROT13_.

I praksis kan kommandoen fungere slik: 
```bash
 mathias@kali:~$ echo "Her er tekst jeg vil kryptere" | tr A-Za-z N-ZA-Mn-za-m
 Ure re grxfg wrt ivy xelcgrer
 ``` 
Outputtet, "Ure re grxfg wrt ivy xelcgrer" er da kryptert med _ROT13_.

Et triks for å slippe å huske denne kommandoen hele tiden er å bruke kommandoen _alias_. Det denne kommandoen gjør, er å endre en lang kommando til det du har lyst til:

<!-- TODO: legge til flere "bash" -->
```bash
 mathias@kali:~$ alias rot13="tr A-Za-z N-ZA-Mn-za-m"
 ``` 

 Vi kan da skrive: 
```bash
 mathias@kali:~$ echo "Ure re grxfg wrt ivy xelcgrer" | rot13
 Her er tekst jeg vil kryptere
 ``` 
 for å dekryptere. Legg også merke til hvordan vi bruker den samme funksjonen til å kryptere som å dekryptere. Vi kan altså se hvordan _ROT13_ er sin egen invers. 

 _ROT13_ og _Ceasar Cipher_ her veldig greie å fortså og det er rimelig rett fram å kryptere. Problemet er at siden krypteringen baserer seg på hvor mange ganger vi flytter oss i alfabetet, er det ikke alt for mange mulige nøkler. Det er faktisk bare 25 forskjellige måter å ha det på. Det er veldig enkelt for et dataprogram eller til og med et menneske å se hva nøkkelen er. Kanskje du ser det i eksemepelet under? Tips: let etter dobbeltkonsonanter, vanlige bokstaver som vokaler og andre ord du tror kan være deler av løsningen. 

 #### picoCTF oppg. 2 Crypto
 Oppgaveteksten sier "Cryptography can be easy, do you know what ROT13 is?" og hintet forteller at oppgaven kan løses på nettet, hvis vi ikke ønsker å gjøre det for hånd. 
 Teksten vi har fått er "cvpbPGS{abg_gbb_onq_bs_n_ceboyrz}". Vi kan rimelig greit se at dette er et flagg som er kryptert. Her ville jeg bare brukt kommandoen vi nettopp har lært:

 ```bash
 mathias@kali:~$ echo "cvpbPGS{abg_gbb_onq_bs_n_ceboyrz}" | rot13
picoCTF{not_too_bad_of_a_problem}
 ``` 
### Random Simple Substitution Cipher
Her trenger vi egentlig to alfabet: vårt vanlige, og et annet med bokstaver som representerer de i vårt vanlige alfabet. _Ceasar Cipher_ er en variant av et _Simple Substitution Cipher_, fordi hvis vi vet hvor mange ganger vi har flyttet oss bort i alfabetet, vet vi hvordan det andre alfabetet ser ut: 

Ceasar Cipher med ROT13:
- Alfabet 1: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
- Alfabet 2: N O P Q R S T U V W X Y Z A B C D E F G H I J K L M

Vi ser da at vi kan enkelt dekryptere ved å ha disse ovenfor hverandre. 

(Eksempel på) Random simple substitution cipher: 
- Alfabet : A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
- Nøkkel  : P H Q G I U M E A Y L N O F D X J K R C V S T Z W B

Vi ser da at "Heisann" blir til "Eiarpff". 

I _Random Simple Substitution Cipher_, er det ikke nødvendigvis noe mønster. A kan bli en B, en Y, en K, eller hva som helst annet. Dermed blir hele nøkkelen det vi kan kalle "Alfabet 2" ovenfra. Det betyr at nøkkelen vår har lengde 26. Den første bokstaven i nøkkelen vår sier hva A blir til. Den har 26 muligheter. Den neste bokstaven i nøkkelen sier hva B blir til, den har kun 25 muligheter, siden den som representerer A allerede har tatt en mulighet. Slik fortsetter det nedover. Vi får dermed 26 * 25 * 24 * ... *2 * 1 = 26! mulige forskjellige nøkler, så det å teste seg fram her er veldig vanskelig.

I begynnelsen kan man tenke at dette høres veldig trygt ut. Men slik er det faktisk ikke. Med dagens teknologi kan vi bruke _frekvensanalyse_ for å dekryptere et slikt chiffer, uten nøkkelen. Det baserer seg på at i det engelske språket er det noen bokstaver og ord som er vanligere enn andre, altså at det har høyere freksens (gjelder så klart og for det norske språket, men vi har brukt engelsk som eksempel og holder oss til det). Dersom vi har en lang tekst, som hele er kryptert på denne måten, kan vi (PC'en), telle alle bokstavene i teksten og gjette seg fram til hvilke bokstaver som blir til hva. Videre er det noen 2-bokstavsord som er mye vanligere enn andre og det samme med 3-bokstavsord (kan og kalles 2-gram og 3-gram). Hvis du f.eks. i en tekst kryptert med dette chifferet ser gjentakende ganger 3-grammet: "Kio". Dersom det dukker opp rimelig ofte, er det stor grunn til å tro at K blir til T, i blir til h og o blir til e. Det er fordi det vanligste 3-grammet i det engelske språket er ordet "The". 

### Vigenère Cipher
Vigenère Cipher finner en løsning på hvordan man skjuler frekvensanalysen ved å "glatte ut" frekvensen av de forskjellige bokstavene. Det betyr at A kan bli til L i ett tilfelle, men den neste A'en kan bli en annen bokstav. Denne krypteringen kalles et _periodisk substitusjonschiffer basert på skiftede alfabet_, fordi vi bruker den samme nøkkelen på nytt og på nytt. Vi har altså en periode som er lengden på nøkkelen. 
I Vigenère har vi én nøkkel. La oss f.eks bruke "KOMTEK" som nøkkel. Siden ordet "KOMTEK" er seks bokstaver langt, blir vi nødt til å dele opp meldingen vår i "blokker" på seks. Vi bruker og notasjonen der A=0, B=1 ... Z = 25 og mellomrom=26. For nå kaller vi mellomrom bare \#.

Med nøkkelen vår K, er det vanlig å dele den opp i hver bokstav slik:
K = "KOMTEK"
k<sub>i</sub> er da den i'te bokstaven i K. 
k<sub>0</sub> = "K", k<sub>1</sub> = "O", k<sub>2</sub> = "M", osv. 
Vi sier og at p<sub>i</sub> er _plaintext_ bokstavene. P er hele _plaintexten_.

På denne måten bli krypteringsfunksjonen:
f<sub>i</sub>(P) = (p<sub>i</sub> + k<sub>i</sub>) mod27
Legg merke til at vi bruker mod 27 her, fordi vi har A=0... Z=25 og \#=26. 

Eksempel: 
Meldingen vi skal sende: "DETTE ER EN TEKST"
Nøkkelen: "KOMTEK"
Det første vi gjør er å skrive om meldingen, ved å dele den inn i blokker på seks bokstaver (siden nøkkelen er seks bokstaver lang i dette tilfellet), og legger til mellomrom som \#. Hvis vi har for få bokstaver, fyller vi inn med mellomrom: "DETTE\#ER\#EN\#TEKST\#"
Vi overfører til tall og plusser på med nøkkelen (her har jeg splittet opp i blokker på seks, så det blir lettere å se.):
- DETTE\# ER\#EN\# TEKST\#
- KOMTEK KOMTEK KOMTEK
- NSFMIJ OBLSZJ MIUCHJ

Her er den krypterte teksten egentlig: "NSFMIJOBLSZJMIUCHJ", uten mellomrom. NSELIJOELXRJCSWKX
  
For å vise hvordan funksjonen fungerer, ser vi på krypteringen av den første bokstaven i klartekst, "D". Gjør vi "D" om til tall, blir D=3. p<sub>1</sub>=3 Den første delen av nøkkelen er "K". Det blir 10 som tall. k<sub>1</sub>=10. (Husk at vi begynner på A=0). p<sub>2</sub>="E"=4, k<sub>2</sub>="O"=14
- f<sub>1</sub>(P) = f<sub>1</sub>(p<sub>1</sub>) = (p<sub>1</sub> + k<sub>1</sub>) = 3 + 10 = 13 = "N"
- f<sub>2</sub>(P) = f<sub>2</sub>(p<sub>2</sub>) = (p<sub>2</sub> + k<sub>2</sub>) = 4 + 14 = 18 = "S"
- Husk at vi hele tiden regner mod27. 

Det er viktig å poengtere at det er ikke alle som velger å ha mellomrom som et eget tegn. For å få en chiffertekst som er mest mulig uleselig, er dette lurt, ettersom det også stokker om på mellomrom. Ofte vil vi og se at vi lar mellomrom bli, og lar da heller nøkkelen gli over mellom:
- DETTE ER EN TEKST
- KOMTEK KO MT EKKOMT
- NSFMI OB SZ MIUCH

Det ser rimelig likt ut, men med noen få forskjeller, grunnet ikke noe mellomrom. 

Vi kan da se at Vigenère gjør den første E'en (den andre bokstaven) først til en S. Den andre E'en, altså den femte bokstaven, blir til en I. Dermed er det ikke så lett å gjette seg fram til hvilke bokstaver som blir hva, fordi de endres hele tiden. 

På 1900-tallet trodde man at Vigenère Cipher var umulig å knekke, uten nøkkelen. Vi kan se hvordan dette gjøres, under "picoCTF Oppg. 8 Crytpo". Det er noen steg man må gjennom for å få det til. Men slik det fungerer, kort oppsummert, er at vi først må finne størrelsen på nøkkelen. Dette kan programmer hjelpe oss med. 
Deretter må vi sjekke en og en bokstav i nøkkelen. Da bruker vi frekvensanalyse. Vi ser altså om det gir mening, statistisk, om en bokstav pluss en annen gir så så mange bokstaver av det vi har i chifferteksten. Dersom vi f.eks. tenker at den første bokstaven i nøkkelen er en K, og vi antar at nøkkelen er 4 karakterer lang, ser vi da hvordan det ser ut om vi plusser en K på hver fjerde bokstav i chifferteksten. Dersom det ser ut til å stemme, kan vi anta at det er en K. Vi skal se et eksempel på dette, i detalj, senere.  

#### One time pad
_One time pad_ (OTP) er en av de absolutt tryggeste måtene å kryptere på. Det kommer på bekostning av at det er veldig kronglete å håndtere nøkkelen. OTP kan minne fungerer som Vigenère, men vi har ikke en kort nøkkel som brukes periodisk. Vi har derimot en nøkkel som må være like lang som hele teksten vi skal kryptere. Nøkkelen må og være helt tilfeldig. På denne måten er det helt umulig å finne en periode eller noe som helst mønster. OTP har blitt brukt mye gjennom den kalde krigen, ettersom den er umulig å dekryptere uten nøkkelen. 

#### picoCTF oppg. 3 Crypto
Vi får beskjed om at OTP er veldig trygg å bruke, men mindre man kan nøkkelen. Chifferteksten vår er "UFJKXQZQUNB", og vi får gitt at nøkkelen er "SOLVECRYPTO". I tillegg får vi en tabell som hjelper oss med å plusse bokstaver sammen. Vi får og vite at flagget er på formen picoCTF{...}. Vi skal altså finne det som skal stå inni krøllparentesene. 

Siden vi her har den krypterte teksten, legge hver on en bokstav her i "midten". Vi kan da si at nøkkelen legges på venstre og det hemmelige ordet legges oppå. 
Ved å titte ser vi at det blir "CRYPTOISFUN". 
Vi kan og legge merke til at det er er egentlig som et Vigenère Cipher, der perioden er 11 og klarteksten vår er og 11 bokstaver lang. 

#### picoCTF Oppg. 4 Crypto
Denne oppgaven heter "Ceasar", så vi skjønner fort hva vi skal gjøre. Det står det at vi skal dekryptere medlingen "picoCTF{jyvzzpunaolybipjvunfzpthre}". For å gjøre dette kjapt, når vi vet at det er et Ceasar Cipher, ville jeg rett og slett brukt en oversetter på nettet. Man står helt fritt fram til å prøve ut noen kombinasjoner selv, men her velger jeg å bruke decode.fr sin decoder. 

Vi legger inn chifferteksten og finner ordet "crossingtherubicongysimakx". ("Crossing the rubicon", Bob Dylan. Se hvordan vi og ser "gysimakx", bak. Denne er vel litt for å prøve å skape forvirring).
Flagget blir da picoCTF{crossingtherubicongysimakx}. 

#### picoCTF Oppg. 8 Crytpo
Her får vi en lang tekst som vi ser er kryptert. Ser vi kjapt gjennom ser vi de krøllede parentesene et sted: hgqqpohzCZK{m311a50_0x_a1rn3x3_h1ah3xf653pdkh}. Vi kan prøve å kjøre hele teksten gjennom en Ceasar Cipher decoder, men her finner vi faktisk ingenting. Her blir vi nødt til å bruke et dekrypteringshjelpemiddel. Jeg bruker her cryptool.org. Her kan vi først sende teksten gjennom en frekvensanalyse ("Frequency Analysis" under "Cryptoanalysis"). Vi ser her at frekvensen av de forskjellige bokstavene er mye mer "glattet" ut enn det som er vanlig i det engelske språket. 

![Frekvensanalyse av chifferteksten](bilder/frekvensanalyse_vig.PNG)

![Vanlig frekvens i engelsk alfabet](bilder/engelsk_frekvens.PNG)

Vi kan altså anta at vi bruker en form for kryptering som glatter ut frekvensene av de forskjellige bokstavene. Da er Vigenère naturlig å bruke. Vi åpner "Vigenère Analysis" under "Cryptoanalysis" og kopierer inn chifferteksten. (Enkleste er å bare søke når du er på den grønne versjonen av cryptool.) 
Vi får ikke noe hjelp av oppgaven og må selv gjette hvor lang nøkkelen er. I Cryptool, kan vi se på forskjellige N-gram. Dermed vil Cryptool hjelpe med å gjette hvor lang nøkkelen er etter å se på statistikk over det engelske alfabetet. På 1-, 2-, og 3-gram sier den at det er høyest sannsynlighet for at nøkkelen er 2 karakterer lang, men med 4 på andreplass. På 4- og 5-gram forteller den at 4 er mest sannsynlig med 2 på andreplass. Ettersom det den vanligste ordlengden, i gjennomsnitt, i det engelske språket er 4,7 bokstaver, stiller 4- og 5-gram sterkere enn 1-, 2- og 3-gram. Derfor stoler vi på at nøkkelen er 4 karakterer lang. 

![Størrelse på nøkkel](bilder/nokkelstr_vig.PNG)

Vi trykker da på tallet 4 litt under. Her ser får vi først opp 4 A'er, så to sett med søyler. De fire A'ene er det vi inn så lenge antar er nøkkelen. Vi markerer den første helt til venstre. Deretter er jobben  å trykke "Right"/"Left" slik at søylene matcher mest mulig overens. Både i høyde på søylene, men og hvor de "klumper seg rundt hverandre". Vi kan og se på tallet mellom "Right"- og "Left"-knappene og få det slik at Autcorrelation-tallet blir så lavt som mulig. Hvis vi da trykker oss fram til at den første karakteren i nøkkelen vår, altså bokstaven lengst til venstre, blir til en F, ser det rimelig riktig ut i forhold til søylene. 

![Første karakteren i nøkkelen](bilder/forste_del_av_nokkel_vig.PNG)

Vi kan da bevege oss over til den neste karakteren. Fortsetter vi på samme måte her, ser vi at det blir en L. Vi fortsetter på samme måte, og får A og G på de neste. Vi har da antatt at nøkkelen er "FLAG". Dersom vi ser outputtet under, ser vi at vi plutselig kan lese det som står der. Les gjerne det for å få litt bakgrunnshistorie til Vigenère Cipher. 

![Nøkkelen ferdig](bilder/ferdig_nokkel_vig.PNG)

Flagget finner vi i den dekrypterte teksten: PICOCTF{B311A50_0R_V1GN3R3_C1PH3RA653EDEC}. 


### Andre former for "kryptering"

#### picoCTF Oppg. 5 Crypto
Vi ser her et eksempel på hvordan kjernen i kryptografi, nemlig å skjule en melding, ikke nødvendigvis trenger å være modulær aritmetikk og skiftede alfabeter. Her finner vi en haug med rare flagg. Vi ser de ikoniske krølleparentesene. Flaggene ser heller ikke ut som nasjonalflagg. Vi vet at løsningen skal være på formen picoCTF{...}. Utfra dette, Googlet jeg "falgs as letters". Da dukker det opp "internasjonale maritime signalflagg". Vi ser da at på sjøen kan man symbolisere bokstaver som flagg. Ved å titte i en tabell, finner vi løsningen kjapt: PICOCTF{F1AG5ANDSTU55}. 
Obs! Her var det en del forskjellige bilder å lese fra, valgte en versjon som ga mening. 

#### picoCTF Oppg. 6 Crypto
For den som har sett dette før, er det koordinater. Vi kan plotte en koordinat rett inn i Google, finne hvor vi havner og antakeligvis hente ut en bokstav. 

picoCTF{(35.028309, 135.753082)(46.469391, 30.740883)(39.758949, -84.191605)(41.015137, 28.979530)(24.466667, 54.366669)(3.140853, 101.693207)_(9.005401, 38.763611)(-3.989038, -79.203560)(52.377956, 4.897070)(41.085651, -73.858467)(57.790001, -152.407227)(31.205753, 29.924526)}

Koordinatene gir byene: Kyoto (Japan), Odessa, Dayton (Ohio), Fatih/Istanbul (Tyrkia), Abu Dhabi (DFAE), Kuala Lumpur (Malaysia), Addis Ababa (Etiopia), Loja (Ecuador), Amsterdam (Nederland), Sleepy Hollow (USA), Kodiak (USA), Alexandria (Egypt). 
Slår vi første bokstav i alle byene sammen og har med understreken fra koordinatene får vi:
picoCTF{KODIAK_ALASKA} t


#### picoCTF Oppg. 7 Crypto
Morsekode er slik vi kommuniserte med på radio før vi kunne sende over stemme som signal. Det er bare å finne fram en morsetabell, eller hive det inn i en oversetter. 

PICOCTF{M0RS3C0D31SFUN1677257287}

## Public key cryptograpyhy (Offentlig nøkkel kryptografi)
(Colins slides)

Enn så lenge, har vi kun sett på kryptering med private nøkkeler. Det betyr at begge parter av kommunikasjonen har en privat nøkkel som brukes for å kryptere og dekryptere. Men det har seg slik at dette ikke alltid er helt gunstig. F.eks. kan det være vanskelig å dele denne nøkkelen med hverandre. Det er og fordelaktig med assymetrisk kryptering fordi det kan gi oss _digitale signaturer_ (skal ikke inn på det her). Dermed har vi annen måte å kryptere på, der det brukes en "offentlig nøkkel" for å kryptere. Public key cryptography (PKC), eller _asymmetrisk kryptering_, baserer seg på noen viktige matematiske prinsipper, og gjør det mulig å kryptere ting vi brukere hele tiden i dag. Vi bruker altså matematikk som gjør det såpass vanskelig, til og med for datamaskiner, at det å prøve å dekryptere uten nøkkel eller finne nøkkelen tar alt for lang tid. Dersom det ikke er mulig (eller tar flere tusen år) for en vanlig datamaskin (ikke en kvante-computer) å løse et slikt matematisk problem, sier vi at det er _unfeasible_ å _brute force_ seg fram til svaret. 
RSA er den mest vanlige formen for PKC vi har. (For å forstå matematikken i PKC, anbefales det å lese "Tallteorien i PKC", under "Tall of alfabet").

Vi bruker både private og offentlige nøkler i PKC. Den private skal holdes hemmelig, mens den offentlige er åpen for alle å se. Vi krypterer med den offentlige nøkkelen og dekrypterer med den private nøkkelen. 

### RSA
Som nevnt, er RSA den vanligste formen for PKC vi har. Slik fungerer det:
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

eks (Fra Colins forelesning 9):
- p = 43, q = 59 da er n = pq = 2537 
- φ(n) = (p − 1)(q − 1) = 2436
- Velger e = 5 
- d = e<sup>−1</sup> mod φ(n) = 5<sup>−1</sup> mod 2436 = 1949
- Hvis vi har f.eks. M = 50 så bli C = M<sup>e</sup> mod n = 50<sup>5</sup> mod 2537 = 2488
- Vi bruker hjelpemidler på nettet for å finne d = 5<sup>-1</sup> mod 2463 = 1949.
- Dekrypering blir da M = C<sup>d</sup> mod n = 2488<sup>1949</sup> mod 2537 som gir M=50.