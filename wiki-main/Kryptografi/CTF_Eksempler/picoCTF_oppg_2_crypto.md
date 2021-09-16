# picoCTF oppg. 2 Crypto

Relevante sider: _ROT13_

 Oppgaveteksten sier "Cryptography can be easy, do you know what ROT13 is?" og hintet forteller at oppgaven kan løses på nettet, hvis vi ikke ønsker å gjøre det for hånd. 
 Teksten vi har fått er "cvpbPGS{abg_gbb_onq_bs_n_ceboyrz}". Vi kan rimelig greit se at dette er et flagg som er kryptert. Her ville jeg bare brukt kommandoen vi nettopp har lært:

 ```bash
 mathias@kali:~$ echo "cvpbPGS{abg_gbb_onq_bs_n_ceboyrz}" | rot13
picoCTF{not_too_bad_of_a_problem}
 ``` 