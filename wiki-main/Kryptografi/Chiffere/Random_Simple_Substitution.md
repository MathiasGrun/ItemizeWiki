# Random Simple Substitution Cipher

<!--TODO: Legge til bruken av terminologien, altså si hvordan kryptering/dekrypteringsfunksjonen ser ut osv-->

Nødvendig forkunskap: "Substitusjon og Ceasar Cipher", "ROT13" og "Intro"

I motsetning til _Ceasar Cipher_ og _ROT13_, er det ikke noe mønster i Random Simple Substitution Cipher. Det er altså ikke et "shifted alphabet", men alle bokstavene havner på en tilfeldig plass.  

Chiffer med ROT13:
- Alfabet 1: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
- Alfabet 2: N O P Q R S T U V W X Y Z A B C D E F G H I J K L M

Vi ser da at vi kan enkelt dekryptere ved å ha disse ovenfor hverandre. 

(Eksempel på) Random simple substitution cipher: 
- Alfabet : A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
- Nøkkel  : P H Q G I U M E A Y L N O F D X J K R C V S T Z W B

Vi kan se at "Heisann" blir til "Eiarpff". "H" har flyttet seg 3 plasser bakover (eller 23 framover), mens "e" har flyttet 4 framover. 

I _Random Simple Substitution Cipher_, er det ikke nødvendigvis noe mønster. A kan bli en B, en Y, en K, eller hva som helst annet, samtidig som en annen bokstav kan ha flyttet seg et annet antall ganger. Det betyr at nøkkelen vår har lengde 26 og er nemlig alfabetet vi subsidierer til. Den første bokstaven i nøkkelen vår sier hva A blir til. Den har 26 muligheter. Den neste bokstaven i nøkkelen sier hva B blir til, den har kun 25 muligheter, siden den som representerer A allerede har tatt en mulighet. Slik fortsetter det nedover. Vi får dermed 26 * 25 * 24 * ... *2 * 1 = 26! mulige forskjellige nøkler, så det å teste seg fram her er veldig vanskelig.

I begynnelsen kan man tenke at dette høres veldig trygt ut. Men slik er det faktisk ikke. Med dagens teknologi kan vi bruke _frekvensanalyse_ for å dekryptere et slikt chiffer, uten nøkkelen. Det baserer seg på at i det engelske språket er det noen bokstaver og ord som er vanligere enn andre, altså at det har høyere freksens (gjelder så klart og for det norske språket, men vi har brukt engelsk som eksempel og holder oss til det). Dersom vi har en lang tekst, som hele er kryptert på denne måten, kan vi (PC'en), telle alle bokstavene i teksten og gjette seg fram til hvilke bokstaver som blir til hva. Videre er det noen 2-bokstavsord som er mye vanligere enn andre og det samme med 3-bokstavsord (kan og kalles 2-gram og 3-gram). Hvis du f.eks. i en tekst kryptert med dette chifferet ser gjentakende ganger 3-grammet: "Kio". Dersom det dukker opp rimelig ofte, er det stor grunn til å tro at K blir til T, i blir til h og o blir til e. Det er fordi det vanligste 3-grammet i det engelske språket er ordet "The". 

## One time pad

<!--TODO: Skrive mer om OTP-->

_One time pad_ (OTP) er en av de absolutt tryggeste måtene å kryptere på. Det kommer på bekostning av at det er veldig kronglete å håndtere nøkkelen. OTP kan minne fungerer som Vigenère, men vi har ikke en kort nøkkel som brukes periodisk. Vi har derimot en nøkkel som må være like lang som hele teksten vi skal kryptere. Nøkkelen må og være helt tilfeldig. På denne måten er det helt umulig å finne en periode eller noe som helst mønster. OTP har blitt brukt mye gjennom den kalde krigen, ettersom den er umulig å dekryptere uten nøkkelen. 

OTP er ikke et Random Simple Substitution Cipher, fordi det ikke bruker ett alfabet, men det har mange likheter med det, som f.eks. at alle shiftene er helt tilfeldige. 