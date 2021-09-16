# Nettside og URL
(https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL). En _webpage_ er en samling av flere _websites_. (Vanskelig å finne norsk oversettelse). 
En nettside er hva vi kan nå ved å skrive inn en _URL_  (Uniform Resource Locator) i en nettleser(/browser) (Chrome, Safari, Firefox, osv.). En _URL_ kan se slik ut: 
"https://www.eksempelnavn.no:443/path/til/minfil.html?key1=value1&key2=value2#etstedidokumentet
 En _URL_ er bygget opp av: 
- "Scheme": eks "https"
- Domenenavn: eks "www.eksempelnavn.no"
- Port: eks "443"
- (Domenenavn og port sammen kalles "Authority" (autoritet)). 
- Path til fil: "path/til/minfil.html"
- Parameter: "?key1=value1&key2=value2"
- Anchor (anker): "#etstedidokumentet"

Et tips er å se på en URL som noen sin adresse når du skal sende et brev: _scheme_ er hvilken posttjeneste du vil bruke, domenenavn er by, _port_ er postkode, _path_ er bygningen brevet skal til, _parametre_ er ekstrainformasjon som leilighetsnummer og _anchor_ er navnet på personen brevet skal til. 

_Scheme_ sier altså hvilken protoll vi bruker. I eksempel er det "HTTPS" (Hypertext Transfer Protocol w/ SSL). 
_Authority_ sier hvem sin server du skal bruke. Dette er egentlig en IP-adresse, men en DNS-server oversetter dette for oss. _Port_ sier noe om hvilke ressurser web-serveren skal bruke. Det er ofte ikke nødvendig å ha med, fordi det er gitt under _scheme_. HTTP bruker f.eks. port 80 og HTTPS bruker port 443. _Path_ forteller stien til dokumentet vi ønsker å hente. _Parametre_ er en ekstra liste med verdier, separert med "&" som web-serveren kan gjøre forskjellige ting med. Det er også denne delen av _URL'en_ som kalles en "Query". _Anchor_ er et spesifikt sted på en website. Altså scrollet ned en plass osv. 

En nettside er skrevet i _HTML_ (Hypertext Markup Language). Det er et programmeringsspråk, så det krever litt forståelse av hvordan syntaxen ser ut. For å få _HTML_-outputtet til å se annerledes ut, brukes CSS. Så det vi altså ser på en nettside er HTML og CSS. For at vi skal kunne interagere med det vi ser, brukes JS (JavaScript). 

Vi sier at når du, som bruker, interagerer med en nettside, er du "client" (klient). Nettsiden (egentlig serveren der nettsiden "ligger") kalles en "host" (vert).