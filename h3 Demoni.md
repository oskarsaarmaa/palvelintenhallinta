# x)


## a) Apassi
Apache2 asennus käsin ilman automatisointia:

<img width="595" height="24" alt="image" src="https://github.com/user-attachments/assets/e8ca99eb-7e62-4c91-aadb-a8f03a72f8ed" />

Tarkistin onko palvelu päällä systemctl komennolla:

<img width="780" height="83" alt="image" src="https://github.com/user-attachments/assets/5e3ad694-c750-4575-95a2-b5c3c174a5de" />

Apache2 default sivu näkyy selaimella:

<img width="841" height="182" alt="image" src="https://github.com/user-attachments/assets/b2e5a4cb-7576-4b6f-8fbc-1475d368d148" />

Annan käyttäjälle html tiedoston muokkausoikeuden:

<img width="682" height="22" alt="image" src="https://github.com/user-attachments/assets/8395b411-4665-4573-a88b-0223cbb09252" />

Muokkasin webbisivua:

<img width="831" height="51" alt="image" src="https://github.com/user-attachments/assets/450d9e56-60e8-402a-a1ff-e0e3966dcd2d" />


Ei pyytänyt salasanaa sivua muuttaeessa. Koska "chown" komento siirsi tiedoston root oikeuden root käyttäjältä oskar käyttäjälle:

<img width="660" height="38" alt="image" src="https://github.com/user-attachments/assets/98d3adcb-ba80-4178-9811-cf6e0f438bb6" />


Webbisivu muutoksen jälkeen:


<img width="469" height="131" alt="image" src="https://github.com/user-attachments/assets/0daf2585-158b-4678-9a73-d4a92aee89b0" />


### b) MoottoriX
Ennen Nginx:in asennusta sammutin apache2 palvelun, koska palvelut toimivat samalla portilla ja jos palvelut ovat samanaikaisesti päällä ongelmatilanteita syntyy.

<img width="889" height="54" alt="image" src="https://github.com/user-attachments/assets/afb3419a-cb54-4a66-b574-642fbbc6deb7" />

<img width="529" height="109" alt="image" src="https://github.com/user-attachments/assets/13349385-72dd-4a07-9d17-7ebd03e562f6" />

Nginx toimivuuden testaaminen, palvelu on päällä kun sitä hakee systemctl:llä ja localhost sivu nyt latautuu ongelmitta:

<img width="855" height="78" alt="image" src="https://github.com/user-attachments/assets/f2e77e70-ba45-473d-b0c3-5040c791b6ae" />


<img width="623" height="269" alt="image" src="https://github.com/user-attachments/assets/dc2dcce5-2729-46c7-97d8-60dd11b9c8cb" />

Siirrän "chown" /var/www/html kansion oikeudet "antero" käyttäjälle. 

<img width="622" height="24" alt="image" src="https://github.com/user-attachments/assets/448d2ac2-1b0f-4255-a76e-78cd8241e350" />

<img width="550" height="55" alt="image" src="https://github.com/user-attachments/assets/b2a2154b-a467-4eaa-a06f-5fb7158df5e2" />


Muokkasin localhost webbisivua, kone ei pyytänyt salasanaa. koska siirsin oikeudet antero käyttäjälle. 


<img width="850" height="42" alt="image" src="https://github.com/user-attachments/assets/c2114e6d-6ea4-4887-97e5-847a94c08c87" />


Webbisivu:

<img width="415" height="121" alt="image" src="https://github.com/user-attachments/assets/a5820272-9027-4a93-8671-b7bef45819e0" />

#### c) Automoottorix
Automatisoin weppipalvelimen pystytyksen muokkaamalla antero-roolin tehtäviä. Lisäsin sinne Nginx-paketin asennuksen ja kansion oikeuksien vaihdon. 
recurse: yes asetuksella varmistin, että oikeudet pysyvät käyttäjällä läpi koko hakemistorakenteen, jolloin sivun muokkaus onnistuu tavallisena käyttäjänä ilman root oikeutta.

<img width="554" height="280" alt="image" src="https://github.com/user-attachments/assets/a8caf9d5-f66e-496e-b81c-541e027baa56" />

Ajoin ansible-playbookin:

Ajo 1:

<img width="1274" height="195" alt="image" src="https://github.com/user-attachments/assets/d4a49612-c379-405b-b570-d84003451bb7" />

Ajo 2:

<img width="1261" height="195" alt="image" src="https://github.com/user-attachments/assets/2458834b-9a82-4b5d-a7f8-e51e4969072f" />

Tekemäni muutokset menivät läpi. 

Testasin nginx toimivuuden kirjautumalla antero käyttäjälle ja muuttamalla webbisivua:

<img width="889" height="84" alt="image" src="https://github.com/user-attachments/assets/8343ea5f-106d-4510-acea-2ab8aa3a9ded" />

Webbisivu:

<img width="424" height="128" alt="image" src="https://github.com/user-attachments/assets/191a49e1-6485-4da4-91e9-df4d927cc335" />

Lopputulos:
Varmistin automaation onnistumisen kirjautumalla sisään antero-käyttäjänä ja muokkaamalla index.html-tiedostoa. Muutos päivittyi selaimelle, muutoksen yhteydessä kone ei pyytänyt salasanaa.


##### d) Bonus - Osiris-T
Asensin puhtaan Debian 13 distron, ja suoritin peruskonffauksen.

<img width="930" height="83" alt="image" src="https://github.com/user-attachments/assets/cce5260f-c4ba-4f80-a73d-c91d28c0e684" />



##### Lähteet:

Karvinen 2026: Palvelinten hallinta https://terokarvinen.com/palvelinten-hallinta/

Karvinen 2026 Apache installed with Ansible: https://terokarvinen.com/apache-ansible/

Ansible Community Documentation 2026: https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html

Häkämies, Saario, Mukkula 2026: https://github.com/oskarihakamies/IDS-project

Häkämies etal 2026: https://github.com/oskarihakamies/IDS-project/blob/main/How-To-Install.md
