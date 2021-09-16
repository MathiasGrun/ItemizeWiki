### pwd (print working directory)

Du har nå greid å åpne et terminalvindu. Men hvordan vet du hvor du er? Den første kommandoen er da _pwd_. Bare skriv det og trykk enter. Når jeg trykker det, ser det slik ut:

```bash
 mathias@kali:~$ pwd
 /home/mathias 
 ``` 

 Det som dukker opp er /home/mathias, akkurat som antatt. Det er dette som kalles en _path_, eller sti. Det forteller altså veien til den mappa du er i. 

### whoami (who am i)

Vi vet hvor vi er, det kan og være greit å vite hvem vi er. Dette brukes ved kommandoen _whoami_.

```bash
 mathias@kali:~$ whoami
 mathias 
 ``` 
Flott, jeg har fått bekreftelse på at jeg er meg. I CTF kan denne kommandoen være hjelpsom dersom du f.eks. har kommet deg inn på en annen bruker og skal bekrefte at du har fått det til. 

### ls (list)
Det _ls_ gjør, er å liste opp alt som er i den mappen vi ser på. I dette eksempelet ser vi alle mappene som er i hjem-mappen min. (Husk at _~_ er det samme som /home/mathias i mitt tilfelle).

 ```bash
 mathias@kali:~$ ls
 ``` 

 ![ls eksempel](bilder\ls_eksempel.PNG)

Vi kan og se hva som er i mappene vi nå har sett, uten å bevege oss inn i dem. 
Dette gjøres slik (hvis vi vil se i _Downloads_-mappa): 

 ```bash
 mathias@kali:~$ ls Downloads
 ``` 

### cd (change directory)
Nå som vi vet hvilke andre mapper vi har i vårt "home directory" (~), kan vi bevege oss inn i de andre mappene. 

Vi gjør dette ved å bruke kommandoen _cd_ og velge hvilken mappe vi ønsker å bevege oss inn i. 

 ```bash
 mathias@kali:~$ cd Downloads 
 ``` 

![cd eksempel](bilder/cd_eksempel.PNG)

I eksempelet ser vi hvordan jeg har gått inn i _Downloads_-mappen, og brukt _ls_-kommandoen igjen for å se hva som er i _Downloads_. Her ser vi en annen mappe, ved navn _Mappe_i_Downloads_. Dette er altså en annen mappe (_directory_) som man kan navigere seg inn til. I den terminalen jeg bruker, kan vi og se at mapper (directories) er markert i blått.
Filen _capture.pcap_ er IKKE en mappe eller et directory og man kan da ikke bruke _cd_ for å komme deg inn i den. Det er fil av typen .pcap. Det er filer som er laget av programmet _Wireshark_. Det er et program som brukes mye innenfor flere studier på NTNU, samt innenfor CTF. Mer om _Wireshark_ senere. 
Prøver man å bruke _cd_ på noe som ikke er en mappe får man en feilmelding. _cd_ brukes altså for å bevege seg inn i mapper. Det gir ikke noe mening å prøve å bevege seg inn i pcap-filen. 

![Feil bruk av cd](bilder/feil_bruk_av_cd.PNG)

_cd_ brukes og for å gå tilbake. Ved å bruke _cd .._ beveger vi oss en mappe tilbake. I eksempelet ser vi at vi er i _Downloads_-mappa, bruker _cd .._ og havner tilbake til hjem-mappa. Vi kan og se hvordan kun _cd_-kommandoen, uten å skrive noe mer, fører oss tilbake til hjem-mappa. Legg og merke til at hvis vi bruker _cd .._ på nytt og nytt, kommer vi tilbake til root(/)-mappa. Herfra kommer vi ikke lenger. Vi kan også skrive _cd /_ for å komme til root-mappa.  

Hvis vi beveger oss inn i mappen som heter _Mappe_i_Downloads_, finner vi en tekstfil. Vi ser at det er en tekstfil, fordi den har _.txt_ bak seg. Vi husker så at det ikke går ann å bevege seg inn i filer ved _cd_, fordi det ikke er en mappe ("Not a directory").

### cat
Dersom vi ønsker å se innholdet i en fil, kan vi bruke commandoen _cat_. _Cat_ står for "cancatenate files and print on the standard output". Det betyr enkelt og greit "print ut det som står i filen". Hvis man prøver dette med et bilde eller andre filer som ikke enkelt lar seg skrive ut, kan man få et problem. Dette vil vi se senere. 

Noen ganger er det ikke helt enkelt å bruke _cat_. Hvis navnet på filen du prøver å åpne ser ut som noe som PC'en tror kan være en del av en kommando, får den vanskeligheter. Derfor bruker man gjerne et punktum og skråstrek etter _cat_, forran navnet på filen. Dette vil vi se et eksempel av senere, under gjennomføringen av _bandit1_. 
Grunnnen til at "./" fungerer er fordi "." referer til mappen vi befinner oss i. Man kan altså skrive _cat ./(navnpåfil)_ for å poengtere at vi skal åpne denne filen i denne mappen som vi befinner oss i. I de fleste tilfeller er dette overflødig, men kan være nyttig, av og til. 

 Man kan andre ganger bruker fnutter ("") rundt navnet på filen. Spesielt hvis det er mellomrom i et filnavn, blir dette nødvendig. 

Eksempler her kan være hvis det er mellomrom i navnet på en fil, eller hvis navnet på filen er et tegn og ikke en/flere bokstaver. 

![cat eksempel](bilder/cat_eksempel.PNG)

### man og whatis
En kommando som kan hjelpe deg mye, er kommandoen _man_. Dette står for "manual", og er en bruksanvisning til andre kommandoer. Ved å f.eks. skrive:

```bash
 mathias@kali:~$ man ls
 ``` 
får vi manualen til _ls_-kommandoen. Dette kan være veldig hjelpsomt når vi skal utnytte kommandoene for det fulle. Hvis ikke vi orker å se gjennom hele manualen til en kommando, kan vi bruke _whatis_. Denne skriver kun og hva kommandoen gjør og ikke noe særlig mer. Mer presist, skriver _whatis_ ut den første linja i _man_. Man kan ofte og bruke flagget -h eller --help etter en kommando for å få opp en hjelpemeny.

### sudo
Står for "super user do". Dette er en litt innviklet kommando. Kommandoen kan brukes før andre kommandoer der det trengs. Noen ganger når man skriver kommander i Linux, trenger man spesialtillatelse. Mange sammenlikner _sudo_ med å si "vær så snill". Det som skjer her, er at man "låner" privilegiene til _root_ for å gjennomføre kommandoer, som f.eks. å legge til/endre brukere eller fikse noen andre viktige konfigurasjoner. Se "Linux fil-hierarki" i "Terminalen" for å få mer kunnskap om _sudo_.


## ssh og intro til Bandit
Disse kommandoene, med noen flere tillegg, er de mest essensielle for basicen i alle CTF'er. Den siste kommandoen vi skal bruke for å begynne vår første CTF, heter _ssh_. _ssh_ står for "secure shell". Som fortalt tidligere, kjører vi et "shell" i en terminal. _ssh_ vil da åpne et shell, på en annen server, PC, bruker, eller hva det enn måtte være. Det å kunne opprette et shell et sted kan gi ekstremt mye makt. 

Ved bruk av _ssh_ er det vanlig å skrive det på formen "ssh <brukernavn>@<nettside/server/pc> <port (markert med -p og hvilken port) >. Vi går senere mer inn på hva en "port" er, men enn så lenge trenger du kun å vite at det er sånn her _ssh_-kommandoen vil se ut. 

_ssh_-kommandoen kan se følgene ut:

 ```bash
 mathias@kali:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
 ``` 

Her ser vi altså at jeg har brukt _ssh_, brukernavnet er _bandit0_, serveren/nettsiden er _bandit.labs.overthewire.org_ og porten vi skal bruke er 2220. 
Dette er fra en CTF som heter _Over The Wire_. (https://overthewire.org/wargames/bandit/bandit0.html) Den oppgaven vi skal se på i eksemplene, heter "bandit". Den er for nybegynnere og med kun de kommandoene vi har lært, kan vi løse noen av oppgavene.

Ved å skrive denne linjen i terminalen, kan vi altså komme oss inn på CTF'en. På nettsiden til _Over The Wire_, sier den at hver gang vi logger inn, trenger vi et passord. Dette er da nivå 0, markert ved at brukernavnet er _bandit0_. Nettsiden forteller at passordet også er _bandit0_, hvilket vi skriver inn når vi har utført linjen med _ssh_.
Før vi begynner, kan det være greit å merke seg noen punkter:

- Når man skriver passord i terminalen, hender det ofte at det ikke dukker opp noen tegn. Dette er helt vanlig
- For å hoppe ut av en _ssh_, kan du skrive _exit_ og trykke enter.
- I mange CTF'er, skrives gjerne flagget med et kjent ord forran, f.eks. _CTF_, så krølleparenteser og flagget inni. Her kommer noen eksempler. 
  - CTF{Jeg_er_et_flagg}
  - flag{c@n_u_und3rs7and_th1s}
  - pico{f1ag_fr0m_picoCTF}
- I _Over The Wire_ sin _Bandit_-CTF ser flagget helt annerledes ut, noe i nærheten av det her _boJ9jbbUNNfktd78000psqOltutMc3MY1_. 
- I mange CTF'er, er flagget gjemt men vi får ofte noen hint om hvor flagget er. Det er ikke flaut å bruke hintet og ofte er det helt nødvendig. 

I Bandit, blir vi altså nødt til å bruke _ssh_ og skrive det gitte passordet (_bandit0_, samme som brukernavnet) for å komme inn på serveren. For å finne passordet til neste nivå, _bandit1_, må vi bruke de kommandoene vi kan. Passordet når du da skriver

```bash
 mathias@kali:~$ ssh bandit1@bandit.labs.overthewire.org -p 2220
 ``` 

 er passordet du fant i den forrige oppgaven. Bare kopier passordet, skriv _exit_ og bruk _ssh_-kommandoen på nytt men endre brukernavn til _bandit1_ isteden for _bandit0_. Det betyr og at det kan være en idé å skrive ned de forskjellige passordene i denne CTF'en, i tilfelle du vil avslutte og begynne igjen senere. 

## Gjennomføring av de første nivåene på Bandit

### Bandit0

Vi skriver altså _ssh_-kommandoen og passordet, _bandit0_.

![ssh til bandit0](bilder/ssh_til_bandit0.PNG)

Da vil det dukke opp en del informasjon, mye likt det som står her. 
Det første som da er lurt å gjøre, er å bruke _ls_, rett og slett for å se hva vi har. 

_ls_ sier det er en fil som heter "readme". Vi ser ikke direkte at det er en tekstfil, men prøver vi å bruke _cd_ ser vi at det ikke er en mappe (not a directory). Hvis vi derimot bruker _cat_ for å se hva som er i filen, dukker flagget opp. 

Legg merke til at nå er brukernavn og maskin endret til "_bandit0@bandit_", fordi vi har brukt _ssh_ inn på en annen maskin/server og brukernavnet er _bandit0_. 

![løsning til bandit0](bilder/løsning_bandit0.PNG)

Deretter, skriver du _exit_ for å forlate _shellet_. Et nytt triks nå, vil være å trykke piltast opp. Dette henter den siste kommandoen du brukte. (Trykker du igjen, henter du den før der igjen). Bytt ut "0"-tallet med 1 og lim inn passordet du henta. 

### Bandit1

Her ser vi at vi har en fil som heter "-". Da fungerer det ikke å kun skrive _cat -_. Vi bruker "./" for å unngå dette problemet. Legg og merke til der det står ^C. Det betyr _keyboard interrupt_, altså at jeg har valgt å ikke gå gjennom med kommandoen. Det er ved bruk av ctrl+C. Dette er nyttig hvis du har skrevet en kommando som _shellet_ ikke helt forstår og ikke greier å gjennomføre kommandoen. Du merker dette om du har skrevet en kommando og når du begynner å skrive igjen, har du ikke den ikoniske "navn@maskin:(mappe)". Grunnen til at akkurat "-" skaper problemer som filnavn er at bindestrek-tegnet er et alias for det som kalles _standard input (stdin)_. (Kan skrive mer om stdin senere).

![løsning til bandit1](bilder/løsning_bandit1.PNG)

### Bandit2

Her ser vi at dersom vi prøver å bruke _cat_ rett fram, prøver den fire ganger å lese fire forskjellige mapper. Vi må derfor bruke fnutter (" ") rundt for å vise at det er en hel fil vi skal se på. 

![løsning til bandit2](bilder/løsning_bandit2.PNG)

### Bandit3

Her blir vi først hintet inn til en mappe som heter _inhere_. Vi går inn i den med _cd_. I den mappen prøver vi oss på _ls_ men finner ingenting. Ved å se på manualen til _ls_, ser vi at vi kan bruke et flagg, _-a_. Her står det at vi skal liste alle filer, til og med de som starter med et punktum. Gjør vi dette, finner vi en fil som heter _.hidden_. Det ser veldig mystisk ut, så åpner vi den med _cat_ finner vi flagget. 

![løsning til bandit3](bilder/løsning_bandit3.PNG)

![man ls](bilder/man_ls.PNG)

### file
_file_-kommandoer forteller enkelt og greit hvilken type fil det er man spør om. Filer som f.eks. heter _data_ er ikke leselig av mennesker, men av datamaskiner. ASCII-filer er som oftest leselige av mennesker. Denne kommandoen kan være grei om du lurer på hva det er du har å jobbe med. 

### Bandit4

Vi går igjen inn i _inhere_. Vi ser at det ligger mange filer her. Etter å ha prøvd å bruke _cat_ på to av filene, ser jeg at jeg ikke finner noe spennende. Derfor bruker jeg _file ./*_. Her bruker jeg altså _file_-kommandoen på alle filene i den mappa jeg er i (_./*_ betyr rett og slett alt i mappa jeg er i.).
Da ser jeg at _-file07_ er leselig og der er flagget. NB! Her kunne man også bare åpnet alle etter hverandre til man fant flagget, men det kan være kronglete hvis det er veldig mange mapper. 

![løsning til bandit4](bilder/løsning_bandit4.PNG)

### find
 _find_ kan hjelpe deg med å finne en fil med en gitt størrelse, hva slags type fil, om den er leselig m.m. Det kan være spesielt gunstig hvis du f.eks. vet at flagg ligger i en fil med noen gitte parametere. 

 For å bruke find, blir vi nødt til å kunne noen flagg. Du finner de fleste ved å sjekke _man find_, men de enkleste er da:
 - _-size_ (antall bytes)c eller -size (antall gigabytes)G (se manualen for flere muligheter)
 - _-readable_
 - _-executable_
 - Vi kan og sette utropstegn forran for å indikere "ikke", f.eks: _! -readable_, som da vil si at filen ikke er leselig. 
 - _-name_ <navn på fil> for å finne hvor en fil med et gitt navn er
 - _-type_ 
   - f er vanlig fil
   - d er directory
   - se manualen for mer


### Bandit5

Vi har fått informasjon om at flagget ligger i en fil som er _human-readable_, 1033 bytes stor, ikke _executable_. Vi åpner først _inhere_, men ser vi har veldig mange mapper å sjekke. Hvis vi skulle gjort alt dette manuelt, hadde det tatt veldig lang tid. Legg merke til hvordan det går helt fint å ha flere flagg etter hverandre. Man må kun vite litt om hvordan kommandoen fungerer for å bruke flaggene riktig.


![løsning til bandit5](bilder/løsning_bandit5.PNG)


## Flere kommandoer

Videre har vi mange kommandoer som kan være lure å ha, ikke nødvendigvis kun for CTF, men til å jobbe i terminalen i Linux, generelt. 

### mkdir og rmdir
Står for "make directory" og "remove directory". Lager/sletter en mappe i mappen du er i. Kan og lage en mappe andre steder ved å skrive pathen til stedet du vil lage mappe. _rmdir_ står for "remove directory". Sletter altså en mappe, men da må den være tom. Det kan unngås ved flagget du kan finne ved å bruke _man rmdir_. 

![mkdir og rmdir](bilder/mkdir_eksempel.PNG)

### touch, echo og rm

_touch_ kan lage en fil. Du kan gjerne spesifisere hva slags fil du lager. I eksempelet har jeg laget en tekstfil (.txt). 
_echo_ betyr bare å skrive en linje med tekst og sende det til _stdout_ (standard output, mer om det senere). Vi kan og kombinere _echo_ "krokodilletegn" (">") for å si at vi skal skrive inn til en fil. I eksempelet har jeg først laget en fil ved å bruke _touch_. Deretter har jeg brukt _echo_ med krokodilletegn/pil for å skrive til tekstfilen. Dette ser vi ved at jeg først brukte _cat_ på tekstfilen, fant ingenting, så skrev jeg litt tekst inn i tekstfilen, og deretter kom det tekst der. 
_rm_ står for "remove". Dette kan fjerne filer på samme måte som _rmdir_ fjerner mapper. 

![touch, echo og rm](bilder/touch_eksempel.PNG)

### clear
_clear_ klarerer terminalen din ved å fjerne alt som står over. Kan være lurt å bruke _clear_ ofte. Den sletter ingenting, bare sørger for at du ikke har så mye ourput i terminalen. 

### nano
_nano_ oppretter en fil og lar deg skrive i den med en gang. _nano_ er en såkalt "text editor". Denne er og vanlig å bruke for å endre på konfigurasjoner i filer. Dette er i motsetning til å først bruke _touch_, for så å bruke _echo_ sammen med pil for å skrive inn til mappe. Merk at vi da havner inn i en egen "skrivefil". For å gå ut av filen og lagre, trykker man ctr+x og trykker "y" hvis du vil lagre, (deretter kommer om du vil endre navnet). Kommandoene under hjelper deg her. Her kan vi igjen presisere hva slags fil det er. I eksempelet skriver jeg:
 ```bash
 mathias@kali:~$ nano tekstfil.txt
 ``` 
 Dette lager altså en tekstfil med navnet tekstfil.txt. Man kan og kun skrive _nano_ for å gå rett inn i tekstskrivingen. Da må du skrive navn etter at du har trykket ctrl+q, y.

 ![nano](bilder/nano_eksempel.PNG)
  ![nano2](bilder/nano2_eksempel.PNG)

### cp og mv
_cp_ står for "copy". Dette kopierer altså en fil. Man bruker kommandoen ved å først skrive copy, så filen man skal kopiere, så hva den nye filen skal hete. Man kan da og skrive pathen til den nye filen, dersom du ønsker å ha den et annet sted. Merk at du må ha med "fullstendig path", om du vil at filen skal kopieres til en mappe, der du må "en mappe tilbake". Hvis jeg ønsker å kopiere fra /Downloads til /Documents, må jeg da ha med tilde-tegnet for å presisere det. 

![cp](bilder/cp_eksempel.PNG)

_mv_ står for "move". Den fungerer på samme måte som _cp_, men da kopierer vi ikke, kun flytter. Vi kan og skrive nytt navn på samme måte som man gjør i _cp_. Det er og slik vi enklest mulig endrer navn på filer. Da bare flytter man filen til den samme mappen som den er, men med nytt navn. I eksempelet ser du bruk av både _cp_, _mv_, samt hvordan "wildcard", (*) kan brukes i praksis. Da den ble brukt, flytta jeg alle .txt-filer fra /Documents til /Downloads. Hvis jeg kun hadde ønsker å flytte "fil1.txt", "fil2.txt" og "fil3.txt", kunne jeg har skrevet _mv fil(stjerne).txt_ ... .

![mv](bilder/mv_eksempel.PNG)

### apropos
Dersom du ikke helt husker hva en kommando heter, men du vet at du skal gjøre noe med f.eks. et directory, kan du skrive 
```bash
 mathias@kali:~$ apropos directory
 ``` 
Denne kommandoen lister da opp alle andre kommandoer som har noe med directories å gjøre. Her fungerer nesten alt som input. 

### grep
_grep_ leter etter "mønstre" i en fil. Det betyr kort oppsummert at den kan sortere. Dersom du får mye output etter å ha brukt en kommando, kan du prøve å bruke kommandoen igjen, men pipe (se "Pipe") for å finne det du leter etter. 

![cat med grep](bilder/cat_med_grep.PNG)

På bildet kan vi se hvordan vi kan hente ut et flag fra en fil med mye rot. _grep_ har mange andre tilleggsfunksjoner som kan være greit å sette seg inn i ved å sjekke _man grep_.