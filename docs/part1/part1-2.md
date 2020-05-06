---
title: "1. C++ ohjelma"
permalink: /part1/2/
nav_order: 2
published: true
parent: "C++ lyhyesti, 1. ohjelma ja perusrakenteet"
---

## 1. C++ ohjelma

Ensimmäinen C++ -ohjelmamme näyttää siis seuraavalta:

![](/assets/images/1_ohjelma.png)

C++ ohjelman rakenne koostuu seuraavista osista

| Materiaalin osa | Tarkoitus | Esimerkki 
|----------|-------------|-------------|
| Avainsanat | Sanat, joilla on erityinen merkitys kääntäjälle | int, float, if, float
| Tunnisteet | Sanat jotka eivät ole rakennettu kieleen | cout, std, x, funktio
| Literaalit | Sanat, jotka suoraan koodissa määrittivät arvon | "Hello, world!", 24.3, 0, ’c’
| Operaattori | Matemaattiset tai loogiset operaatiot | +, -, &&, %, <<
| Välimerkit / Erottimet | Merkit jotka luovat rakennetta | { } ( ) , ;
| Tyhjät merkit | Tyhjät merkit, joilla ei ole kääntäjälle merkitystä | Välit, tab-merkit, rivinvaihto 


**Esimerkki-ohjelman selitys rivi-riviltä**

1. Rivit jotka alkavat # merkillä ovat niin sanottuja _**esikääntäjän**_ komentoja, ne muuttavat kirjoitettua lähdekoodia joka välitetään varsinaiselle kääntäjälle. _**#include**_ komento kertoo esikääntäjälle, että tähän kohtaan sisällytetään sen tiedoston sisältö joka _**< >-merkkien**_ sisään on kirjoitettu. Esimerkissä käytämme _**iostream tiedostoa**_ joka antaa käyttöömme C++:sen syöte / tulostusfunktiot.
_**#include-komennolla**_ voidaan hakea tiedostoja joko käyttäjän/projektin omista poluista käyttämällä lainausmerkkejä esim. _**#include ”oma_header.h”**_ tai sitten järjestelmänpoluista käyttämällä nuolimerkkejä kuten esimerkissä. 
2. _**using namespace std;**_ , C++:ssa funktioita voidaan kasata osaksi nimiavaruuksia (namespace), jotta niiden hallinta ja erottelu olisi helpompaa. Tätä käsitellään myöhemmin kurssilla. Nyt riittää tietää, että komennolla määritellään, että tässä koodissa käytetään _**std-nimiavaruuden**_ funktioita/muuttujia. Nämä funktiot tulevat edellä mainitusta _**iostream-tiedostosta**_. 
3. Jokainen C++ ohjelma sisältää yhden _**int main()**_ -funktion, tämä on ohjelman kohta, josta kaikki ohjelman suoritus alkaa. Funktio palauttaa kokonaismuuttuja tyyppisen arvon _**(int)**_ sille ohjelmalle, joka on ohjelmamme on käynnistänyt. Yleensä tämä arvo on 0, jos ohjelma on suoriutunut onnistuneesti. Muut arvot kuvaavat virhetilanteita ohjelmassa. main()-funktion sisältö on rajattu lohkoksi _**{...}-merkein**_.
4. _**cout << "Hello World!" << endl;**_:
    - _**cout << **_, kertoo kääntäjälle että haluamma tulostaa ruudulle jotain, tämä jotain seuraa << -merkin jälkeen.
    - _**"Hello World!"**_, määrittää tähän kohtaan tekstityyppisen literaalin
    -  _**<< endl;**_, yhdistää seuraavaksi tulostukseen _**endl;**_ avainsanan, joka tarkoittaa rivinvaihtoa
5. _**main-funktion **_lopussa on edellä mainittu ohjelman lopetus, tämä lopetus palauttaa 0 arvon. 


> **Oppimistehtäviä:**
> 
> - Koeta kopioida rivi _**cout << "Hello World!" << endl;**_ ja liittää se olemassa olevan rivin alle. Muuta rivin sisältöä, niin että se tulostaa oman nimesi.
>
> - Muuta _**return 0;**_ -> _**return 1;**_ , tapahtuuko mitään?
> 
> - Entä jos poistat _**{**_ -merkin, millaisia virheitä saat?, palauta nyt _**{**_ -merkki
> 
> - Lisää \\n sanan _**Hello**_ jälkeen, mitä tapahtuu? Testaa myös seuraavat \\t, \\\\, \\"


> Jos kirjoitat koodia joka ei ole kelvollinen C++ -kääntäjälle, QtCreator ilmoittaa siitä virheellä:![](/assets/images/virhe_idessa.png)
> Näet miltä riviltä virhe löytyy sekä minkälainen virhe on kyseessä. Tuplaklikkaa riviä ja IDE avaa sinulle sen rivin jolla virhe on.
