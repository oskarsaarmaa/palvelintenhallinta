# x)
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







## Lähteet: 

Chacon and Straub 2014:

Git 2026: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

Git book 2014: https://git-scm.com/book/en/v2

Git komennot (add) 2026: https://git-scm.com/docs/git-add
Git komennot (git: commit, pull ja push) 2026: https://git-scm.com/docs/git

