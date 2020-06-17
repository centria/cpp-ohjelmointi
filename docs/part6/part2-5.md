---
title: "Luokat omissa tiedostoissa"
permalink: /part6/3/
nav_order: 1
published: false
parent: "Osa 6. Luokat"
---

# Osa 6b - Luokat osa 2

## Johdanto

Kurssilla on tähän mennessä käyty läpi koodin kirjoittamista yhteen tiedostoon, käyttäen funktioita ja luokkia.. Kuitenkin jo yksinkertaisen esimerkkimme ja tehtävien avulla huomaamme, että tämä ei ole jatkuvuuden, ylläpidon tai ylipäätään yleisen projektin hallinnan kannalta järkevä tapa. 

Olemme käyttäneet tähän mennessä myös muiden kehittämiä, ja C++:n standardijakeluun kuuluvia otsikkotiedostoja ().h). Kuitenkin ohjelmamme kasvaessa tarvitsemme omia otsikkotiedostoja ja koodin jakamista tiedostoihin.  

## Otsikko- ja lähdekooditiedostot

Koodi voidaan jakaa C++:ssa, seuraavasti:

- Otsikkotiedostot (header-files, .h) sisältävät funktioiden esittelyt, luokat sekä muuttujat 

- Lähdekooditiedostot (source-files, .cpp) sisältävät määrittelyt edellisille 


Jakaminen otsikkoihin ja lähdekoodiin on esitetty seuraavassa kuvassa.
![](2020-06-16-08-11-48.png)

Ohjelmaa käännettäessä kääntäjä lukee aluksi sisään ne lähdekooditiedostot, jotka ohjelmoija kääntäjälle lähettää. Lähettäminen tehdään usein IDEn toimesta, mutta joskus ohjelmoijan tulee hallita tätä itse (mm. Makefilen avulla). Näissä lähdekooditiedostoissa (kuten main.cpp) on lueteltuna ne otsikkotiedostot, joiden esittelyitä lähdekooditiedosto tarvitsee. Näin kerrotaan kääntäjälle, että seuraavat funktiot / oliot ovat käytettävissä. Seuraavassa vaiheessa kun kääntäjä luo lähdekoodista koodikieliset versiot se linkittää otsikkotiedoston viitteet oikeisiin kohtiin koodikielisessä versiossa. 

![](2020-06-16-08-12-36.png)


On myös mahdollista, kirjoittaessa omia lähdekooditiedostoja (.cpp), kertoa lähdekooditiedostossa, että tämä tiedosto käyttää funktio/luokkaa, joka on määritelty toisessa tiedostossa (.h). Näin kaikkia otsikkotiedostoja ei tarvitse kasata pääohjelmaan (main.cpp). Tätä on havainnollistettu seuraavassa: 
![](2020-06-16-08-13-02.png)

Nyt auto.cpp käyttää ratti.h tiedostoa.

## Luokkien toteuttaminen .h ja .cpp -tiedostoissa

C++:ssa luokan määrittely kannattaa tehdä omaan .h tiedostoon. Esim. Auto-luokan määrittely tehdään auto.h tiedostoon. Ja itse funktiot, jotka luokka toteuttaa tulevat auto.cpp -tiedostoon. 

Qt-Creatorissa luokan tekeminen on helppoa. Kun luokka tehdään IDEn UI:n kautta ei koodarin tarvitse huolehtia kääntäjän manuaalisesta konfiguroinnista. Tee uusi luokka seuraavasti: Klikkaa oikealla napilla projektin kansiota ja valitse **”Add new…”**  

![](2020-06-16-08-22-30.png)

Seuraavasta ikkunasta valitse **C++ luokka**:
![](2020-06-16-08-22-54.png)

Kirjoita seuraavaksi luokan nimi ja valitse **”Continue”** ja seuraavasta ikkunasta **”Done”**:
![](2020-06-16-08-24-03.png)

Nyt Qt-Creator on luonnut luokan rungon valmiiksi, ja jakanut luokan määrittelyt .h tiedostoon sekä alustanut .cpp tiedoston.  

Otsikkotiedostoon .h on tehty seuraavat määritykset:

```c++
#ifndef AUTO_H
#define AUTO_H


class Auto
{
public:
    Auto();
};

#endif // AUTO_H

```

**#ifndef** rivi kertoo kääntäjälle, että jos AUTO_H määritettä ei ole esitelty kääntäjälle, jatketaan seuraavien rivien käsittelyä. Jos AUTO_H on esitelty kääntäjälle tiedoston käsittely lopetetaan. Tämän tarkoituksena on estää luokan määrittely useamaan kertaan. Jos luokka määriteltäisiin useasti kääntäjälle, kääntäjä ei tietäisi mikä määrittely on oikea. Tämä rivi on oleellinen, jos otsikkotiedostoa käytetään useassa lähdekooditiedostossa. 


**#define** rivi määrittelee kääntäjälle AUTO_H määritteen, tämän jälkeen kääntäjällä on AUTO_H määrite tiedossa. vrt. edellinen rivi.

**class Auto** rivi kertoo kääntäjälle, että tästä alkaa Auto-luokan määrittely, seuraavalla riville tulee kaarisulke { joka aloittaa varsinaisen määrittelyn, huomaa että määrittely loppuu kaarisulku ja ; yhdistelmään };. 

Seuraavaksi tutustumme itse luokan lähdekoodiin Qt-Creatorin luoma toteutus (auto.cpp) näyttää tältä: 

```c++
#include "auto.h"

Auto::Auto()
{

}

```

Tässä on aluksi kerrottu kääntäjälle, että tämä luokka on määritelty ”auto.h” -tiedostossa. 


Tämän jälkeen määritellään Auto() rakentajan sisältö, huomaa että rakentaja (kuten ei myöskään hävittäjä) palauta mitään arvoa.  

Funktion määrittely luokan tapauksessa sisältää aluksi luokannimen, johon funktio kuuluu, eli Auto sen jälkeen tulee :: pisteet sekä funktion nimi Auto(). Jos funktiolla on paluuarvo se tulee ensimmäisenä ja parametrit kuten normaalisti funktioita määriteltäessä. 

## Omien funktioiden määrittely luokkaan

## Staattiset funktiot ja muuttujat

Static data members of a class are also known as “class variables,” because there is only one
unique value for all the objects of that class. Their content is not different from one object
of this class to another.
For example, it may be used for a variable within a class that can contain a counter with
the number of objects of the class that are currently allocated, as in the following example:

## const member functions

## Type Conversions and Constructors