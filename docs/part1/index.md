---
title: "C++ lyhyesti, 1. ohjelma ja perusrakenteet"
permalink: /part1/
nav_order: 3
published: true
has_children: true
has_toc: true
---

## Osa 1 - C++ lyhyesti

C++ on tehokas ohjelmointikieli, jota käytetään matalantason ohjelmien rakentamisessa. Nämä ohjelmat toimivat usein käyttöjärjestelmien perustana, sekä erilaisten laitteiden ohjaajina. C++ on vanha ohjelmointikieli, mutta se on vuosien varrella laajentunut sekä kehittynyt, ja sillä on mahdollista koodata niin pieniä sovelluksia kuin käyttöliittymän sisältäviä laajoja ohjelmia. C++ on laiteläheinen kieli, joten sillä kirjoitetuista ohjelmista on mahdollista saada hyvin tehokkaita. C++ ei itsessään sisällä suurta määrää laajennuksia, kuten esim. CSV-tiedostojen käsittelyyn tai vaikkapa käyttöliittymien rakentamiseen, mutta eri organisaatiot ja käyttäjät ovat laajentaneet C++:aa kirjastoilla. Nämä kirjastot ovat saatavilla maksutta tai maksullisina riippuen kirjaston käyttötarkoituksesta. Näin ollen lähes mikä tahansa sovellus voidaan rakentaa C++:lla. C++ on käytössä monissa yrityksissä ja mitä lähemmäs laitteiden ohjaamista työ menee sitä varmemmin yritys käyttää C++ ohjelmointikielenä. C++:n historiaa ei tällä kurssilla käydä läpi, mutta esim. GeeksForGeeks sivustolla on aiheesta hyvä
kuvaus, tämä löytyy osoitteesta: https://www.geeksforgeeks.org/history-of-c/



![C++ historia](assetss/images/History-of-C.jpg)

_Kuva 1. C++ Historia (GeeksForGeeks)_

C++ vaatii ohjelmoijalta taitoja, joiden vuoksi se on haastavan kielen maineessa. Tämä johtuu osittain C++:n historiasta, mutta pääasiassa siitä, että C++ on kielenä laiteläheinen. Muun muassa muistinhallinta ja tiedostojen käsittely on monessa muassa ohjelmointikielessä yksinkertaisempaa kuin C++:ssa, joten sillä on helppo tehdä virheitä, jotka aiheuttavat ohjelmien kaatumisen ja erilaiset virhetilanteet. Toisaalta ohjelmoijalla on lähes kaikki valta kun ohjelmoidaan C++:lla joten hän
pystyy hallitsemaan sovelluksen käyttäytymistä hyvin hienojakoisesti. Tällä kurssilla opiskelija perehtyy C++:aan niin, että hallitsee sen perusteet ja osaa luoda C++:lla sovelluksia, jotka on kirjoitettu laadukkaasti. 

Seuraavassa on kuvattuna joitain tunnuspiirteitä, jotka ovat C++:lle ominaisia:
- Yksinkertaisuus ja loogisuus, C++ muistuttaa luonnollista kieltä, ja sillä kirjoitetut ohjelmat voidaan paloitella loogisiin kokonaisuuksiin, joita on yksinkertaista hallita.
- Laiteriippumaton, mutta alustariippuvainen, C++ sovellukselle pitää määrittää
käännettäessä alusta, jolla sovellus toimii (esim. Linux tai Windows). Jokaiselle alustalle tulee kääntää oma versio lähdekoodista. Tämä tekee C++ sovelluksesta kuitenkin laiteriippumattoman, eli sama koodi toimii useissa laitteissa, kunhan ne toimivat samalla alustalla.
- Keskitason kieli, C++ kuuluu ohjelmointikielien kategoriaan, jolla voidaan tehdä niin laitteiden ohjelmointia kuin laajoja sovelluksia.
- Laaja tukikirjasto, C++:lle löytyy laaja joukko kirjastoja, joita käyttäjät ovat kirjoittaneet laajentamaan C++:n perusominaisuuksia.
- Nopeus, C++:lla kirjoitetut sovellukset saadaan optimoitua nopeiksi, koska suoritettava sovellus on konekielistä koodia. C++:ssa ei ole automaattista muistinhallintaa, roskienkeruuta tai muita ominaisuuksia, jotka helpottavat ohjelmoijaa, mutta aiheuttavat suoritettaessa ”ylimääräistä” resurssien käyttöä.
- Osoittimet ja suora muistinhallinta, C++:lla voidaan käyttää osoittimia ja hallita suoraan muistiin tallennettua tietoa. Tästä on hyötyä kun toteutetaan matalantason ohjelmia, kuten laiteohjaimia.
- Olio-ohjelmointi, vaikka C++ ei ole puhdas olio-ohjelmointi kieli mutta luetaan olioohjelmointikieleksi. Siinä ei tarvitse pakosta käyttää oliota, mutta oliopohjaisuus on C++:ssan yksi tärkeimmistä piirteistä oliot. Olioiden ja luokkien avulla voidaan tehdä sovelluksia, jotka ovat siirrettäviä ja ylläpidoltaan kevyitä

C++:lla luotuja sovelluksia ovat mm.:
- Käyttöjärjestelmät
- Selaimet
- Grafiikka ja pelimoottorit
- Tietokantapalvelimet
- Useat pilvi- / hajautetut järjestelmät
- Sulautettujen järjestelmien sovellukset

### Kääntäminen 

C++ on ohjelmointikieli, joka on ”helposti” luettavissa ihmiselle, sillä kirjoitettu koodi muistuttaa ulkoasultaan mitä tahansa tekstiä. Tämä tarkoittaa sitä, että C++:lla kirjoitetut ohjelmat pitää **_kääntää (compile)_** tietokoneen ymmärtämään muotoon. Tämän suorittaa _**kääntäjä (compiler)**_, jolle annetaan syötteenä C++:lla kirjoitetut tiedostot eli _**lähdekoodi (source code)**_. Kääntäjä tulkitsee C++:lla kirjoitetun ohjelman ja muuntaa sen konekieliseksi suoritettavaksi tiedostoksi _**(executable file)**_. 

Konekieliset tiedostot voidaan suorittaa suoraan tietokoneella tai muulla laitteella, nämä suoritettavat tiedostot ovat pääasiassa _**.exe muotoisia ajettavia ohjelmia**_ tai _**.dll muotoisia kirjastoja.**_ 
Konekielinen tiedosto on binäärikoodia, ja sen muodostuminen riippuu siitä, mille ympäristölle ja suorittimelle ohjelma on tarkoitettu. C++:lla voidaan siis kirjoittaa sovelluksia eri laitteille, mutta ajettavat ohjelmat tulee kääntää kohdistumaan tietylle alustalle (vrt. käyttöjärjestelmä). Näin ollen C++:lla käännettäviä ohjelmia voidaan suorittaa vain määritetyissä ympäristöissä.

Kääntäminen ja kääntäjä eivät sisälly tämän kurssin aihealueeseen, mutta seuraavassa on kuvattu kääntäjän toimintaa yleisesti. Lisätietoja kääntäjästä voi lukea esim.
https://binarymove.com/2018/12/01/how-c-works-ides-compilers-linkers/

![](/assets/images/compiler.png)
_Kuva 2. Kääntäjän toiminta_

C++ ohjelmaa kirjoitettaessa kääntäjälle toimitetaan vähintään .cpp lähdekoodi, jonka kääntäjä tulkkaa konekieliseksi. Laajemmissa sovelluksissa kääntäjälle toimitetaan useita _lähdekooditiedostoja (.cpp)_ tiedostoja, sekä niin liittyvät _otsikkotiedostot (header file, .h)_. Otsikko- ja lähdekooditiedostoista puhutaan myöhemmin lisää. Kääntäjän toimintaa yleisesti on esitetty seuraavassa kuvassa.


![](/assets/images/compiler2.png)
_Kuva 3. Kääntäjän toiminta_

Kääntäjästä kannattaa käydä lukemassa seuraava kirjoitus, jossei heti niin vähintään kun kurssi on loppupuolella:
https://www.fi.freelancer.com/community/articles/how-c-works-understanding-compilation

