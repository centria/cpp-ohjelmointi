---
title: "OOP - kotelointi"
permalink: /part6/4/
nav_order: 2
published: true
parent: "Osa 6. Luokat"
---

# Kotelointi

Kotelointi (encapsulation) on yksi olio-ohjelmoinnin perusteista, kotelointi tarkoittaa toisiinsa liitoksissa olevan tiedon ryhmittelyä, koskien niin muuttujia kuin funktioita. Lisäksi kotelointiin kuuluu tiedon piilottaminen ja rajapintojen luominen

Koteloinnin tarkoituksena on piilottaa luokan käyttäjältä tieto jota hän ei tarvitse. Näin käyttäjä voi keskittyä vain olenaisten rajapintojen käyttämiseen.

Luokkien osalta C++ määrittää oletuksena funktiot ja jäsenmuuttujat yksityisiksi, jotta voidaan suojella luokan yhtenäisyyttä ja paljastaa vain tarvittavat rajapinnat.


## Tehtävät

1. Toteuta luokka Ajoneuvo sekä Paikka. Ajoneuvo luokassa on kolme jäsenmuuttujaa
- nopeus (int)
- paikka (Paikka)
- renkaidenLkm (int)
Paikka luokassa on kaksi jäsenmuuttujaa:
- latitude (double)
- longiture (double)

Toteuta jäsemuuttujille asettajafunktiot sekä noutofuktiot.
