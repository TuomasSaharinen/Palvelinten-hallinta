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


<img width="791" height="409" alt="image" src="https://github.com/user-attachments/assets/d2a87ab2-f312-4235-8247-12134c0574f5" />

<img width="811" height="433" alt="image" src="https://github.com/user-attachments/assets/ae025d98-844c-4e9c-ac36-20054d161f56" />




E)
