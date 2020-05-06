---
title: "Käännösympäristön asentaminen"
permalink: /part1/1/
nav_order: 1
published: true
parent: "C++ lyhyesti, 1. ohjelma ja perusrakenteet"
---

## Qt-Creator IDE:n asentaminen

Tällä kurssilla käytetään ohjelmointiympäristönä Qt-Creator sovellusta, sovellus sisältää niin lähdekoodieditorin kuin kääntäjän. Näin ollen ohjelmoija saa käyttöönsä kokonaisen IDE:n (Integrated Development Environment). C++ ohjelmia voi kirjoittaa millä tahansa tekstieditorilla ja sovelluksen kääntämiseen on tarjolla useita vaihtoehtoja, jotka toimivat komentoriviltä tai IDE:stä.

> Tämän kurssin esimerkit on toteutettu Qt-Creatorilla, mutta opiskelija saa halutessaan käyttää muutakin IDE:tä tai muita kääntäjiä, kuitenkaan näille ei voida kurssin aikana antaa erillistä ohjausta

Asennusohje: [asennusohje.pdf](/assets/qt_asennus.pdf)

## Projektin luominen

Kun Qt-Creator on käynnistynyt valitse valikosta: 
_**”File -> New File of Project…”**_
Avautuvasta dialogista valitse 

_**”Non-Qt Project”**_ sekä  _**Plain C++ Application**_
näin saat luotua uuden tyhjän projektin. 
Valitse lopuksi _**”Choose…”**_

![](/assets/images/qt_projekti_1.png)

Anna projektille nimi: _**”Eka projekti”**_, tallennuspaikkana voit käyttää haluamaasi osoitetta. Qt-Creator luo tähän kansioon oman alikansion projektille. Kun tämä tehty _**"Valitse next"**_

> Projektit voi tallentaa esim. käyttäjän omaan Documents-kansioon ja luoda sinne Cplusplus nimisen kansion jonne luo kaikki projektit. Kannattaa kuitenkin suosi projektikansion nimessä polkua jossa ei ole välilyöntejä.

![](/assets/images/qt_projekti_2.png)

Seuraavassa dialogissa valitaan kääntäjä, tässä käytetään _**qmake**_ ja paina _**Next**_

![](/assets/images/qt_projekti_3.png)

Kits-osiossa valitaan pelkkä _**Desktop**_, riippuen asennuksesta voi muitakin vaihtoehtoja olla saatavilla.

![](/assets/images/qt_projekti_4.png)

Summary osioon ei tehdä muutoksia, ja paina lopuksi _**Finish**_

![](/assets/images/qt_projekti_5.png)

Nyt sinulla pitäisi olla ensimmäinen ohjelma ja seuraava näkymä edessäsi. 

![](/assets/images/qt_projekti_6.png)

Kyseessä on Qt-Creatorin perusnäkymä. Tässä näkymässä:
-	Vasemmalla näkyvät projektin tiedostot, nyt meillä on vain yksi tiedosto main.cpp, kun haluamme kääntää suoritettavan sovelluksen tämä tiedosto lähetetään kääntäjälle. Meidän ei tarvitse huolehtia miten tämä tapahtuu, vaan IDE tekee sen puolestamme. Lisäksi näet .pro loppuisen tiedoston, nämä ovat Qt-Cretorin omia tiedostoja ja niillä hallitaan projektia, tämän kurssin aikana ei näihin tiedostoihin perehdytä.
-	Alhaalla näet ikkunan, jonne tulevat ilmoitukset kääntäjältä tai IDE:ltä.
-	Suurimman alan täyttää kuitenkin itse koodieditori, tähän kohtaan tulemme jatkossa kirjoittamaan omaa koodia. Tähän aukeaa aina .cpp tai .h tiedoston sisältö riippuen siitä minkä olet avannut.
-	Aivan vasemmasta alakulmasta löydät vihreä ”Play”-painikkeen kun painat sitä lähdekoodisi käännetään ja suoritetaan, ja sinun pitäisi saada seuraava ikkuna.

![](/assets/images/qt_projekti_7.png)

Nyt sinulla on toiminnassa toimiva ympäristö, jossa pääset kehittämään omia C++ -ohjelmiasi.
