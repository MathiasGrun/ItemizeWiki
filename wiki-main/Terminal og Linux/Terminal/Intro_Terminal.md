# Intro Terminal

##  Terminal
 Før vi begynner med hackingen, er det nødvendig å vite hva en "terminal" er. En terminal er et grensesnitt, altså noe du som person kan interagere med. I terminalen så kjører man en software som kalles et "shell". Her finnes det forsakjellige varianter men de vanlige er "Bourne Shell" og "Bourne Again Shell" (her brukes for det meste forkortelsen "Bash"). En terminal kjører altså et "shell". De som har Linux eller Mac som operativsystem på PC'en, bruker samme språk i terminalen. Det er fordi de begge er basert på det som heter Unix. Windows PC'er bruker ofte shellet som heter "PowerShell", fordi Windows er basert på MS-DOS. Ved standardkonfigureringer, bruker altså Linux og Mac det samme språket i terminalen, mens Windows ser litt annerledes ut. Forskjellene der er litt som i norsk og svensk. Problemet er bare det at kommandoene du setter inn må være korrekte. Dersom du skriver noe til maskinen som den ikke forstår, vil den si fra om det. 

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
- _clear_ klarerer terminalen din ved å fjerne alt som står over. Bare å skrive det i terminalen og trykke enter. Kan være lurt å bruke _clear_ ofte. Den sletter ingenting, bare sørger for at du ikke har så mye ourput i terminalen. 

### apropos
Dersom du ikke helt husker hva en kommando heter, men du vet at du skal gjøre noe med f.eks. et directory, kan du skrive 
```bash
 mathias@kali:~$ apropos directory
 ``` 
Denne kommandoen lister da opp alle andre kommandoer som har noe med directories å gjøre. Her fungerer nesten alt som input. 

(Her kan du begynne å lese på "Terminalkommandoer")