# find
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