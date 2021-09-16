# Terminalen
 Før vi begynner med hackingen, er det nødvendig å vite hva en "terminal" er. En terminal er et grensesnitt, altså noe du som person kan interagere med. I terminalen så kjører man en software som kalles et "shell". Her finnes det forsakjellige varianter men de vanlige er "Bourne Shell" og "Bourne Again Shell" (her brukes for det meste forkortelsen "Bash"). En terminal kjører altså et "shell". De som har Linux eller Mac som operativsystem på PC'en, bruker samme språk i terminalen. Det er fordi de begge er basert på det som heter Unix. Windows PC'er bruker ofte shellet som heter "PowerShell", fordi Windows er basert på MS-DOS. Ved standardkonfigureringer, bruker altså Linux og Mac det samme språket i terminalen, mens Windows ser litt annerledes ut. Forskjellene der er litt som i norsk og svensk. Problemet er bare det at kommandoene du setter inn må være korrekte. Dersom du skriver noe til maskinen som den ikke forstår, vil den si fra om det. 

## Linux
(Network Chuck)

 Det er viktig å presisere at for å begynne med hacking og CTF, er det ikke nødvendig å jobbe med Linux, men det anbefales på det sterkeste. Hovedgrunnen til det er at Linux er _open source_, noe som betyr at alle kan hjelpe til med å lage operativsystemer innenfor Linux. Linux er altså ikke et operativsystem i seg selv, men det som kalles en _kernel_. Det du trenger å vite om en _kernel_, er at en _kernel_ snakker med hardwaren på PC'en din, altså de fysiske delene. Operativsystemene som kjører på Linux, er de hvem som helst kan lage, til mange forskjellige hensikter. Det er f.eks. vanlig å bruke operativsystemet som heter _Kali Linux_ i mange tilfeller hvor man skal hacke eller drive med CTF. Andre vanlige Linux operativsystemer er _Debian_, _Ubuntu_, _unix_ m.m.

## Første møtet med terminalen

  Først og fremst; hvordan åpne terminalvinduet? (Her finnes det mange forskjellige måter, dette er kun sånn jeg finner det enklest.)

 - For Windows: 
    - "windows"+"r" -> "cmd"
    - Hold inne windows-knappen (den mellom "Alt" og "Ctrl"), samtidig som du trykker på "r". Da vil det dukke opp en liten "søkeboks". Her vil du skrive inn "cmd" og trykke enter. Da vil terminalvinduet ditt dukke opp. Terminalvinduet i Windows heter "Command Prompt". 
 - For Mac: 
   - "Cmd"+"space" -> "terminal
   - Hold inne "Cmd" og trykk på "space". Da vil du få et søkefelt. Skriv da inn "terminal" og trykk "enter". 
 - For Linux:
   - "ctrl"+"alt"+"T"
   -  Her ligger den ofte på skrivebordet allerede, da er det bare å åpne den ved å trykke på ikonet.

Herfra vil eksemplene jeg kommer med være fra en Linux-maskin. Det er, som sagt, de samme kommandoene man bruker som på Mac, så språket blir det samme. Det er vanlig å jobbe med Linuxmaskiner både på NTNU og ellers i CTF. Det finnes en variant av Linux som heter "Kali Linux". Dette operativsystemet er vanlig å bruke innenfor hacking, hovedsakelig fordi det kommer med mange innebygde programmer som er kjekke å ha i CTF. Det er Kali Linux jeg bruker i eksemplene nedenfor, men for andre Linux og Mac brukere, blir språket det samme.

 Når jeg åpner terminalvinduet, er det en sort/gjennomsiktig boks med teksten:
 ```bash
 mathias@kali:~$ 
 ``` 
 Her er "mathias" navnet på brukeren på PC'en. "kali" er navnet på datamaskinen. Etter kolon-tegnet ser vi hvilken  mappe (_directory_) vi er i. Her ser vi et "tilde"-tegn (~). Det representerer "Home Directory", altså hjemme-mappa, for brukeren du er på. Det er det samme som /home/username, eller /home/mathias, for min del. Helt på slutten ser vi et dollartegn. Dette betyr at du er logget inn som en bruker. Det er nesten alltid tilfelle, men det finnes ett unntak. Når man er logget inn som _root_. _root_ skal vi komme tilbake til senere, men enn så lenge kan du tenke at _root_ er sjefen av datamaskinen. _root_ har tilgang til alle mapper og kan slette eller legge til alle mulige brukere. 
_root_-brukeren har med andre ord fullstendig kontroll over maskinen. Dersom man er logget inn som _root_, har man en "hastag" (#) i stedet for dollartegn ($). Er du logget inn som _root_, kan det se sånn her ut: 

```bash
 root@kali:~# 
 ``` 

## Tips og triks i terminalen

I terminalen og når du skriver i et shell-program, er ting litt anneledes i begynnelsen. Derfor kan det være å ha noen tips til å starte med. 
- Den første delen av det du skriver er kommandoen, altså hva du skal gjøre. Avhengig av kommandoen, kan ting se forskjellig ut heretter. Det vanligste er å ha kommandoen først, etterfulgt med hvor/hva. Deretter kan det gjerne komme det som kalles "flag". (Ikke til å forveksle med flag i CTF). Et flag er en ekstra detalj som du kan legge til for å få kommandoen til å kjøre annerledes enn standard. F.eks. er det vanlig å skrive en kommando, etterfulgt av mellomrom, så _-v_, _--v_ eller _--version_ for å se hvilken versjon av kommandoen du kjører. Flaggene for en kommando og hva de gjør kan sees ved bruk av _man_-kommandoen, som vi kommer til senere. 
- Hvis du ser at du har skrevet noe feil i en kommando og den ikke fungerer, kan du trykke pil opp. Dette henter den siste kommandoen du skrev. Pil opp igjen henter den før der, osv. For å slette noe i kommandoen, må du bevege deg bort med piltastene og slette derfra. I terminalen blir markøren lagt "oppå" ett og ett tegn. Backspace-knappen sletter det som er bak der markøren er. Delete-knappen sletter det som er foran. 
- Hvis du skriver en kommando, f.eks. _cd_ og skal inn i en mappe, kan du begynne å skrive mappen, for så å trykke "tab". Da vil det automatisk bli skrevet ferdig, så langt det lar seg gjøre. 
- Når du skal kopiere og lime ting, er det greit å markere med musen. Men det fungerer ofte best å høyreklikke og kopiere, så høyreklikke og lime inn, i stedet for den vanlige ctr/cmd+c og ctr/cmd+v. 
- Stjernetegnet (*), kalles et _wildcard_. Man kan bruke * som en benevning på "alt". Hvis man f.eks. skal åpne alle mappene i en fil man er i, kan man skrive "cat ./*". Hvorfor dette fungerer, kommer vi til senere. 

(Her kan du begynne å lese på "Terminalkommandoer")


## Linux fil-hierarki

(Her kan det være lurt å ha lest deler at "Terminalkommandoer").

 Linux er basert på et _filsystem_. Det betyr at alt er på en eller annen måte en fil. Hvis du skal endre på brukere på PC'en, finner du det i en fil. Nettverkskonfigurasjoner: i en fil. Bilder du har lastet ned er filer. Til og med kommandoene vi bruker er filer. Derfor er det greit å vite hvordan filsystemet ser ut. 

 (Bilde av fil-hierarkiet)
 ![Hierarkiet i Linux](bilder/linuxDirHierarchy.jpg)

Fra "Terminalkommandoer har vi for det meste operert i /home/-mappa. Bildet over gir en oversikt over diverse filer og hva de inneholder. Vi skal nå se litt på noen av disse.

### bin
_bin_ står for "binaries". Det er filer som ikke er leselig for mennesker, men for datamaskinen. Ved å ha slike filer, kan datamaskinen f.eks. utføre kommandoer. Så det _bin_ inneholder er de mest essensielle kommandoene vi bruker, som f.eks. _ls_. Det betyr at når vi bruker _ls_-kommandoen, henter vi egentlig bin-filen til _ls_. Med de kommandoene vi har lært fra "Terminalkommandoer", kan vi altså gjøre noe kult:

![Kopi av ls](bilder/kopi_av_ls.PNG)

Det jeg har gjort her er å gå inn i _bin_, kopiert _ls_-filen og kalt den _mathiassinls_. Ved å gjøre det kan jeg faktisk bruke den nye kommandoen _mathiassinls_ til å liste innhold i mapper. Merk at dette ikke egentlig er så lurt å gjøre. Ting som er i _bin_ kan være greit å la være.
Merk at vi her trenger _sudo_. 

### sbin
_sbin_ er for det meste det samme som _bin_, nemlig binary-filer. Forskjellen er at _sbin_ inneholder filer som kun administratorer skal ha tilgang til. Det kan være f.eks. å legge til brukere, ved kommandoen _adduser_.

### usr
Denne mappen inneholder kommandoer som brukerene kan kjøre. Det som er rart, er at i /usr, finner vi og _bin_ og _sbin_. /usr/bin og /usr/sbin inneholder nesten akkurat det samme. Grunnen til at vi har disse mappene er to forskjellige steder er hovedsakelig av historiske årsaker som vi ikke trenger å gå inn på. En mappe som er viktig, er /usr/local. Denne brukes til å lagre binary-filer som du selv kan lage. 

### boot, var, tmp og lib
Boot: filer maskinen trenger for å boote opp (starte opp).
Var: log-filer. Dersom man f.eks. prøver å bruke _sudo_-kommandoen uten å være sudo-bruker, kommer det informasjon om at det blir rapportert. Det er ikke farlig men blir lagret her.
tmp: filer som blir slettet, ved f.eks. en reboot.
lib: viktige filer som andre kommandoer og prosesser trenger for å fungere som de skal.

### home
Dette er hjem-mappa til alle brukere. Vi har sett hvordan tilde-tegnet (~), representerer hjem mappa til en bruker. Som nevnt, er det det samme som /home/mathias, siden jeg har vært logget inn på mathias. Ved å legge til brukere, finner vi de andre brukerne sitt "hjem" under denne mappa. 

![adduser](bilder/adduser_eksempel.PNG)

Når man legger til en bruker, ser vi altså at brukeren får en _group_ (1001 i dette tilfellet). Dette kommer vi tilbake til senere. Samtidig står det 1001 i parentes bak navnet på den nye brukeren, ("mathias2" (1001)). Det er brukerID'en til den nye brukeren. Vi ser og hvordan det blir opprettet et _home_-directory for den nye brukeren. Man trenger ikke fylle inn informasjonen om rom-nummer osv, bare trykk enter og hopp over det. 

Selv om vi ikke ser det på bildet av hierarkiet, er det og en mappe der som heter _root_. Dette er hjem-mappa til _root_-profilen. _root_-profilen ønsker vi egentlig å holde oss litt unna, fordi det er fort gjort å slette/endre filer som datamaskinen må ha for å fungere. 

### etc
Denne mappen inneholder konfigurasjoner til datamaskinen, som f.eks. nettverkskonfigurasjoner. Det er og noen andre aplikasjoner i denne mappa. I _etc_ har vi en mappe som heter _network_. I den igjen finner vi _interfaces_. Denne er vanlig å endre på dersom det er ting ved internettkonfigurasjonene dine du vil endre på. 

### mnt og media
Disse brukes for å "mounte" drives på maskinen din. Det betyr at når man f.eks. setter inn en USB-pinne i maskinen, er det _media_ som registrerer og sørger for at det går i orden. _mnt_ er det samme som _media_ men det velger man manuelt å mounte drivesene. 

### dev
Denne mappa inneholder "device files". I motsetning til vanlige filer, er dette filer som snakker med en driver i kernelen, som igjen snakker med en "hardware device", derav navnet "device". Det er her vi finner filene _stdin_, _stdout_ og _stderr_. Videre finnes det en fil her, som man ikke kan bruke _ls_ for å finne som går under navnet _/dev/null_. Dette er Det spennende med denne mappa, er at å skrive til den gjør ingen verdens ting, og å lese fra den gir ingen output. Dermed fungerer _/dev/null_ som en intens søppelbøtte. Den har ofte en hensikt ved at man kan filtrere mellom _stdout_ og _stderr_, som begge er former for output. Dersom man f.eks. prøver å bruke kommandoer som returner tonnevis med feilmeldinger, kan man legge til kommandoen 2>/dev/null for å filtrere bort alle feilmeldingene. Se eksempel under "Terminalkommandoer"-> "Bandit5". Mer om det kommer nå. 


## Pipe

https://www.howtogeek.com/435903/what-are-stdin-stdout-and-stderr-on-linux/

Vi har så vidt vært innom _stdin_ og _stdout_. I terminalen, eller mer nøyaktiv, i et shell, består kommandoene våre av det som kalles en stream. En stream (eller "strøm" på norsk, tenk en vannstrøm), har to åpninger. En inngang og en utgang. I bash (shellet vi bruker i Unix systemer), har vi egentlig en inngang (stdin), og to utganger (stdout) og (stderror). _stdin_ (standard input) er det shellet tar inn, som vi har skrevet. _stdout_ (standard output) er det shellet spytter ut, som vi ser som tekst på skjermen. Når vi skriver kommandoer i terminalen, er det shellet som tolker kommandoene. Når vi skriver en kommando, f.eks. _ls_, sender vi den til _stdin_, som vi da har sett utfører in binary-fil i /usr/bin, også spytter den up innholdet i mappa til oss som _stdout_. Dersom man prøver på noe man ikke får lov til, blir det spyttet ut som _stderr_ (standard error). Disse mappene er såpass viktige at de har fått egne tall assosiert med seg:
- 0: stdin
- 1: stdout
- 2: stderr

Vi ser dermed hvordan kommandoen _2>/dev/null_ markerer at all som kommer ut fra _stderr_ skal til vår intense søppelbøtte _/dev/null_. Det er dette som kalles "pipe" (som i "rør" på engelsk). Vi ser altså hvordan pilen tvinger en _stdout_ som _stdin_ til en annen fil. Dersom vi ønsker å bruke flere kommandoer samtidig, er dette også helt mulig. I stedet for å bruke pil, bruker vi da "|". 

![echo med pipe](bilder/echo_pipe.PNG)
Vi ser her hvordan echo først sender _stdout_ til displayet, i tekst, sånn at vi kan lese det. Dersom vi piper den inn i en tekstfil, får vi _stdout_ fra echo kommandoen som _stdin_ i tekstfilen.

Piping kan være ekstremt hjelpsomt i noen situasjoner. F.eks. blir kommandoen _grep_ (se "grep" i "Terminalkommandoer") gjerne brukt i kombinasjon av en _stdout_. 