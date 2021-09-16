# Bandit1

Relevante sider: _cat_, _ls_

Her ser vi at vi har en fil som heter "-". Da fungerer det ikke å kun skrive _cat -_. Vi bruker "./" for å unngå dette problemet. Legg og merke til der det står ^C. Det betyr _keyboard interrupt_, altså at jeg har valgt å ikke gå gjennom med kommandoen. Det er ved bruk av ctrl+C. Dette er nyttig hvis du har skrevet en kommando som _shellet_ ikke helt forstår og ikke greier å gjennomføre kommandoen. Du merker dette om du har skrevet en kommando og når du begynner å skrive igjen, har du ikke den ikoniske "navn@maskin:(mappe)". Grunnen til at akkurat "-" skaper problemer som filnavn er at bindestrek-tegnet er et alias for det som kalles _standard input (stdin)_. (Se _standard input, output og error_).

![løsning til bandit1](../../../bilder/løsning_bandit1.PNG)