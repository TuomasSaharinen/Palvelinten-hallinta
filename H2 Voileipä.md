X) Tiivistelmä:
Karvinen 2026: Sudo withoutpassword
  - Salasanattoman sudon määritys
  - Tärkeä varotoimi on pitää pääkäyttäjällä kuori auki (sudo -i)
  - %sudoless ALL = (ALL) NOPASSWD: ALL
  -Käytä aina hyviä salasanoja, älä ikinä käytä huonoja sekä opettele tekemään alusta alkaen oikein.

Munroe 2006: xkcd 149: Sandwitch
  - Pyyntö tee minulle voileipä hylätään, mutta kun lisätään sudo pyyntöön se suoritetaan heti.

Karvinen 2026: Passwordless Sudo with Ansible
  - Kokeile manuaalisesti ennen kuin automatisoit
  - Ensimmäisellä kerralla ansiblelle pitää antaa salasana -K (--ask-become-password)

Ansible-doc copy
  - nimensä mukaan saadan kopiomalla siierrettyä tiedostoja paikalliselta tai etäkoneelta kohdekoneen hakemistoon
  - määritetään dest: tiedoston "päämäärä" tai kohdepolku
  - owner: Tiedoston omistaja
  - Group: omistaja ryhmä
  - content: Mahdollistaa tiedon kirjoittamisen tehtävä määrittelyssä
  - src: kopio olemassa olevan tiedoston
  - mode: käyttäjän määrittämät oikeudet
    

Ansible-doc apt
  - Hallinnoi paketteja
  - name: paketin nimi
  - state: paketin tila, present, absent tai latest

Ansible-doc file
  - Luodaan hakemistoja ja tiedostoja
  - path: hallinnoitavan tiedoston tai hakemiston polku
  - recurse:Määrittää, asetetaanko annetut oikeudet rekursiivisesti koko hakemistorakenteelle
  - src: kohteen polku josta tiedosto tai hakemisto on
  - owner, group ja mode, omistaja, omistaja ryhmä ja oikeuksien tila esim 0644

Ansible-doc user
  - moduuli hallinnoi järjestelmän käyttäjätilejä ja niiden ominaisuuksia, kuten ryhmiä, kotihakemistoja
  - name: halinnoitavan käyttäjän nimi
  - create_home: luodaanko kotihakemisto jos ei ole valmiiksi
  - groups: lista ryhmistä johon kuuluu
  - state: pidetäänkö käyttäjä present eli olemassa vai absent eli poistetaan
  - system: luo tilin järjestelmäkäyttäjänä

Ansible-doc authorized_key
  - lisää tai poistaa SSH-julkisia avaimia määritetyn käyttäjätilin tiedostoihin
  - user: käyttäjä jonka avaimia muokataan
  - key: SSH avain


A) <img width="416" height="261" alt="image" src="https://github.com/user-attachments/assets/800034d1-878e-421f-ab33-627336703d8b" />

<img width="526" height="299" alt="image" src="https://github.com/user-attachments/assets/462eee7e-10f7-4dba-887e-a12fa83b89bd" />
<img width="797" height="281" alt="image" src="https://github.com/user-attachments/assets/0e7a94b8-b965-4911-b6ca-8d85087938c8" />


B)
Sudo ilman salasanaa
Seurasin tehtävässä Karvinen 2026: Passwordless Sudo with Ansible ohjetta. 
Ensin loin main.yml tiedostoon tarvittavan ryhmän ja käyttäjän ja asetin tarvittavat tiedot.
<img width="818" height="370" alt="image" src="https://github.com/user-attachments/assets/ec7fa164-8e51-43d9-9f7a-60c231f0eebc" />

Tämän jälkeen muokkasin site.yml tiedostoa jotta saa pääkäyttäjä oikeudet käyttöön

<img width="232" height="146" alt="image" src="https://github.com/user-attachments/assets/24a7c750-07f1-45eb-a58d-9a00b1b3b07f" />

määritin Ansiblen käyttämään anteroa oletuksena, jolla ratkaisin ongleman "missing sudo password" 

<img width="151" height="115" alt="image" src="https://github.com/user-attachments/assets/4c37cfb7-ec39-4fe1-bff0-a2090bb04d52" />

Kohtasin ongelmia tehtävässä kun esimerkiksi koitin suorittaa "ansible-playbook site.yml" ja vastaus oli että tiedosta ei löydy, mutta tästä selvisin siirtämällä 
roles/antero oikeaan kansioon.

<img width="552" height="458" alt="image" src="https://github.com/user-attachments/assets/4a936efc-c126-4cbd-9897-fb0afd9c3eb0" />

Myös kohtasin jonkin verran kirjoitusvirheitä nano tiedostoissa.
 

C) Asensin kaksi pakettia Curl ja Git muokkaamalla main.yml tiedostoon

<img width="739" height="343" alt="image" src="https://github.com/user-attachments/assets/702b1ac3-4992-41f0-aaac-38b89a0d0b9d" />

Kuvassa näkyvät alimmat kohdat, apuna käytin Ansible community documentation nettisivua sekä Google Gemini tekoälyä. https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/apt_module.html

D) 
Loin monirivisen teksti tiedoston Ansiblen Copy työkalulla ja asetin sille 0600 oikeudet eli vain tiedoston omistaja voi lukea tai kirjoittaa siihen.

<img width="278" height="157" alt="image" src="https://github.com/user-attachments/assets/d5c4477d-475b-4f61-ad20-7b924299c453" />

Sijoitin tiedoston anteron kotihakemistoon ja omistajaksi ja omistajaryhmäksi laitoin anteron.


<img width="791" height="409" alt="image" src="https://github.com/user-attachments/assets/d2a87ab2-f312-4235-8247-12134c0574f5" />

<img width="811" height="433" alt="image" src="https://github.com/user-attachments/assets/ae025d98-844c-4e9c-ac36-20054d161f56" />

suoritin komennot "ansible-playbook site.yml ja sen jälkeen kokeilin ls -l /home/antero/tervehdys.txt komentoa joka palautti virheen " permission denied", koska tiedosto sijaitsee /home/antero , ei tavallisilla käyttäjillä ole pääsyä sinne joten kun kokeilin uudestaan sudo ls ... tuloste oli:

<img width="497" height="27" alt="image" src="https://github.com/user-attachments/assets/106c1420-3ffb-4688-8421-6f6fd356933c" />

Apuna käytin ansible community documentation ansible.builtin.copy module - Copy files to remote locations. sivua.


https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/copy_module.html





E) Debug
Tehtävässä valitsin ansiblen ydin moduuleista debugin, jonka avulla voi esim saada vahvistusviestin tulostettua suorituksen jälkeen.

<img width="206" height="89" alt="image" src="https://github.com/user-attachments/assets/856198a9-f6dd-437f-a6b1-1622f1a9a4fc" />

Lisäsin roles/antero/tasks/main.yml nano tiedostoon kuvassa näkyvän pätkän.

<img width="833" height="458" alt="image" src="https://github.com/user-attachments/assets/d1c77f94-5a53-40ce-8947-1a723eeaacc5" />

Ja kun playbookin suoritti oli vahvistus viesti mukana.

ansible-doc debug


https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/debug_module.html

Lähteet:

Red Hat Ansible Documentation:

copy-moduuli: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html

apt-moduuli: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html

file-moduuli: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html

user-moduuli: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html

debug-moduuli: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/debug_module.html

chmod(1): https://man7.org/linux/man-pages/man1/chmod.1.html

getent(1): https://man7.org/linux/man-pages/man1/getent.1.html

Karvinen 2026: https://terokarvinen.com/passwordless-sudo-with-ansible/

Karvinen 2026: https://terokarvinen.com/passwordless-sudo/

Munroe 2026: https://xkcd.com/149/
