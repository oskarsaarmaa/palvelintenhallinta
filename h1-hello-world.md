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
Linux koneen asennus, päivitys ja peruskonffaus. OpenSSH:n asennus ja testaus. SSH avaimen generointi, pääsin kirjautumaan SSH ilman salasanaa. 
<img width="955" height="118" alt="image" src="https://github.com/user-attachments/assets/7b70d2f2-de73-42f3-8c59-382223b9382c" />

<img width="666" height="114" alt="image" src="https://github.com/user-attachments/assets/05e2ab17-b8f4-470c-b192-62aabe470f73" />

## c) Hei Ansible
Ansible ja Micro teksti editorin asennus. Ansible konfigurointiin tein kansioita ja tekstitiedostoja Micro:lla. Testasin Ansible uptime komennon avulla.
<img width="708" height="58" alt="image" src="https://github.com/user-attachments/assets/c701326e-c57e-49c2-920f-3c5afc0fd6c3" />

<img width="555" height="182" alt="image" src="https://github.com/user-attachments/assets/386c7a0e-4233-407d-9669-24ca6a93e926" />

Loin kansiot ja tekstitiedostot: hosts.ini ansible.cfg ja site.yml määritin niihin säännöt jolla ansoble hello world toimii. 

<img width="1178" height="63" alt="image" src="https://github.com/user-attachments/assets/6a0ada0a-d659-4b00-9d9e-96203d901fd6" />

<img width="763" height="43" alt="image" src="https://github.com/user-attachments/assets/c1f2b97b-6fe4-48df-b18d-74e99d0ce502" />

<img width="855" height="75" alt="image" src="https://github.com/user-attachments/assets/b56c4325-5733-4120-9789-0d25ea9b935b" />

Hakemistopuu:
<img width="730" height="178" alt="image" src="https://github.com/user-attachments/assets/76f9d613-4c5b-49b6-8fa2-022aa0fe0c6e" />

Lopputulos:
<img width="1057" height="498" alt="image" src="https://github.com/user-attachments/assets/411f14df-ae39-4b2e-a46f-7f14e0698720" />

<img width="1142" height="30" alt="image" src="https://github.com/user-attachments/assets/8baf6a9c-491a-4132-b939-8bd2b4bd17b1" />


## Lähteet
Karvinen 2026 SSH public key - Login without password: https://terokarvinen.com/ssh-public-key-login-without-password/ 
Karvinen 2026 Hello Ansible: https://terokarvinen.com/hello-ansible/
