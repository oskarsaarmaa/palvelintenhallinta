## x)
### Git

* Git tallentaa tiedostot tilannekuvina (snapshots). Jos tiedosto ei muutu, Git linkittää aiempaan versioon sen sijaan.
* Suurin osa toiminnoista ei vaadi verkkoyhteyttä, mikä tekee Gitistä nopean ja paremmin saatavilla olevan.
* Git tiedostot jakautuvat kolmeen tilaan: modified, staged ja committed.
* Git antaa kaikelle datalle yksilöllisen tunnisteen niiden sisällön perusteella. Jos tiedoston sisältö muuttuu, sen hash-tunniste muuttuu ja Git huomaa sen ja ilmoittaa käyttäjälle siitä.

On siistiä miten Git varmistaa vanhemman tiedon luotettavuuden hash:in avulla tarkoitan siis sitä, että jos joku menisi muokkaaman vanhoja tietoja kaikki muutkin osalliset tietäisivät siitä.

### Komento: 
  git add --all && git commit; git pull && git push
  
* git add --all: Päivittää indeksin vastaamaan työskentelypuun nykytilaa. Se huomioi uudet tiedostot, muokatut tiedostot ja myös poistetut tiedostot. (add)
* git commit: Ottaa huomioon kaikki tehdyt muutokset, tallentaa muutokset ja lu ne pysyväksi tilannekuvaksi projektin historiaan. (git: commit)
* git pull: Komento hakee muutokset toisesta varastosta (pilvestä) ja integroi ne nykyiseen paikalliseen respoon. (git: pull)
* git push: Komento lähettää paikalliset muutokset palvelimelle ja päivittää viitteet (remote refs). (git: push)


## a) Online
Loin Github:iin uuden projektin "sunshine" lisäsin readme.md ja käytin lisenssinä: GNU General Public License v3.   

<img width="795" height="699" alt="image" src="https://github.com/user-attachments/assets/c6b92e09-a031-44bf-89c4-426a845307c0" />


## b) Dolly
Kävin lisäämässä virtuaalikoneen julkisen SSH avaimen github:iin.

<img width="812" height="491" alt="image" src="https://github.com/user-attachments/assets/d0eccac2-e3c5-4424-a751-763faf88ff48" />

Kloonasin tekemäni respon virtuaalikoneelle:

<img width="773" height="226" alt="image" src="https://github.com/user-attachments/assets/35e5b7d4-517d-4841-88df-598e43d7e7ea" />

Muutin README.md tiedostoa:

<img width="774" height="39" alt="image" src="https://github.com/user-attachments/assets/acc6ed30-9086-4287-9744-229ebb24a551" />

Pusken tekemäni muutoksen pilveen:

<img width="611" height="185" alt="image" src="https://github.com/user-attachments/assets/da746b57-b09f-4b6d-9441-3b8947bca347" />


README.md muutokset 

<img width="846" height="327" alt="image" src="https://github.com/user-attachments/assets/1dd20ca4-7da1-4299-a4c0-6090170116d7" />


## c) Doh!
Muutin README.md tiedostoa ja lisäsin cloudly.md tiedoston varastoon:

<img width="715" height="280" alt="image" src="https://github.com/user-attachments/assets/d6c02a1b-1a75-44d8-bf7e-39e7f2262957" />

Nollaan tekemäni muutokset:

<img width="519" height="37" alt="image" src="https://github.com/user-attachments/assets/e640c289-a3a3-4dca-a45b-50f33ea131cd" />

Komento palautti tiedostot viimeisimpään tallennettuun tilaan. Status:

<img width="469" height="91" alt="image" src="https://github.com/user-attachments/assets/90b4d03d-4361-49fc-b5cf-eeba84a4515f" />


## d) Tukki
### Ensimmäinen commit: 
* README.md ja lisenssi varaston luonti.
  
### Toinen commit:
* Viesti: "Lisää aurinkoisia päiviä" 
* Loki näyttää, että olen luonut cloudy.md tuedoston
* Vihreä rivi: Kertoo, että tiedostoon on kirjoitettu rivi: "Cloudy days are coming"

### Kolmas commit: 
* Kertoo että Cloudy.md on poistettu kokonaan. Poistin, koska vahingossa olin mennyt committaa muutokset c) kohtaan ja halusin reset komennolla poistaa cloudy.md tiedoston.
* Punainen rivi tarkoittaa sitä että "Cloudy days are coming" teksti ja sen tiedosto on poistettu varastosta.

<img width="895" height="612" alt="image" src="https://github.com/user-attachments/assets/4d7f3b09-eb1e-4d33-b3d3-b759655f6693" />


## e) Gitanbile

#### Alustin kansion Git-varastoksi. Kuten tulosteesta näkyy, Git loi tyhjän varaston ansible kansiooni.

<img width="817" height="228" alt="image" src="https://github.com/user-attachments/assets/30645533-b05d-4ecc-a26e-e831c4fda3c6" />

#### Tarkistin, että löytyykö .git kansio.

<img width="565" height="174" alt="image" src="https://github.com/user-attachments/assets/fb55a702-e9eb-4fb9-b90d-74e8c157b2dc" />

#### Valmistelin tiedostot tallennusta varten, tein ensimmäisen commitin "Ansible rakenne" viestillä. Git loi tässä vaiheessa "root-commitin" (tunniste: c75f065), joka tallensi Ansiblen perusrakenteen versionhallinnan piiriin.

<img width="775" height="169" alt="image" src="https://github.com/user-attachments/assets/01ea7068-0f9d-433c-9894-392ace0ff397" />

#### Luoin gitanbile kansion ja sinne uuden playbookin git-ansible.yml:

<img width="665" height="176" alt="image" src="https://github.com/user-attachments/assets/bfa8077d-781f-4504-bacf-b097c4808e46" />

#### Ajoin git-ansible.yml playbook:in, ajo onnistui:

<img width="1250" height="311" alt="image" src="https://github.com/user-attachments/assets/1144b409-8d40-4d6b-b6f5-8b5c1f2789e6" />

#### Tallensin testatun ja toimivan muutoksen Gittiin. Git commit tallensi uuden tilannekuvan (tunniste 702d449), jossa näkyy yksi muutettu tiedosto ja kahdeksan uutta riviä.

<img width="932" height="96" alt="image" src="https://github.com/user-attachments/assets/04528d82-7607-4467-8fa5-8fd3ca785661" />

#### Ansible kansion git log muutoksien jälkeen:

<img width="678" height="253" alt="image" src="https://github.com/user-attachments/assets/eb6c22c1-e9d8-41cf-a545-4f2b9b9a3c89" />


## g) Se toinen järjestelmä: Windows

#### 1. Git asennus Windows:
* Lataa Git 64-bit osoitteesta: https://git-scm.com/install/windows
* Asennus vaiheessa voit edetä painamalla "Next" oletusasetuksilla. Suosittelen valita "Git Bash" asetuksen mikäli olet edistyneempi käyttäjä, asetus tuo Linux tyylisen komentorivin Windowsiin (Käytän tätä). HUOM! Valitse teksti editor, jota osat käyttää oletuksena Git käyttää Vim voit valita esim. Notepad++
* Avaa Git sovellus Windows hakukentästä

#### 2. Varaston kloonaus
Hae projektin osoite GitHubista Code-painikkeen alta. Voit käyttää HTTPS-linkkiä.
* Komento: git clone {osoite}
* Mitä tapahtuu: Git lataa koko projektin pilvestä omalle koneellesi.
  <img width="404" height="329" alt="image" src="https://github.com/user-attachments/assets/7dab8630-6b05-4037-9efd-9218c2d63045" />

#### 3. Navigointi
Kloonaamisen jälkeen siirry projektikansioon ja tarkista, mitä se sisältää.
* cd {tiedoston nimi}
* ls [listaa kansion sisällön]
  <img width="261" height="94" alt="image" src="https://github.com/user-attachments/assets/094c0e8a-8325-4094-be71-14ec0e610251" />
  
#### 4. Muutosten tekemienen 
Kun olet muokannut tiedostoja (esim. Notepadilla tai Vimillä), ne on lisättävä "jonoon" eli indeksiin.
* Komento: git add --all
* Tulos: Git huomioi kaikki muutokset: uudet tiedostot, muokkaukset ja poistot koko projektin laajuisesti.
  <img width="427" height="40" alt="image" src="https://github.com/user-attachments/assets/b9d5da21-303d-4762-ab0e-848a49d123fc" />
  
#### 5. Paikallinen tallennus 
Kun muutokset on lisätty indeksiin, ne lukitaan pysyväksi versioksi koneesi muistiin.
* Komento: git commit
* Git näyttää sinulle tekemäsi muutokset kuittaa ne tallentamalla ja poistumalla tekstieditorista.
* Kannattaa kirjoittaa lyhyt kuvaus siitä, mitä muutit.

#### 6. Muutosten siirto pilveen
Lopuksi paikalliset tallennukset lähetetään takaisin GitHubiin.
* Komento: git push
* Windowsilla Git avaa tässä kohtaa selaimen kirjautumista varten, kirjaudu GitHub tunnuksilla.
* Kirjautumisen jälkeen git ilmoittaa terminaaliin, että siirto on onnistunut (mikäli siirto meni läpi).  
  <img width="446" height="159" alt="image" src="https://github.com/user-attachments/assets/3f947adf-6ff8-4e0a-ab9e-6b4de59234e4" />

## h) Varaston oikeuksien jakaminen

Lisäsin parini varastoon 'projekti' 
<img width="646" height="190" alt="image" src="https://github.com/user-attachments/assets/035efcc3-12d3-4315-b982-f79490d24e4a" />

Pull
<img width="695" height="339" alt="image" src="https://github.com/user-attachments/assets/0c8359c3-7360-45ac-95dc-228bbbf3210b" />

Logi muutoksista:
<img width="567" height="641" alt="image" src="https://github.com/user-attachments/assets/0cff064b-4a52-42f9-a9e4-27b5e0975a58" />



## Lähteet: 

karvinen 2026 Palvelinten Hallinta: https://terokarvinen.com/palvelinten-hallinta/ 

Chacon and Straub 2014:

Git 2026: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

Git book 2014: https://git-scm.com/book/en/v2

Git komennot (add) 2026: https://git-scm.com/docs/git-add

Git komennot (git: commit, pull ja push) 2026: https://git-scm.com/docs/git

Git Windows 2026: https://git-scm.com/install/windows



