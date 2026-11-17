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


  
