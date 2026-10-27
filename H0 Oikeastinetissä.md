a) asensin debian 13 virtualboxiini. käytin apuna Punnala 2025: tietokone ja käyttöjärjestelmä ohjetta.
Noudatin Punnalan ohjetta täsmällisesti Virtual box guest addtition kohtaan saakka. koko asennukseen minulla kului noin 1 tunti.
Lisäsin kuvia eri työvaiheista omaan kuva kansioon, josta näkee esim. että nettiyhteys toimi, sekä että sain päivitettyä sudo komenolla uusimpiin vaiheisiin ja sain palomuurin päälle ja siihen ssh:lle "reiän" komenolla sudo ufw allow ssh ja tarkistamalla sen sudo ufw status . Tähän hyödynsin Google Geminiä kysymällä "How to open ssh on debian ufw" 

Weppipalvelimen asennus: Asensin apache2 palvelimen komennolla sudo apt-get -y install apache2 . Tämän komennon sain Punnalan h3-hello-web-server raportista (punnala 2025)
asennuksen jälkeen kokeilin toimivuutta komennolla sudo systemctl status apache2, Tulostuksesta on kuva kuvat kanisossa. Kun tulostus osoitti että web palvelin oli päällä ja enabloitu testasin että se vastaa localhost osoitteesta komennolla curl localhost , johon vastaus oli html muodossa oleva websivu.

Tehtävä X
Niemi 2025: H4 tehtävät
- Hyvä ohje raportti pilvipalvelimen vuokraukseen ja virtuaalipalvelimen alkutoimiin.
- ufw allow 22/tcp
- ufw status

Partanen 2025 Harjoitus 5
- Namecheapista saa halpoja domaineja
- Miksi alidomaineja tarvitaan?



Lähteet: 
https://github.com/punnalathomas/linux-course/blob/main/h1-installing-linux.md Luettu 23.10.2026
https://github.com/AONCODES/linux-course/blob/main/h4.md Luettu 23.10.2026
https://partanennn.github.io/linux-servers/practices/fifth-week.html Luettu 23.10.2026
Google gemini
https://linuxcapable.com/how-to-install-apache-on-debian-linux/ Luettu 23.10.2026
