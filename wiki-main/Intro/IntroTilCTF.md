# Introduksjon til CTF

<!-- TODO: Skrive mer detaljert om de forskjellige temaene innenfor CTF-->

Capture the Flag (CTF) er en informasjonssikkerhetskonkurranse der deltakernes mål er å få tak i en “hemmelig” kode/tekst, altså flagget, som bevisst er gjemt av de som har laget konkurransen. En CTF-konkurranse kan på mange måter sammenliknes med en rebus, der man, sakte men sikkert, løser forskjellige gåter og til slutt når et mål. 
Hvordan flagget ser ut og hvordan det er gjemt varierer i stor grad i hva slags CTF-konkurranse det er man har gitt seg ut på. Forskjellige teknikker og verktøy kreves for de forskjellige konkurransene. Det er vanlig å jobbe sammen i team for å løse disse oppgavene. 

## Hacking

Uavhengig av de forskjellige formene for CTF som finnes, er det en fellesnevner som kreves: hacking. 
Å hacke betyr å jobbe seg rundt begrensninger og utnytte et system på en måte det ikke er ment å fungere. Det kan f.eks. være ved å sende en mail som har et virus vedlagt, skjult som et ufarlig vedlegg, der mottakeren av mailen uvitende laster ned viruset. Hacking kan og være ufarlig, slik som å endre på fargen på en nettside som du egentlig ikke skal ha tilgang til.


## Hvem vil hacke?

Det finnes mange grunner til at en hacker gjør det han/hun gjør. De vanligste insentivene til en hacker er: økonomisk gevinst, spionasje, sabotering, mestringsfølelse / for moro skyld, tyveri, kontroll eller rett og slett “fordi man kan”. 

Hacking kan altså medføre store konsekvenser for alt fra enkeltpersoner til hele nasjoner. Dermed kan det være naturlig å stille seg spørsmålet: hvorfor lærer vi å hacke? 
En måte å tenke på her er at for å forstå hvordan vi skal forsvare vår digitale infrastruktur, er vi nødt til å forstå hvordan angriperne opererer. På et lavt nivå kan dette være hvordan man håndterer sine egne passord slik at de ikke kommer på avveie og noen andre får tak i disse. Da ville i så fall personen som har fått tak i passordene dine ha muligheten til å hacke deg på forskjellige måter. På den andre siden av spekteret kan vi se hvordan store organisasjoner som f.eks. Stortinget og Hydro (lenke til deres hackeangrep) har fokusert for lite på sin digitale infrastruktur eller interne rutiner, hvilket har medført til at de har blitt utsatt for store angrep. Det å hacke for å finne _sårbarheter_ og tette hullene før angriperne finner dem, kalles etisk hacking. Det vil si at man hacker med gode intensjoner i trygge rammer og sørger for å ikke gjøre noe skade for noen. 

For å separere på hva slags hackere som finnes bruker vi terminologien “script kiddies”, “white hat hackers”, “grey hat hackers” og “black hat hackers”. For å forstå disse begrepene enklere, skal vi bruke en analogi der vi kan se for oss hacking som hvordan man kan bryte seg inn i et hus. Huset kan da sees på som den digitale infrastrukturen, og alle mulige måter å komme seg inn i huset, er en måte å få _uautorisert tilgang_ på. 

Script kiddies er hackere som i stor grad er ufarlige. Det er personer som kan ha funnet et _“script”_ på nettet og ønsker å se hvordan det fungerer. Her vil insentivene hovedsakelig basere seg på spenning og mestringsfølelse. Eksempler her kan være at man har sett at det finnes et dataprogram som kan få en nettside til å stenge ved å sende veldig mange innloggingsforsøk eller forespørsler på en gang. Dette kalles et _DDOS-angrep_ (Distributed Denial of Service) og medfører at nettsiden lukkes for en liten stund og ingen får tilgang til den. For å avverge et slikt angrep, er det dermed nødvendig at de som har utviklet nettsiden innfører tiltak som sørger for at man ikke kan logge inn x antall ganger i sekundet og krasje nettsiden. 
Ved analogien om å bryte seg inn i et hus, vil script kiddies kanskje se om det er et vindu åpent på huset, eller finne utstyr som kan dirke opp en lås. De vil ikke bryte seg inn i huset, men heller kjøpe en egen hengelås for så å øve seg på å dirke opp den. 

White hat hackere er hackere som driver med etisk hacking. De er ansatt av bedrifter og gjør dette som en vanlig jobb. White hats har mye IT-kompetanse og må forstå hvordan den digitale infrastrukturen ser ut. De må og ha evnene til å tenke som en angriper for å finne alle mulige måter å _utnytte_ et system på. 
White hats kan altså jobbe i f.eks. et konsulenthus. Da vil en klient/en annen bedrift ansette disse hackerne som, i trygge rammer, gjør det de kan for å teste klientens digitale infrastruktur. Etter at de har gjort det, leverer de en rapport som forteller hva de har funnet og hvordan man kan utbedre feilene.
White hat hackere får altså lov til å gjøre alt de kan for å bryte seg inn i huset. De har inngått en avtale med huseier og  skal gjøre det de kan for å komme seg inn i huset. De dirker låser, klatrer gjennom vinduer, hopper ned piper og alt annet man kan gjøre. White hatsene gjør ikke noe skade når de først er inni huset, men forteller huseierne hvordan de kom seg inn og hvordan de skal sørge for at ikke andre kan bryte seg inn i huset. 
De store konsulenthusene som fokuserer på digital sikkerhet på denne måten har gjerne også en “SOC” (Security Operation Center). Det er et stort rom med masse dataskjermer, nesten som man ser på film, som kan overvåke diverse datapakker til klientene. Dermed kan de se, fra avstand, om de finner noe som kan se ut som et angrep og avverge det før det er for sent. 

Grey hat hackere er hackere som jobber i gråsonen. Som oftest er ikke disse heller ute etter å gjøre ugang, men de jobber ikke med en bedrift. I motsetning til white hats, jobber ikke disse i en bedrift som hjelper med utbedre feil. De jobber gjerne selvstendig og prøver å finne sårbarheter i forskjellige digitale systemer for så å ta betalt for å si hvordan de utnyttet sårbarheten og hvordan man skal fikse det. 
Grey hats vil altså bryte seg inn i huset ditt, eller i alle fall dirke opp låsen, for så å be deg om penger for å fortelle deg om hvordan de gjorde det. Her begynner man å bevege seg vel over på grensen av det som er lovlig. Større andeler av grey hat hacking er ulovlig og kan straffes med fengsel. <!--TODO: (Lenke til straffelovens paragraf 201. mm.)-->


Black hat hackere er hackere som jobber med ondsinnede intensjoner. Deres insentiver er alle de overnevnte. Black hats bryter seg inn i datasystemer, stjeler passord, sletter informasjon og det som verre er. Ofte vil black hats bryte seg inn i datasystemer og hindre brukerne tilgang til systemene. Dette har enorme konsekvenser og skjer dessverre ofte i dag. Angrepet på Hydro og Coop er eksempler på store hackeangrep der hackerne har fått uautorisert tilgang, krypterer all informasjonen og gjør den utilgjengelig for så å kreve store summer penger for å gi tilbake tilgangen. Black hats kan og f.eks. få tilgang til kontoer på sosiale medier og enten bedrive identitetstyveri for å krenke den hackede, eller kreve løsepenger for å gi tilbake informasjon <!--Eventuell TODO: (Lenke til Fredrik Solvangs hack)?.--> Black hats kan og jobbe i team i hackegrupper på det mørke nettet. 


### Hacking og CTF
I CTF-konkurranser er det bevisst lagt ut sårbarheter som deltakerne av konkurranse skal finne og utnytte. I de aller simpleste formene for CTF, er det ikke nødvendigvis hacking som skal til for å finne flagget, men heller noen simple kommandoer i terminalen som skal til for å åpne riktige mapper og orientere seg til flagget. 

CTF-konkurranser blir ofte laget av store aktører som Google og PST, men kan og bli laget av mindre aktører. De store aktørene lager disse konkurransene og lager den gjerne såpass vanskelig at det teamet som først finner alle flaggene kan få pengepremier eller jobbtilbud. 

Det finnes altså forskjellige forskjellige "øvelser" innenfor CTF-konkurranser. De aller vanligste er “Binary exploitation”, “Cryptography”, “Web exploitation”, “Reverse engineering” og “Forensics”. 

I eksemplene som gåes gjennom, vil jeg hente oppgaver fra OverTheWire sin "Bandit" CTF og picoCTF2019 sin CTF. 

#### Binary exploitation
_"Binaries"_ eller "_executables_" er filer med kode som datamaskinen skal utføre. Her blir jobben din å finne små feil eller hint som er lagt ut. Det kan enten være hvordan kodne blir utført, eller det kan være at du skal endre noe på koden for at den skal bli utført annerledes.

### Forensics

