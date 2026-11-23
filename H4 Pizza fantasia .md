x) Lue ja tiivistä.
Karvinen 2023: Configuration Management of Distributed Systems over Unreliable and Hostile Networks (pdf, ̣mirrors: local, archive.org), vain nämä kohdat:
4.12.1 Size and Complexity of Some DSLs 
  - Salt työkalussa yli 510 funktiota, yli 20 000 riviä tekstiä ja 75 000 sanaa.
  - DSL:S voivat kasvaa erittäin suuriksi ja monimutkaisiksi
  - Puppet:issa on 113 valmista funktiota
  - Omahuomio: Vaikka tarkoitus olisi yksinkertaistaa palvelinten hallintaa DSL kielten avulla, voi se käyttäjälle osoittautua erittäin raskaaksi opetella yli 500 funktiota.

4.12.2 Use of DSL Functions in Case Configuration
  - Käytetyimmät funktiot toimivat siten että demonit määritetään package-file-service mallilla ja käyttäjä ohjelmat package-file mallilla
  - Vaikka funktioita on todella paljon, selviää vain muutamilla perus funktiolla
  - Yli 1% käytettyjä komentoja on vain 12, ja niistä funktioita 4
  - Omahuomio: Hieno huomata että pääasiassa voi pärjätä samalla mallilla jota me harjoittelemme Package-file-service

4.12.3.1 Dependencies Between Main Functions
  - Yleisimmät toiminnot (package, file, service, user, group)
  - Idempotenssi toteutetaan yksinkertaisesti, muutoksia tehdään vain jos systeemi ei ole oikeassa tilassa.
  - Ensin käsin, sitten automatisoidaan

A) Räpylä

Aloitin Caddyn asennuksen sammuttamalla Nginx:in jotta saan portin 80 vapautettua

<img width="563" height="99" alt="image" src="https://github.com/user-attachments/assets/7810d632-f7d7-46a9-97a0-e19f941f609c" />

Sitten asensin Caddyn ja päivitin (sudo apt update)

<img width="605" height="384" alt="image" src="https://github.com/user-attachments/assets/6ede18b0-fa61-48dd-8d05-52473ef79bad" />

Sitten testasin toimivuuden

<img width="434" height="230" alt="image" src="https://github.com/user-attachments/assets/2a39a054-806f-4c74-aae1-217a54563dbf" />

B) Automatisointi
