# picoCTF oppg. 3 Crypto

Relevante sider: "One time pad" under "Random Simple Substitution Cipher" eller "Vigenère"

Vi får beskjed om at OTP er veldig trygg å bruke, men mindre man kan nøkkelen. Chifferteksten vår er "UFJKXQZQUNB", og vi får gitt at nøkkelen er "SOLVECRYPTO". I tillegg får vi en tabell som hjelper oss med å plusse bokstaver sammen. Vi får og vite at flagget er på formen picoCTF{...}. Vi skal altså finne det som skal stå inni krøllparentesene. 

Siden vi her har den krypterte teksten, legge hver on en bokstav her i "midten". Vi kan da si at nøkkelen legges på venstre og det hemmelige ordet legges oppå. 
Ved å titte ser vi at det blir "CRYPTOISFUN". 
Vi kan og legge merke til at det er er egentlig som et Vigenère Cipher, der perioden er 11 og klarteksten vår er og 11 bokstaver lang.