# ssh og intro til Bandit

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