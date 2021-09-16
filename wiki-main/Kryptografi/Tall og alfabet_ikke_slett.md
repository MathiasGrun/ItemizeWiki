 

# Tall og alfabet 

Det er viktig å definere et alfabet i kryptografi. Som du kanskje har hørt, jobber datamaskiner kun med 1’ere og 0’ere. Det betyr at datamaskinen må oversette tall om til bokstaver. Hvordan dette fungerer skal vi se nærmere på her. 

## Binære tall
Binære tall betyr tall som kun er satt sammen av 0 og 1. Fordi en datamaskin, i all hovedsak, kun jobber med signaler som enten er på eller av, representerer vi dette som 0 og 1. I forhold til hvordan vi vanligvis teller (10-tallssystemet, eller desimalt, ikke til å forveksle med tall bak komma), baserer det binære systemet seg på kun på 2 tall. 
Når man teller binært, begynner man på 0. så går man til 1. Men nå har vi brukt opp alle tallene vi har, og da gjør vi det samme som vi gjør i 10-tallssystemet (desimalt) når vi når 9; vi begynner på nytt, men bruker to sifre. I 10-tallssytemet (desimalt), når vi når tallet 10, betyr det egentlig at vi har brukt opp de tallene vi har (0-9). Da legger vi på 1 foran og begynner på nytt. Det samme gjør vi med de binære tallene. Når vi når 1, så legger vi på 1 foran og begynner med 0 igjen bak. Vi ser da at tallet 10 på binært, blir 2 desimalt. 
På bildet ser vi hvordan det kan være vanlig å begynne med et visst antall 0’ere. Dette er kun for å vise “hvor langt” vi teller. 

 ![Binære tall](bilder/binære_tall.PNG)

Et binært siffer (enten 0 eller 1) kalles et bit. Et bit har 2 mulige kombinasjoner, 0 eller 1. Har vi to bit, kan hvert bit ha 2 mulige kombinasjoner. Vi har da 2 bit med 2 kombinasjoner hver, hvilket gir 2<sup>2</sup> = 16 antall mulige kombinasjoner. Med fire bits, har vi 2<sup>4</sup>=16 antall mulige kombinasjoner, noe vi ser utfra bildet. (Legg merke til at vi inkluderer 0 med i antall kombinasjoner. 

Vi sier og at 8 bits utgjør 1 byte. 8 bits kan representere 2<sup>8</sup>=256 forskjellige tall. 128GB (gigabyte)  betyr muligheten til å representere 2<sup>128 000 000 000</sup> kombinasjoner. 

I terminalen og i datamaskinen generelt, er det vanlig å si fra at man bruker et binært system, ved å skrive _0b_ foran tallet. Tallet 7 blir da 0b0111. Det er for å unngå å tro at man skriver tallet 111 (hundreogelleve) på decimal. 

## Heksadesimale tall
Et annet vanlig tellesystem som brukes i datamaskiner er det heksadesimale systemet (16-tallssystemet, kan og bare kalle det “hex”). Dette brukes gjerne fordi det passer veldig bra sammen med det binære systemet, og gjør det enklere å representere store tall. Det er enkelt å gå fra hex til bin (binær) og motsatt, fordi et hex-tall utgjør ½ byte, altså 4 bits. 
For å telle på hex, teller man som vanlig, fra 0-9. Men når man når 10, bruker man bokstaven A. 11 blir B osv. Mer at vi stopper på 15, som er F i hex. 

For å gjøre om fra hex til bin og motsatt, kan man enkelt se på ett og ett siffer på hex-tallet, eller 4 og 4 bits på det binære. Så kan man legge sammen og det er det. 
Har vi f.eks. tallet 1F45 (8005 på desimal), ser vi først på 1. I binært er det 0001 (med fire sifre). F, 15 på desimal, blir 1111, 4 er 0100 og 5 er 0101. Dermed blir 1F45 i binært lik 0001 1111 0100 0101. 

 ![Hex-tabell](bilder/hex_tall.PNG)

På samme måte som vi representerer binært med 0b foran, er det vanlig å representere hex med 0x foran. Vi kan da skrive f.eks. 0x1f45 = 0b0001111101000101. 

I CTF er det en stor fordel å ha disse kunnskapene. Men det er ikke nødvendigvis at man gidder å sette seg ned og skrive hva som er hva. Derfor er det vanlig, og helt lov, å bruke kalkulatorer på internett hvis man får sånne oppgaver som det her. 

Merk at man kan, i teorien, bruke hva slags tellesystem man ønsker. Bin, desimal og hex er de mest vanlige, men det er fint mulig å treffe for octa (8-tallssystemet) og mange andre varianter. 

## ASCII
http://cactus.io/tutorials/web/what-is-an-ascii-code
ASCII (American Standard Code for Information Interchange) er et standardisert alfabet som forteller hvordan vi går over fra tall til bokstaver og tegn. Som nevnt, jobber datamaskiner kun med binære tall, men for at vi skal kunne tolke hva som står, er vi nødt til å ha en standard for å forstå hvilke binære tall som kan bli til hva slags bokstaver, desimale tall og andre tegn. 

Det originale ASCII-alfabetet ble laget på 8 bits, men kun 7 ble brukt i alfabetet. Den åttende bitten ble brukt til _error korrigering_, noe vi ikke skal gå inn på her. Det betyr at det kun er 128 mulige tegn man kan lage med det originale ASCII-alfabetet. Det inkluderte altså ikke mange forskjellige tegn, blant annet “æ”, “ø” og “å”.
Senere har det kommet “extended ASCII”, der alle 8 bitsene brukes, som inkluderer mange flere tegn (256 kombinasjoner). 

Det dette betyr, er at når man trykker en knapp på tastaturet, får datamaskinen en kommando, representert med bits, så vi den oversette til ASCII og forstå hva som skal skje. Trykker man f.eks. _backspace_-knappen, tolker datamaskinen dette som tallet 8 i desimal, 0b00001000 eller 0x08. “CTF” blir til 0x43 54 46 (i hex, se “0x”). Slik oversettes altså 1 og 0 i datamaskinen til bokstaver og tegn som vi kan lese. 


## Vanlig måte å representere bokstaver
I kryptografi, og spesielt i CTF, er det noen ganger vanlig å representere bokstaver via tall på en enklere måte. Vi kan kalle A for 0 eller 1, B for 2, C for 3 osv. Dette skaper en rimelig og intiuitiv representasjon på bokstaver. I de fleste former for kryptografi, er dette den absolutt vanligste måten å representere bokstaver på. Grunnen til det, er at vi kan kryptere, ved å f.eks. plusse tall sammen, slik at man får et nytt tall. (Se Ceasar Cipher).

 ![Bokstaver som tall](bilder/bokstaver_som_tall.jpg)

 Generelt når vi skal plusse sammen bokstaver, kan det være gunstig å bruke en lik tabell:

![Alfabetmatrise](bilder/alfabetmatrise.PNG)

Her kan vi tenke at hvor bokstav på toppen, er klarteksten og for hver bokstav nedover, på venstre siden har vi plusset på et tall. F.eks. dersom vi har "C" som klartekst og skal plusse på 2, går vi ned til "C" ("A"=0) på venstresiden og ser hva vi får i midten, altså "E".

## Modulær aritmetikk
Modulær aritmetikk er et stort fagområde. (Kan nok ikke gå alt for mye i dybden her.) Det viktigste å huske på i modulær aritmetikk, er at i stedenfor en vanlig tallinje, har vi en sirkulær tallinje, litt som en klokke. Dersom vi operer i _modulo 5_, kan vi kun få tall mellom 0 og 4. Da kan det være hjelpsomt å se for seg en klokke der 0 (og 5) er tallene som er rett opp (klokka 12 på vanlige klokker). 

 ![Modulo 5](bilder/mod5.PNG)

Noen viktige prinsipper: 
- Hvis vi skriver på måten "a mod n = z", kan vi da si at a er tallet vi ser på, n, er hva slags "klokke" vi opererer i og z er tallet vi får ut etter å ha tatt a steg i klokka. 
- 3 mod5 = 3, fordi vi begynner på 0, går tre steg fram og havner på 3.
- 5 mod5 = 0. Vi ser da at vi har gått en hel runde rundt og havna på 0 igjen
- 6 mod5 = 1, fordi klokka vår har gått en hel runde rundt og havna på 1 igjen. 
- 17 mod5 = 2 fordi vi går 3 ganger rundt klokka og 2 steg til. 
- 300 mod3 = 0. Her går vi rett og slett 100 ganger rundt klokka.
- En fin observasjon å ha er at hvis a er delelig med n, altså at "a er i n-gangen", får vi 0 uanett.
- Vi kan da og se at -1 mod5 = 4, fordi vi har gått ett steg bakover i klokka og havnet på 4.  

Når vi bruker det engelske alfabetet, opererer vi i modulo 26 (26 bokstaver i det engelske alfabetet). NB! Her er det viktig å skille mellom om vi bruker A=1 eller A=0. Dersom vi skal bruke modulær aritmetikk i utregningen, er A nødt til å være 0 for at dette skal vi mening. Husk derfor å ha dette i tankene. Dersom vi bruker notasjonen med A=1, kan vi ikke direkte regne med modulær aritmetikk. 
Det vanligste er fortsatt å bruke notasjonen med A=1, B=2, osv. Dette er hovedsakelig snakk om når vi bruker _Ceasar Cipher_. 

### picoCTF oppg. 1 Crypto
For å begynne, kan vi se på en CTF med en gang. Denne CTF'en calles picoCTF. Mer spesifikt, er denne fra 2019. Oppgavene er åpne og CTF'en er generelt veldig bra. Den fungerer som et interaktivt spill med en bakgrunnshistorie, der jobben din er å "hacke" forskjellige PC'er. (Jeg har egentlig ikke fulgt med på historien, men er noe i den duren). I picoCTF kan man velge mange forskjellige oppgaver og vi skal her se på noen som handler om kryptografi. 

I første oppgave, får vi beskjed om at flagget er på formatet "PICOCTF{}". Vi laster ned et bilde og ser mange tall (alle under 26), med to klammeparenteser. Da er det logisk at ett tall representerer plassen til en bokstav i alfabetet. 

Tallrekken vi får er:
_16 9 3 15 3 20 6 {20 8 5 14 21 13 2 5 18 19 13 1 19 15 14}_

Ved oversettelsen får vi da:
PICOCTF{THENUMBERSMASON} ( "The numbers, Mason", en referanse fra Call of Duty: Black Ops)


### Invers modulo
Som inverse funksjoner, har vi og inverser i modulær aritmetikk. Kort fortalt et inversen til et tall, A, 1 delt på A, altså A<sup>-1</sup>. Det er fordi hvis vi ganger de to sammen, få vi 1. 
I modulær aritmetikk, er det flere måter å få 1 på, men den samme regelen gjelder fortsatt:
- A\*A<sup>-1</sup> = 1 mod n 
- eller, akkurat det samme: A\*A<sup>-1</sup> mod n = 1
Som vi vil se under "Greatest common divisor", er det kun tall som har gcd(A,n)=1 som kan ha inverser modulo n.
I modulær aritmetikk, kan A<sup>-1</sup> være helt vanlige tall, ettersom målet er å have på 1. 
eks:
- A=3, n=7
- Vi skriver det slik for å finne inversen: 
- Finn 3<sup>-1</sup>mod7
Med små tall er dette enkelt, fordi vi kan gjette oss fram. Målet er altså å finne et tall som, ganget med 3, gir 1 (mod7).
Vi kan prøve oss fram, og se at 5 ganget med 3 gir 15, som er 1 mod 7.
- 3<sup>-1</sup>mod7 = 5

For å finne inversen på større tall, blir vi nødt til å bruke "Kinesiske restteorem". (Eller søke på nettet, noe som er mer vanlig i CTF).


## Tallteori i PKC (Public Key Cryptography)

Ved bruken av PKC, er vi helt avhengige av å bruke matematiske teorier som gjør det "umulig" (_unfeasible_) for datamaskiner å gjette seg fram til hva den hemmelige nøkkelen er. 

### Greatest Common Divisor
Greatest Common Divisor (GCD) er det vi på norsk kaller "Største felles multiplum". Dersom vi har to tall, x og y, er GCD av x og y (GCD(x,y)), det største tallet som er delelig med begge to. F.eks. x=5, y=10, GCD(5,10)=5, fordi 5 deler 5 og 5 deler 10. GCD(120, 50) = 10. For å finne GCD, kan vi enten bruke kalkulator, men matematikken i det, sier at vi faktoriserer tallene og slår sammen alle felles faktorer. 
- For x=120, y=50: 
- 120 = 12\*10 = 2\*6\*5\*2 = 2\*2\*3\*5\*2
- 50 = 5\*10=2\*5\*5
- Vi ser at vi har én 2'er og én 5'er felles. Ganger vi de sammen, får vi 10. Altså GCD(120,50)=10.

Dersom vi har to tall der GCD(x, y)=1, kaller vi disse to tallene for _relativt primske_. Det betyr ikke at tallene i seg selv er primtall, men bare at de ikke har noen felles faktorer. Dersom vi har skal finne GCD av to primtall, vil dette alltid være 1. F.eks. gcd(33,25)=1, men hverken 33 eller 25 er primtall. 

### Kinesiske restteorem
Denne brukes for å finne GCD mellom to tall. Går ikke inn i dybden her på hvordan man gjør dette for hånd, ettersom vi hovedsakelig bruker kalkulatorer på nettet for å gjøre dette i CTF.

### Eulers funksjon
Eulers funksjon av et tall, n, skriver vi som phi(n). Tallet som kommer ut kalles _Eulers totient_. Det betegner antall tall mindre enn 5 som er relativt primske til tallet n, altså at gcd(n, x)=1 for et tall, x, mindre enn n. F.eks. phi(10) = 4. Fordi det er fire tall som er mindre enn 10 og er relativt primske med 10. Disse tallene er 1, 3, 7 og 9. Alle andre tallene under 10 deler en felles faktor med 10 (eller 2 og 5, siden 10=2\*5). Noen viktige prinsipper for phi(n):
- phi(p) = p-1 for et primtall, p. Det betyr at alle tall som er mindre enn et primtall, p, er relativt primske med primtallet. 
- phi(p\*q) = (p-1)(q-1) for to forskjellige primtall, p og q. 
- - eks. phi(15) = phi(3\*5) = (3-1)(5-1) = 2\*4 = 8
- Dersom n er satt sammen av flere enn 2 primtall, ser funksjonen litt annerledes ut. Vi finner alle primtallene. For hvert forskjellige primtall, fjerner vi ett av dem. Deretter ganger vi det med primtallet - 1.
- - eks. phi(24) = phi (6\*4) = phi(2\*3\*2\*2) = phi(2<sup>3</sup>\*3<sup>1</sup>). Vi har to forskjellige primtall her, 2 og 3. Vi har tre 2'ere og én 3'er. Vi får altså (2<sup>2-1</sup>(2-1)) \* (3<sup>1-1</sup>(3-1)) = 2<sup>2</sup>\*1\*3<sup>0</sup>\*2 = 4\*1\*1\*2 = 8

Eulers funksjon er svært essensiell i mange former for PKC, spesielt RSA. 
Vi finner og to viktige teoremer:
- Eulers teorem: 
  - a<sup>phi(n)</sup>mod n= 1, hvis gcd(a,n) = 1
- Dersom n er et primtall, p, husker vi at Eulers funksjon gir phi(p) = p-1. Dette gir oss Fermats teoriem
- Fermats teorem: 
  - a<sup>p-1</sup>mod p= 1

Grunnen til at primtall er viktig innenfor kryptering er det vi kaller _Discrete Logarithm Problem_ (DLP). Dette er et problem som er svært vanskelig (_unfeasible_) for maskiner å løse. Det ser sånn her ut: 
- Gitt et heltalltall, y, en base, b, og et primtall, p. Finn en x slik at:
- y = g<sup>x</sup>mod p
Det å finne denne x'en er unfeasible dersom p er et ekstremt stort primtall. Det er dette som er kjernen bak sikkerheten i PKC. 



