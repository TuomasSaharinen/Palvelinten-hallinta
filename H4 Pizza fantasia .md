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
  -
