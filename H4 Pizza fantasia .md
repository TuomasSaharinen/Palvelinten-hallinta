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

Aloitin luomalla tarvittavat alikansiot

<img width="383" height="50" alt="image" src="https://github.com/user-attachments/assets/c4f5a72d-9c9a-4fa6-b53d-3357d9d8cfc3" />

Tein mallipohjan jotta testauksen yhteydessä portista 80 palautuu caddy toimii!

<img width="463" height="100" alt="image" src="https://github.com/user-attachments/assets/ea538901-a47f-4fa0-83a6-45b37a0fe536" />

Loin tehtävät

<img width="176" height="260" alt="image" src="https://github.com/user-attachments/assets/a3330df8-67fe-4d05-b8bc-43cd8a49a9df" />

Jonka jälkeen loin handlerin

<img width="461" height="107" alt="image" src="https://github.com/user-attachments/assets/21c51e42-3973-43a0-99ca-fb8678412d45" />

ja sitten loin playbookin

<img width="469" height="116" alt="image" src="https://github.com/user-attachments/assets/f774212a-e278-45b1-bb51-0193116c699c" />

ja tämän jälkeen ajoin playbookin ja testasin toimivuuden ja palautuksena tuli 

<img width="415" height="243" alt="image" src="https://github.com/user-attachments/assets/57e89ea8-11ea-4b15-bf52-5c7c4b4c814a" />

c) Asetus
Muutin asetustiedoston palauttamaa tekstiä

<img width="536" height="98" alt="image" src="https://github.com/user-attachments/assets/fe078aaa-a73e-49c7-bdfa-54fbc23a9562" />

jonka jälkeen ajoin playbookin jossa tuli 2 muutosta

<img width="625" height="232" alt="image" src="https://github.com/user-attachments/assets/e1de5f37-554f-4a70-89ea-50e0164459a9" />

ja sitten vielä curl komennolla testaus

<img width="255" height="40" alt="image" src="https://github.com/user-attachments/assets/98e5ed18-554a-4acd-8b27-b64787594765" />

D)




Lähteet:
https://www.golinuxcloud.com/ansible-idempotency/ (luettu 23.11.26)
https://westminsterresearch.westminster.ac.uk/item/w7vvz/configuration-management-of-distributed-systems-over-unreliable-and-hostile-networks (luettu 23.11.26)
https://docs.ansible.com/projects/ansible/3/user_guide/playbooks_handlers.htm (luettu 23.11.26)


