X) lue ja tiivistä
  1. Karvinen 2026 Apache installed with Ansible -quick notes
     - Asennetaan verkkopalvelin paketti : sudo apt-get install Apache2
     - muokataan tiedostoja : sudoedit /etc/apache2/...
     - Käynnistetään uudelleen jotta muutokset tulevat voimaan : sudo systemctl restart apache2

  2. Ansible community documentation: Handlers running operations on change
     - Handlerit ovat tavallisia tehtäviä jotka suoritetaan vasta kun toinen tehtävä ilmoittaa tehneensä muutoksen
     - Handlereita kutstuaan notify avainsanalla jotta vältytään turhilta uudelleenkäynnistyksiltä vaikka mitään ei olisi muutettu
     - Suoritetaan playbookin lopussa

  3. Ansible-doc service
     - hallinnoi palveluilta 
     - Name on palvelun pakollinen nimi
     - state palvelun tilaa (started, stopped...)
     - enabled määrittää käynnistyykö automaattisesti

Y) Infra uutiset : https://news.ycombinator.com/item?id=46449852 

  Artikkeli: Show HN: Enroll, a tool to reverse-engineer servers into Ansible config mgmt
  (Tammikuu 2026)
  - Enroll skannaa olemassa olevan linux-palvelimen paketit, palvelut ja poikkeavat asetustiedostot ja tekee niistä suoraan Ansible playbookit
  - Enroll harvest ja enroll manifest
  - Voidaan käyttää paikallisesti tai Ssh:n yli

A) Apassi
Aloitin lataamalla päivitykset 
sudo apt update
ja sitten latasin apachen 
sudo apt-get install apache2

<img width="856" height="489" alt="image" src="https://github.com/user-attachments/assets/05b5926d-ecb1-4d9d-b158-4ec53c1fa0f2" />

Sitten loin kansion ja tekstitiedoston

<img width="399" height="38" alt="image" src="https://github.com/user-attachments/assets/fa15f40a-fb93-4b18-a469-23972c848ab1" />

Annoin oikeudet x kansiohion ja r oikeudet tiedostoihin

<img width="369" height="49" alt="image" src="https://github.com/user-attachments/assets/f7c7ed91-7be5-468b-a6cf-c84b97135d03" />

sitten ohjasin apachen uuteen kansioon jotta se löytyy

<img width="308" height="111" alt="image" src="https://github.com/user-attachments/assets/30990ae4-8f7e-4bf1-a348-151644501b3a" />

Tämän jälkeen sallin turva-asetuksista kotihakemiston lukemisen menemällä apachen pää asetustiedostoon ja lisäämällä loppuun:

<img width="636" height="415" alt="image" src="https://github.com/user-attachments/assets/0a7c3d00-3fe6-40b5-81ed-d541d8e1319e" />

Uudelleen käynnistyksen jälkeen yhteyden otolla sain vastauksen 

<img width="339" height="58" alt="image" src="https://github.com/user-attachments/assets/62d013b1-5e0f-4436-8c2a-85d4657667b3" />

B) Moottorix

Aloitin sammuttamalla apachen ja sen jälkeen lataamalla nginx

<img width="816" height="411" alt="image" src="https://github.com/user-attachments/assets/af046a09-543e-46ef-93b6-3258867171f8" />

Ohjasin nginx kotihakemistooni samalla tavalla kuin apachen

<img width="517" height="431" alt="image" src="https://github.com/user-attachments/assets/9f906527-4524-49ea-9fc5-14658a06cd40" />

taas yhteydenotolla tulostui sama apassi toimii joten onnistuin.

<img width="515" height="133" alt="image" src="https://github.com/user-attachments/assets/217fc830-6305-4bb4-b0f9-893a3fface61" />

C) Automoottorix
aloitin poistamalla vanhan nginx ja sen asennustiedostot

<img width="511" height="255" alt="image" src="https://github.com/user-attachments/assets/9d33f347-9a7a-4ac1-8e63-cd6cc3ca8e1f" />

ja tämän jälkeen luon ansiblelle hakemistot ja tarvittavat alihakemistot

<img width="483" height="44" alt="image" src="https://github.com/user-attachments/assets/1186321c-6f51-4bc2-8286-413eb83968a2" />




Lähteet:
https://nginx.org/en/docs/beginners_guide.html
https://terokarvinen.com/apache-ansible/
https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html
https://news.ycombinator.com/item?id=46449852
Ansible documentaatio sivut
