# x)
4.12.1 Ominaisuuksien määrä:

- Konfiguraationhallinnan työkalut kuten: Ansible ja Salt omaavat valtavan määrän moduuleita ja tuhansia funktioita.
- Työkalut mahdollistavat järjestelmän automatisoinnin, ominaisuudet kuitenkin tekevät järjestelmän hallinnasta vaikeamman suuren ja monimutkaisen ekosysteemin takia (riippuu toki siitä kuinka suuren osan automoi järjestelmästä).

4.12.2 Mitä oikeasti käytetään:

- Vaikka tarjolla on tuhansia funktioita, käytännön tapaustutkimuksissa vain hyvin pientä osaa todella käytettiin.
- Suosituimpia toimintoja ovat: tiedostojen hallinta, pakettejen asennus ja palveluiden hallinta.
- Tämä osoittaa, että suurta osaa infrastruktuurista voidaan hallita hyvin rajatulla peruskäskyjen joukolla.

4.12.3.1 Tärkeimmät rakennuspalikat:

- Pelkkä komentojen listaus ei riitä, vaan niiden pitää jutella keskenään.
- Tyypillinen ketju on: Paketti -> Tiedosto -> Palvelu. Esim. asennetaan Apache, muokataan sen asetustiedostoa ja varmistetaan, että palvelu käynnistyy uudelleen muutoksen jälkeen.
- Riippuvuuksien hallinta on kriittistä, jotta muutokset tapahtuvat oikeassa järjestyksessä ja järjestelmä pysyy halutussa tilassa


->  On mielenkiintoista, miten suuri kuilu on tarjolla olevien ominaisuuksien ja todellisen käytön välillä. 
    Herää kysymys: tekeekö työkaluista turhaan raskaita se, että niissä on valtavasti erikoistoimintoja,
    joita vain murto-osa käyttäjistä ikinä tarvitsee, vai onko tämä välttämätön ammattikäytössä?


## a) Räpylä
Sammutin Apache:n joka oli pyörimässä portilla 80 jota haluan käyttää porttia Caddy palvelulle. 

<img width="567" height="24" alt="image" src="https://github.com/user-attachments/assets/bcc61b5c-8071-446c-9431-f2ffcca46445" />


<img width="906" height="94" alt="image" src="https://github.com/user-attachments/assets/1e1d3292-8216-432a-9f2b-995790ab393b" />

Asensin Caddy:n ja aktivoin palvelun:


<img width="622" height="22" alt="image" src="https://github.com/user-attachments/assets/62d43417-3da7-44a4-9440-0e8739e2c227" />


Tarkistin, että onko palvelu päällä ja tuleeko caddy:n oletussivu näkyville kun haen localhostia selaimella:

<img width="855" height="234" alt="image" src="https://github.com/user-attachments/assets/04ac4f97-4bd0-483a-922f-12e621c6483f" />


<img width="922" height="547" alt="image" src="https://github.com/user-attachments/assets/5e06b242-cf60-46a6-92a8-aa96603f4cc7" />


### b) Automaatti
Loin ***** tiedoston. Määritin säännöt, säänöt saa aikaan seuraavan tarkistaa onko portti 80 vapaana caddy:lle ja asentaa Caddy:n automaattisesti kun pyörtiän playbookin:


<img width="565" height="312" alt="image" src="https://github.com/user-attachments/assets/d301241f-6126-4c0b-bcbc-c8ffdd979565" />


<img width="1268" height="363" alt="image" src="https://github.com/user-attachments/assets/743a5327-00bd-4a6f-8f66-9e6e2aa1b560" />

#### c) Asetus
Muutin asetustiedoston konfiguraatiota hallintakoneella ja varmistin, että muutokset siirtyvät automaattisesti palveluun.

<img width="607" height="289" alt="image" src="https://github.com/user-attachments/assets/4da074c5-c698-49a3-a594-6ab7b63e78fa" />

Muokkasin playbook.yml-tiedostoa ja lisäsin Caddyfile-tehtävän, jossa määriteltiin uuden vastaustekstin: "Caddy on ansiblen hallinnassa :-)". 

<img width="530" height="78" alt="image" src="https://github.com/user-attachments/assets/cd570da7-8507-410c-98fc-bd2852299aa3" />


Ensimmäinen playbookin ajo. Ansible huomasi, että tiedosto /etc/caddy/Caddyfile oli muuttunut. Tila oli changed.

<img width="1247" height="468" alt="image" src="https://github.com/user-attachments/assets/5bc7054d-3481-4223-be13-20c7fd190103" />

Toinen playbookin ajo. Tila on nyt ok ja changed=0. Tämä osoittaa Ansiblen olevan idempotentti eli järjestelmä ei tee turhia muutoksia, jos järjestelmä on jo halutussa tilassa.

<img width="1250" height="422" alt="image" src="https://github.com/user-attachments/assets/e9b5020e-14ce-4cf4-abf1-031eb6ae6ad6" />


Varmistin asetusten voimaantulon, terminaalissa ja selaimessa:

<img width="766" height="51" alt="image" src="https://github.com/user-attachments/assets/029a0f0b-b8f7-4c66-9cb0-b61e58459912" />


<img width="387" height="117" alt="image" src="https://github.com/user-attachments/assets/fc9b5d05-e01c-44a9-b10a-d24ccd3e6b64" />


##### d) Paikka remonttiin
Poistin koko Caddyn asetuskansion. Testasin tuhon lataamalla localhost sivun, odotin "Connection refused" virheilmoitusta kun latastin sivun.
Sivu kuitenki latasti ja toimi ihan normaalisti, otin selvää ja Caddy:n muistoon oli säilinyt asetuskansio.

<img width="523" height="34" alt="image" src="https://github.com/user-attachments/assets/c7d6af9d-42c3-46a5-bf85-849692f191a0" />

<img width="725" height="39" alt="image" src="https://github.com/user-attachments/assets/23105154-ed4b-400d-916e-69ef3910f4e1" />

<img width="444" height="127" alt="image" src="https://github.com/user-attachments/assets/c0a21f74-6bb7-4c2a-bda3-b7a58446e7d2" />












