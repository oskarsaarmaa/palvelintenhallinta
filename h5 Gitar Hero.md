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

# Lähteet: 

Chacon and Straub 2014:

Git 2026: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

Git book 2014: https://git-scm.com/book/en/v2

Git komennot (add) 2026: https://git-scm.com/docs/git-add
Git komennot (git: commit, pull ja push) 2026: https://git-scm.com/docs/git

