## x)
### SSH public key
* Avainparin luontiin käytetään komentoa ssh-keygen, joka luo julkisen ja yksityisen avaimen.
* Tärkeetä, että jos SSH avainta käyttäjältä pyydetään hän syöttää .pub pääättyvän avaimen. Yksityisellä avaimella käyttäjän konetta voi hallita, joku muu kuin käyttäjä itse.
* Julkisen avaimen saa siirrettyä palvelimelle komennolla ssh-copy-id localhost tai tunnus@osoite.
* Kun palvelin saa käyttäjän jukisen avaimen se tunnistaa käyttäjän avaimen perusteella, tämä mahdollistaa automaation ja nopeuttaa työntekoa / skaalautuvuutta.

Siistiä miten pieni vaiva avainten käyttöönotto on verrattuna siihen, kuinka paljon se nopeuttaa työntekoa ja ylläpitoa.

### Hello Ansible
* Ansible on työkalu, jolla voidaan hallita useita tietokoneita yhtä aikaa automatisoidusti.
* Ansible asennetaan ohjaavalle koneelle, ja hallittavat koneet määritellään inventory-tiedostoon.
* Voidaan ajaa yksittäisiä komentoja kaikille koneille kerralla, admin voi implementoida muutoksia ympäristöille jopa salasanattomasti.
* Ansible Playbook on YAML tiedosto johon voidaan konfiguroida sääntöjä ympäristölle, säännöt tulevat voimaan playbookin ajon jälkeen (mikäli playbook ajo menee läpi).
Osaako Ansible porrastaa järjestelmälle tehtyjen muutoksien vientiä SSH:n läpi? Jos ei muodostuuko tästä pullonkaula? 


## a) Ssh secrets
Linux koneen asennus, päivitys ja peruskonffaus. OpenSSH:n asennus ja testaus. 

<img width="819" height="195" alt="image" src="https://github.com/user-attachments/assets/9acc2596-9534-4904-b67a-9407bafba676" />


SSH avaimen generointi, komennolla ssh-keygen:


<img width="745" height="39" alt="image" src="https://github.com/user-attachments/assets/2639031e-b4fb-421e-803e-4f2896bdeadc" />


<img width="1042" height="40" alt="image" src="https://github.com/user-attachments/assets/a7321373-f4a8-4abe-a40d-e8072f31e891" />

Loin ryhmän sudoless ja lisäsäin 'antero' käyttäjän ryhmään komennoilla: sudo groupadd sudoless, sudo useradd antero: 

<img width="842" height="37" alt="image" src="https://github.com/user-attachments/assets/ee090320-72a4-4021-9d04-cff1c4abf535" />




Lisäsin main.yml tiedostoon säännöt, jossa: käyttäjät jotka kuuluvat ryhmään 'sudoless' pääsevät kirjautumaan salasanattomana järjestelmään.

<img width="607" height="373" alt="image" src="https://github.com/user-attachments/assets/4eacec1b-6d5e-455f-a03b-1071d84e142b" />



Kirjautuminen SSH:lle ilman salasanaa:

<img width="1050" height="210" alt="image" src="https://github.com/user-attachments/assets/e6707e6b-9526-4070-929f-10b061666de6" />

 

## c) Hei Ansible

Loin YAML tiedoston 'hei_maailma.yml' määritin sinne säännön, jossa kun playbookin ajan Ansible tulostaa "Hei Maailma! Ansible toimii" tekstin:

<img width="617" height="148" alt="image" src="https://github.com/user-attachments/assets/76de6716-ece7-48c4-b298-6d23e76c9866" />

Ansible-playbook:in ajo:

<img width="2025" height="540" alt="image" src="https://github.com/user-attachments/assets/149b2870-026e-402b-ae23-a4b3f18e538f" />

* Ajo meni läpi ja tulosti just sen mitä sääntöihin määritin.


## d) Bonus - Paketin asennus Ansiblella

Loin YAML tiedoston 'asennus.yml' määritin säännöksi, että Ansible asentaa komentoriviohjelman 'cowsay' ja päivittää pakettilistan.

<img width="440" height="206" alt="image" src="https://github.com/user-attachments/assets/9092531c-7707-46f0-9c41-8946ff6af7d2" />

Ensimmäinen playbookin ajo:

<img width="1168" height="297" alt="image" src="https://github.com/user-attachments/assets/fe061a35-f8f2-44a6-bafb-9ae68687cef0" />

Toinen playbookin ajo:

<img width="1331" height="823" alt="image" src="https://github.com/user-attachments/assets/db86fa51-f31e-4138-aa18-78df7960bbb1" />

* Ansible asensi cowsay:n onnistuneesti.


## Lähteet
Karvinen 2026 SSH public key - Login without password: https://terokarvinen.com/ssh-public-key-login-without-password/ 
Karvinen 2026 Hello Ansible: https://terokarvinen.com/hello-ansible/
