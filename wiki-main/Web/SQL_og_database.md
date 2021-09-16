# Database og SQL 

<!-- Legge til flere SQL-kommandoer som feks (--'' OR 1=1)-kommandoen og fortelle hvorfor den fungerer -->
En database er en samling med informasjon. En nettside trenger en database til å lagre informasjon. Dette kan være f.eks. en samling av alle registrerte brukere, diverse registre, registrerte gjenstander i en nettbutikk, osv. Når vi oppretter en konto på en nettside, vil den lagres i en database, sammen med et passord. Når vi logger inn på nettsiden, skriver vi altså inn brukernavnet og passordet. Da sender vi en forespørsel ("_query_") til nettsiden. Da spør vi om nettsiden kan se i databasen etter noen med det oppgritte brukernavnet og passordet. Dersom dette stemmer overens, vil du få logget inn på siden. 

Mange databaser er skrevet i et språk som heter SQL (Structured Query Language). Med SQL kan stille slike "_queries_" for å hente ut diverse ting fra databasen. La oss f.eks. si at vi har en database over alle studenter i Trondheim. Alle studentene er registrert med navn, unik student-id og studieretning. Vi kan da søke etter alle studenter som går KomTek, eller alle studenter som heter Ola. Man kan og spesifisere queriesene mer, og hente alle studenter som både heter Ola og går KomTek. Forskjellige versjoner av SQL har litt forskjellig syntax, men i all hovedsak ser det slik ut: 

SELECT ? FROM ? WHERE ? . 

Dersom man skal logge inn på en nettside med brukernavn=Ola og passord=fotball, kan det se slik ut:

SELECT \* FROM 'users' WHERE name='Ola' AND password='fotball'.

Her har vi hentet alt (\* betyr 'wildcard', altså at man henter alt), fra gruppen 'users' med brukernavn og passord som gitt. Merk at det er en enorm sårbarhet i en nettside om det ser slik ut. Det er mange steg som helst skal gjennomføres her, f.eks. _"hashing"_ av passord, med "_salt"_. 

Dersom man ikke har satt nødvendige restriksjoner på hvordan man logger inn eller søker på ting, kan man misbruke det. Uten de nødvendige restriksjonene, er nettsiden sårbar for blant annet _"SQL injection attack"_. Det betyr at vi bruker SQL-kommandoer rett inn i skrivefelt, som serveren forstår som kode. Disse nødvendige restriksjonene er gjerne at det ikke skal være lov å bruke spesielle tegn (som bindestrek, fnutter, osv.) i innlogging. 