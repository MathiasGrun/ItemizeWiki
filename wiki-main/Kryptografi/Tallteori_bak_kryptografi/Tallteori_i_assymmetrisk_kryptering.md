# Tallteori i PKC (Public Key Cryptography)

Ved bruken av PKC, er vi helt avhengige av å bruke matematiske teorier som gjør det "umulig" (_unfeasible_) for datamaskiner å gjette seg fram til hva den hemmelige nøkkelen er. 

## Greatest Common Divisor
Greatest Common Divisor (GCD) er det vi på norsk kaller "Største felles multiplum". Dersom vi har to tall, x og y, er GCD av x og y (GCD(x,y)), det største tallet som er delelig med begge to. F.eks. x=5, y=10, GCD(5,10)=5, fordi 5 deler 5 og 5 deler 10. GCD(120, 50) = 10. For å finne GCD, kan vi enten bruke kalkulator, men matematikken i det, sier at vi faktoriserer tallene og slår sammen alle felles faktorer. 
- For x=120, y=50: 
- 120 = 12\*10 = 2\*6\*5\*2 = 2\*2\*3\*5\*2
- 50 = 5\*10=2\*5\*5
- Vi ser at vi har én 2'er og én 5'er felles. Ganger vi de sammen, får vi 10. Altså GCD(120,50)=10.

Dersom vi har to tall der GCD(x, y)=1, kaller vi disse to tallene for _relativt primske_. Det betyr ikke at tallene i seg selv er primtall, men bare at de ikke har noen felles faktorer. Dersom vi har skal finne GCD av to primtall, vil dette alltid være 1. F.eks. gcd(33,25)=1, men hverken 33 eller 25 er primtall. 

## Kinesiske restteorem
<!-- TODO: Vurdere om det trengs noe mer her-->
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