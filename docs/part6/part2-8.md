---
title: "OOP - Polymorphismi"
permalink: /part6/6/
nav_order: 4
published: true
parent: "Osa 6. Luokat"
---

# Polymorphismi

Polymorphismilla tarkoitetaan olio-ohjelmoinnissa, että oliolla on "monia muotoja". Edellisen osion HenkiloAuto on myös Auto, kuten KuormaAuto on myös Auto.

Polymorphismita on hyötyä kun haluamme toteuttaa toiminnallisuuksia, jotka ovat yleisiä oliolle jotka on muodostettu samasta isäntäluokasta. Samoin jos haluamme välittää olion funktiolle voimme hyödyntää polymorphismia ja käyttää funktion parametrityyppinä isäntäluokkaa.

Polymorphismin osalta on muutama asia, joita ohjelmoijan tulee noudattaa jotta toiminta on oikea. Toteutetaan Auto-luokkaan funktio:

```c++
//auto.h:n uusi julkinen jäsenfunktio
void aanimerkki();

//auto.cpp, funktion toteutus
void Auto::aanimerkki()
{
    cout << "geneerinen Auto ei anna äänimerkkiä" << endl;
}
```

Sekä vastaavat toteutukset HenkiloAuto ja KuormaAuto luokkiin. (HUOM!) joudut lisäämään .cpp tiedostoihin oikeat includet ja nimiavaruuden std cout -funktion käyttämiseksi.

```c++
//henkiloauto.h:n uusi julkinen jäsenfunktio
void aanimerkki();

//henkiloauto.cpp, funktion toteutus
void HenkiloAuto::aanimerkki()
{
    cout << "tööt tööt" << endl;
}
```

```c++
//kuormaauto.h:n uusi julkinen jäsenfunktio
void aanimerkki();

//kuormaauto.cpp, funktion toteutus
void KuormaAuto::aanimerkki()
{
    cout << "TUUT TUUT" << endl;
}

```

Nyt jos käytämme muutettuja luokkiamme main.cpp tiedostossa.

```c++
//HUOM! pitää käyttää viittausta, jotta emme kopioi oliota a1 uuteen olioon
Auto& geneerinenAuto = a1;
geneerinenAuto.aanimerkki();
```

On tuloksena tuloste

```c++
geneerinen Auto ei anna äänimerkkiä
```

Toiminta on tavallaan ok, eli kutsumme isäntäolion aanimerkki funktiota. Mutta toisaalta perityt luokamme toteuttaisivat omat aanimerkki()-funktio joita oikeasti haluaisimme kutsua. Jotta voisimme toteuttaa tämän halutusti tarvitsemme virtuaalisia funktoita.

## Virtuaaliset funktiot

Virtuaalimetodi tai virtuaalifunktio (virtual function) on olio-ohjelmointikielien ominaisuus, jolla perintää käyttävä olio voi korvata yliluokassa olevan funktion toteutuksen toisella. 

Mikäli perityssä luokassa ei ole toteutusta virtuaalimetodille kutsut tehdään isäntäluokan toteutukseen. 

Kun haluamme funktiosta virtuaaliset laitamme sen eteen määritteen virtual.

```c++
//auto.h
virtual void aanimerkki();
```

Nyt toteutuksemme tulostaa halutusti.

```c++
tööt tööt
```

Tätä toiminnallisuutta kutsutaan dynaamiseksi suorittamiseksi (dynamic dispatch). Olio selvittää ajonaikana itse mitä funktiota tulisi kutsua.

## Abstarkti pure virtual funktio

Abstrakti pure virtual funktio, jolla ei ole toteutusta kantaluokassa on pakko toteuttaa perityssä luokassa. Tämän myötä voidaan esim. isäntä-luokassa kertoa, että funktio toteutetaan perivissä luokissa. Jos luokassa on yksikin abstrakti pure virtual funktio ei siitä voi luoda oliota.

Luodaan Auto-luokkaan funktio kaynnista() joka on abstrakti pure virtual funktio.

```c++
virtual void kaynnista() = 0;
```

Nyt ohjelmamme ei kelpaa kääntäjälle, ennenkuin olemme toteuttaneet kaynnista()-funktion KuormaAuto ja HenkiloAuto -luokassa.


```c++
//kuormaauto.h ja henkiloauto.h luodaan esittely
void kaynnista();

//seka toteutukset - kuormaauto.h ja henkiloauto.cpp
void KuormaAuto::kaynnista()
{

}

void HenkiloAuto::kaynnista()
{

}
```


## Tehtävät

Toteuta edellisen osion tehtävien jatkoksi:

1. Toteuta Ajoneuvo luokkaan virtuaalinen fuktio void kuvaile(), joka kuvailee luokkaa sekä toteuta kuvaile() funktio Skootteri ja VesiSkootteri luokissa. Käytä luokkia pääohjelmassa.

2. Ajoneuvo -luokkaa abstrakti virtuaalinen funktio henkilot(), joka kertoo kuinka monta henkilo voi kyseisessä kulkuneuvossa olla. Toteuta funktio Skootteri ja Vesiskootteri luokassa.

3. Toteuta pääohjelmaan funktio tulostaAujoneuvo, jolle välitetään viitteenä paramaterina Ajoneuvo-olio ja funktio kutsuu tämän olion kuvaile() funktiota.



