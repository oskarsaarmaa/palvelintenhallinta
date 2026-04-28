## x)
### Salasanaton sudo
* Käyttäjä, joka kuuluu ryhmään jossa ryhmän säännöissä sallitaan salasanaton kirajutuminen pystyy kirjautumaan salasanattomana järjestelmään.
* Kätevä automaatiossa, mutta riskialtis, jos koneelle pääsee ulkopuolinen taho.

### Munroe
* Sarjakuva opettaa, että sudo on "taikasana" jolla saa linuxin tekemään mitä käyttäjä haluaa.

### Salasanaton sudo Ansiblella
* Salasanaton kirjautuminen mahdollistaa satojen koneiden ylläpidon ilman manuaalista salasanojen syöttelyä.

### ansible-doc
ansible-doc copy
* Kopioi tiedostoja paikalliselta tai etäkoneelta kohdekoneelle.

ansible-doc apt
* Hallitsee apt-paketteja Debian/Ubuntu pohjaisille järjestelmille.

ansible-doc file
* Hallitsee tiedostojen, hakemistojen ja symlinkkien ominaisuuksia.

ansible-doc user
* Hallitsee käyttäjätilejä ja niiden ominaisuuksia.

ansible-doc authorized_key
* Lisää tai poistaa SSH-julkisia avaimia.

## a) Sudoless 
Salasanaton kirjautuminen on automaatioon kätevä jos on kymmeniä käyttäjiä ja ylläpitäjä haluaa tehdä muutoksia ympäristölle hänen ei tarvii kirjoittaa monimutkaisia/pitkiä salasanoja yhä uudestaan.
Opin, että /etc/sudoers.d/ on se paikka mihin sääntöjä voidaan tehdä. 
Tehtävää tehdessä ajattelin, että onko salasanattomana kirjautuminen turvallista ja normaali tapa työelämässä googlailin asiaa ja sain selville, että jos sääntö on tarkasti määretty oikealle ryhmälle sitten se on turvallista.

Luon Ryhmän "sudoless" (sudo groupadd sudoless) ja lisään ryhmään "antero" käyttäjän (sudo adduser antero - sudo adduser antero sudoless). Tarkistan antero tilin ryhmät:

<img width="712" height="35" alt="image" src="https://github.com/user-attachments/assets/d6ab0c71-4a51-4466-9fb3-89ecc611ba1f" />


Luon sudoless tiedoston ja määritän sinne säännön jossa sudoless ryhmässä olevilla käyttäjillä ei tarvitse syöttää salasanaa kirjautumiseen / muutoksien tekemiseen salasanaa. 

<img width="628" height="41" alt="image" src="https://github.com/user-attachments/assets/3570806d-0462-4de4-9e7d-bd4af9644b19" />

Pääsin kirjautumaan ilman salasanapyyntöä:

<img width="841" height="203" alt="image" src="https://github.com/user-attachments/assets/92987929-6407-4a10-8bdd-fa91dced4af3" />

<img width="551" height="65" alt="image" src="https://github.com/user-attachments/assets/1b3b42b9-1f8f-48d7-a183-3b09611421b7" />


## b) Antero 
Tehtävässä tavoitteena oli automoida sudon käyttö ilman salasanaa ansiblen avulla.

Ansible hakemistopuu:

<img width="446" height="211" alt="image" src="https://github.com/user-attachments/assets/b0a874a9-224c-4462-912e-4162a7333839" />

Julkinen SSH avain:

<img width="833" height="32" alt="image" src="https://github.com/user-attachments/assets/665f855a-237f-4518-b2be-2579179282b7" />


Sääntö - Antero

<img width="920" height="348" alt="image" src="https://github.com/user-attachments/assets/30ce8fd4-4880-41d1-aa66-85b654128ee3" />


Site.yml konfigurointi: 

<img width="438" height="98" alt="image" src="https://github.com/user-attachments/assets/86636e5a-c309-4bd0-ae0c-cebd8495864f" />

Ansible kysyy become salasanaa kun ajaa -K (--ask-become-password) operaattorilla:

<img width="1265" height="553" alt="image" src="https://github.com/user-attachments/assets/12fc73f7-eedb-4647-9547-6bebf35c77b8" />

Salasanaton SSH kirjautuminen:

<img width="1165" height="215" alt="image" src="https://github.com/user-attachments/assets/b7cc949f-769f-4020-b4a5-ae8f03e6265e" />


## c) Paketti 
Asensin orjakoneelle kaksi hyödyllistä työkalua: git-versionhallinnan ja htop-prosessinhallinnan. 
main.yml-tekstitiedostoon määritin nämä asennukset käyttämällä Ansiblen apt-moduulia. Asetin tehtävään update_cache: yes, mikä vastaa Linuxin sudo apt update -komentoa.

<img width="402" height="114" alt="image" src="https://github.com/user-attachments/assets/4704616f-5f43-4460-b221-7d396cae223b" />

Kokeilin löytyykö git ja htop ohjelmat ansiblen polusta:

<img width="571" height="74" alt="image" src="https://github.com/user-attachments/assets/15f5ead8-da12-4b41-bc9a-729c4230d948" />




## d) Tiedosto 
Loin tiedoston nimeltä leipä.txt antero-käyttäjän kotihakemistoon.


Asetin tiedoston oikeudet  0600. Symbolisessa muodossa tämä tarkoittaa -rw-------. Tämä tarkoittaa seuraavaa:
Omistaja (antero): Saa lukea (r) ja muokata eli kirjoittaa (w) tiedostoa.
Omistava ryhmä ja muut: Heillä ei ole mitään oikeuksia tiedostoon.

<img width="596" height="60" alt="image" src="https://github.com/user-attachments/assets/38890fcb-de0d-4f1d-bc07-813e36fce0dc" />

main.yml:

<img width="438" height="228" alt="image" src="https://github.com/user-attachments/assets/823c13b5-0f29-4b30-ae83-f0cb5c11247a" />

Leipä.txt:

<img width="494" height="95" alt="image" src="https://github.com/user-attachments/assets/b9333df8-6fdd-44c3-8b0d-b1277430e8e1" />


## Debug moduuli ja dynaamiset muuttujat - e)
Valtsin  työkaluksi debug-moduulin ja Ansiblen automaattisesti keräämät faktat kyseisestä playbookista. main.yml-tekstitiedostoon määritin tehtävän, joka tulostaa ruudulle orjakoneen käyttöjärjestelmän ja IP-osoitteen käyttämällä muuttujia. 
Tämä oli mielestäni siistiä, sillä se osoittaa, miten Ansible "tuntee" hallitsemansa koneet ilman, että minun tarvitsee syöttää tietoja käsin.

main.yml:

<img width="1049" height="55" alt="image" src="https://github.com/user-attachments/assets/668f4971-c71d-4263-935d-9d3f2e1c6c09" />

Testasin pyörittämällä playbookin:

<img width="1257" height="157" alt="image" src="https://github.com/user-attachments/assets/41a3e611-cd31-4471-8098-be7b402ef6a4" />


  
## Lähteet

Karvinen 2026: Palvelinten hallinta https://terokarvinen.com/palvelinten-hallinta/

Karvinen 2026: Sudo without password https://terokarvinen.com/passwordless-sudo/

Karvinen 2026: Passwordless Sudo with Ansible https://terokarvinen.com/passwordless-sudo-with-ansible/

Ansible Community Documentation 2026: https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_vars_facts.html

Ansible Community Documentation 2026: https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/debug_module.html
