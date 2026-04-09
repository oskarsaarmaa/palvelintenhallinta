# Sudo ilman salasanaa - a)
Salasanaton kirjautuminen on automaatioon kätevä jos on kymmeniä käyttäjiä ja ylläpitäjä haluaa tehdä muutoksia ympäristölle hänen ei tarvii kirjoittaa monimutkaisia/pitkiä salasanoja yhä uudestaan.
Opin, että /etc/sudoers.d/ on se paikka mihin sääntöjä voidaan tehdä. 
Tehtävää tehdessä ajattelin, että onko salasanattomana kirjautuminen turvallista ja normaali tapa työelämässä googlailin asiaa ja sain selville, että jos sääntö on tarkasti määretty oikealle ryhmälle sitten se on turvallista.


## Antero - b)
Tehtävässä tavoitteena oli tehdä käyttäjä, jolle pääsee kirjautumaan sisään ilman, että kone kysyy salasanaa kertaakaan. 
Loin antero-käyttäjän ja lisäsin hänet sudoless-ryhmään. Sudoless-ryhmälle määritin säännön, jossa ryhmään kuuluvilla käyttäjillä ei tarvitse syöttää salasanaa sudo-komentoja käyttäessä. 
main.yml-tekstitiedostoon määritin tämän lisäksi authorized_key-tehtävän. Tällä komennolla kopioin (cat ~/.ssh/id_ed25519.pub) oman isäntäkoneeni julkisen SSH-avaimen suoraan anteron kotihakemistoon. Ilman  avainta orjakone kysyisi salasanaa jo sisäänkirjautumisvaiheessa.
Nyt voin kirjautua/hallinnoida ympäristöä ilman salasanoja.

### Paketti - c)
Asensin orjakoneelle kaksi hyödyllistä työkalua: git-versionhallinnan ja htop-prosessinhallinnan. 
main.yml-tekstitiedostoon määritin nämä asennukset käyttämällä Ansiblen apt-moduulia. Asetin tehtävään update_cache: yes, mikä vastaa Linuxin sudo apt update -komentoa.
Tässä kohdassa tuli vastaan mielenkiintoinen tilanne, kun Ansible antoi punaisen virheilmoituksen "Could not get lock". Ihmettelin tätä jonkin aikaa, pienen googlailun jälkeen sain selville että orjakoneella oli jokin taustapäivitys menossa samaan aikaan, mikä esti uudet asennukset.
Pienen odottelun jälkeen ajoin playbookin uudestaan, ja oli palkitsevaa nähdä, miten molemmat ohjelmat asentuvat ongelmitta.

#### Tiedosto - d)
Loin tiedoston nimeltä leipä.txt antero-käyttäjän kotihakemistoon.
main.yml-tekstitiedostoon määritin tämän käyttämällä copy-moduulia. Käytin siinä pystysuoraa viivaa (|), jonka avulla sain kirjoitettua tiedoston tekstisisällön suoraan playbookiin usealle eri riville.
Asetin tiedoston oikeudet  0600. Symbolisessa muodossa tämä tarkoittaa -rw-------. Tämä tarkoittaa seuraavaa:
Omistaja (antero): Saa lukea (r) ja muokata eli kirjoittaa (w) tiedostoa.
Omistava ryhmä ja muut: Heillä ei ole mitään oikeuksia tiedostoon.
Testasin tiedoston olemassaolon ja oikeudet orjakoneella ls -l -komennolla, ja tiedostot löytyivät!

##### Debug moduuli ja dynaamiset muuttujat - e)
Valtsin  työkaluksi debug-moduulin ja Ansiblen automaattisesti keräämät faktat kyseisestä playbookista. main.yml-tekstitiedostoon määritin tehtävän, joka tulostaa ruudulle orjakoneen käyttöjärjestelmän ja IP-osoitteen käyttämällä muuttujia. 
Tämä oli mielestäni siistiä, sillä se osoittaa, miten Ansible "tuntee" hallitsemansa koneet ilman, että minun tarvitsee syöttää tietoja käsin.

  
###### Lähteet

Karvinen 2026: Palvelinten hallinta https://terokarvinen.com/palvelinten-hallinta/
