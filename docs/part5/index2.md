---
title: "Osa 5. Osoittimet"
permalink: /part5/
nav_order: 7
published: true
has_children: true
has_toc: true
---

# Osa 5 - Osoittimet

## Johdanto

Kun määrittelemme muuttujia varataan tietokoneen muistista muuttujalle osoite ja varataan tila.
Kun käytät muuttujia tapahtuu seuraavat:
1. Tietokone tarkastaa mitä mihin muistialueeseen muuttuja viittaa
2. Tietokone siirtyy käsittelemään muistialuetta ja joko noutaa tai asettaa arvon sen perusteella

C++:ssa voidaan käsitellään muistialuita suoraan suorittaen jommankumman kohdan 1. tai 2. Olemme aikaisemmin käyttäneet vittausta, eli kohtaa 1.

1. &x -> hakee muuttujan x muistiosoitteen
2. *( &x ) ottaa x:n muistiosoitteesta arvon, eli *( &x ) = x

Muistialueiden suora käsittely, osoittimien kautta, tarjoaa tehokkuuden lisäki uusia ominaisuuksia kuin pelkkä muuttujien käyttö:

1. Osoittimilla voidaan toteuttaa viittauksien välitys monipuolisemmin
2. Monimutkaisten tietorakenteiden tehokas käsittely, vaikka tieto olisi ei muistiosoitteissa
3. Polymorphismi, käsitellään myöhemmin osioissa 7-8


Osoittimia voidaan hyödyntää monipuolisesti perustietotyyppien käsittelyssä, mutta niistä on erityisesti hyötyä talukoita käsiteltäessä sekä kun käytämme myöhemmin dynaamista muistia.

## Osoittimet

Osoittimet kunten mikä tahansa muuttuja, niihin tallennetaan muistiosoitteita, yleensä muiden muuttujien muistiosoitteita. Muuttuja joka tallentaa muuttujan X muistiosoitteen sanotaan osoittavan X:ään. Muistiosoitteeseen viittavasta muuttujasta voidaan hakea arvo tarvittaessa.

Kuten taulukoiden tapauksessa osoittimien toimintaa voidaan havainnollistaa peräkkäisillä lohkoilla. Jokainen alla esitetty lohko vastaa yhtä muistilohkoa. Piste (ptr) on muuttuja joka viitaa toiseen muistipaikkaan x, näin ollen prt muuttujan arvo on 12314, joka edustaa x:n muistipaikan osoitetta.

![](/assets/images/pointers_1.png)

_Kuva 1. osoittimen havainnollistaminen, Lähde: MIT._

## Määrittely

Kun haluamme muodostaa osoittimen joka osoittaa int-tyyppiseen muuttujaan, määritellään

```
tietotyyppi * muuttujan_nimi;
```

Esim. int-tyyppiseen muuttujan osoitin määritellään.

```c++
int x = 10; 
int *ptr = &x; //ptr sisältää nyt x:n muistiosoitteen
```

Osoitin toimii mille tahansa tietotyypille, tätä käsitellään luokkien yhteydessä lisää.

## Arvojen käyttö

Kun haluamme hakea osoitimen arvon, teemme seuraavat toimet:
1. Siirrytään osoittimen muistipaikkaan, (* operaattori)
2. Luetaan arvo valitussa tietotyypissä

```c++
int x = 10; 
int *ptr = &x; //ptr sisältää nyt x:n muistiosoitteen

cout << "PTR osoittaa: " << ptr << endl; //Tulostetaan ptr:n muitipaikan osoite
cout << "PTR:n osoittaman muistipaikan sisältämä arvo: " << *ptr << endl; //Tulostetaan ptr:n arvo käyttäen * operaatiolla
```

Vastaavasti jos haluamme asettaa arvon muistipaikkaan käyttämme* operaatiota

```c++
*ptr = 5; // Asettaa muistipaikan arvoksi 5
```

Kuten mitä tahansa tietotyyppiä, osoittimia voidaan käyttää funktion parametereina. Jolloin parametreina välitetään muistipaikkojen tietoja joita voidaan sitten käsitellä. Tämä tehostaa ohjelman suorittamista sekä vähentää sen muistinkäyttöä.

```c++
void korotaToiseenPotenssiin ( int * numPtr ) 
{
    *numPtr = *numPtr * *numPtr ;
}

int main () 
{
    int x = 5;
    korotaToiseenPotenssiin (&x);
    cout << x; // Tulostaa 25
}
```

## Osoittimen muuttaminen

Osoitin voidaan siirtää osoittamaan toiseen muistiosoiteeseen, tämänkin osalta osoitin toimii kuten mikä tahansa muuttuja. Osoittimet myös tottelevat artimeettisia operaatioita esim ++ siirtää osoittimen seuraavaan muistipaikkaan ja -- edelliseen, näistä on hyötyä käsiteltäessä taulukoita osoittimien kautta.

```c++
int x = 10; 
int y = 12;
int *ptr = &x; //ptr sisältää nyt x:n muistiosoitteen

cout << "PTR osoittaa: " << ptr << endl; //Tulostetaan ptr:n muitipaikan osoite
cout << "PTR:n osoittaman muistipaikan sisältämä arvo: " << *ptr << endl; //Tulostetaan ptr:n arvo käyttäen * operaatiolla

ptr = &y; //ptr sisältää nyt y:n muistiosoitteen

cout << "PTR osoittaa: " << ptr << endl; //Tulostetaan ptr:n muitipaikan osoite
cout << "PTR:n osoittaman muistipaikan sisältämä arvo: " << *ptr << endl; //Tulostetaan ptr:n arvo käyttäen * operaatiolla
```


## Vakiot osoittimissa

Kun halutaan vakioida osoittimia tai niiden arvoja, voidaan const-lause kohdistaa kahteen eri paikkaan:
- osoittimeen
- osoittimen osoittamaan arvoon

Seuraava lauseke määrittää osoittimen joka osoittaa vakio int-arvoon, int-arvoa ei voida muuttaa osoittimen kautta. Osoitin voidaan siirtää kuitenkin osoittamaan toiseen muistipaikkaan.
```
const int *prt;
```

Seuraava lauseke taas määrittää osoittimen joka osoitaa aina samaan muistipaikkaan, tällöin sitä ei voida siirtää toiseen muistipaikkaan. Mutta sitä arvoa voidaan muuttaa johon osoitin osoittaa.
```
int *const ptr;
```


## Null, alustamattomat, and Deallocated Pointers

Jotkin osoittimet eivät osoita oikeaan tietoon, esim jos osoitin jää alustamatta ja sitä käytetään. Tai sitten käytetään osoitinta jonka osoittama muistialue on vapautettu. Jos tällaista osoitinta käytetään aiheutuu ajonaikainen virhe ja ohjelma kaatuu.

Jokainen osoitin joka on asetettu arvoon 0 on ns. NULL osoitin, myös tällaisen osoittimen käyttö aiheuttaa ongelmia. NULL-osoitinta voidaan kuitenkin käyttää tarkistamaan osoittaako osoitimen tilaa. Hyvien käytäntöjen mukaisesti tulisi osoitin aina tarkistaa ennen käyttöä ja näin selvittää onko se NULL-osoitin. On myös yleinen käytäntö asettaa osoitin 0:ksi kun sitä ei enään käytetä.

Virheellisen osoittimen voi saada aikaan esim. seuraavasti:

```c++
int * myFunc () 
{
    int haamuNummero = 4;
    return &haamuNummero ;
}

```

Edellinen funktio palauttaa osoittimen haamuNumeron muuttujan muistipaikkaan, kuitenkin kun funtkion suorittaminen päätty haamuNumero on jo tuhoutunut. Näin ollen funktion palauttama osoitin osoittaa muistipaikkaan joka ei ole enään ohjelman hallusa.


As with any other variable, the value of a pointer is undefined until it is initialized, so it
may be invalid. 

## Lisää viittauksista

Kun olemme tehneet funktiota tyyliin **f(int &b) {...}**, ja kutsumme sitä **f(a)**, viittattu muuttuja a saa funktiossa nimen b, käytänössä siis b on a:n muistipaikan aliasnimi. Voimme myös määritellä paikallisesti viittauksia:

```c++
int a;
int &b = a; // Tekee b:stä vittauksen (aliaksen) a:lle
```

Nyt jos muutamme a:ta tai b:tä niin molemmat muuttuvat, koska ne käsittelevät samaa muistipaikkaa.

Osoittimien ja viittauksien erot:

- Viittauksia käsiteltäessä ei tarvitse huolehti operaatioista (* / &)  vaan ne tehdään automaattisesti
- Viittauksen osoitetta ei voi vaihtaa, osoittimen voi. Tämän vuoksi viittaukset pitää alustaa

## Viittaukset (&) ja osoittimet (*)

Viittauksien ja osoittimien haaste on, että ne usein sekoitetaan varsinkin jos niitä ei käytä paljon. Tämä koskee erityisesti & ja * operaattoreita.

\* operaattoria käytetään:
1. Määrittelemään osoitin, * sijoitetaan tällöin muuttujan nimen eteen
2. Kun halutaan osoitinmuuttujasta ottaa arvo 

\& operaattoria käytetään:
1. Määrittelemään viittaava muuttuja, & sijoitetaan tällöin muuttujan nimen eteen
2. Kun halutaan saada muuttujan muistiosoitteen arvo


## Osoittimet ja taulukot

Kun luomme taulukon esim. int taulukko[3], taulukko muuttuja itseasiassa on osoitin taulukon ensimmäisen alkion muistipaikkaan. Kun viittaamma indeksiin 2 viittaamme alkioon joka on 2:den lohkon päässä taulukon alkiosta 0. 


### Osoitin artimetiikka

Osoitimilla voidaan toteutta myös laskentaa, jolloin osoittinta on mahdollista siirtää matemaattisilla toimilla. Tämä mahdollistaa osoittimen nopean siirtämisen haluttuun lohkoon. Useammin käytetty menetelmä on lisätä / vähentää osoittimesta tietty luku jotta päästään haluttuun alkioon. Osoittimen siirtämistä eteenpäin lisäämällä osoittimeen lukuja on mahdollista seuraavasti:

![](/assets/images/pointers_2.png)

Kun käytetään osoitinaritmetiikkaa kääntäjä varmistaa, että osoitin siirtyy oikeaan muistipaikkaa, siirros riippuu siis käytettävästä tietotyypistä. 

Edellisen kuvan mukainen koodi, joka tulostaa alkiot taulukosta käyttäen osoitinta on esitetty seuraavassa.

```c++
long arr [] = {9,5,6,33,21,44,2,99,65,41};
long * ptr = arr;

cout << "Alkiossa 0 on luku " <<  *(ptr) << endl;
cout << "Alkiossa 1 on luku " <<  *(ptr+1) << endl;
cout << "Alkiossa 2 on luku " <<  *(ptr+2) << endl;
cout << "Alkiossa 9 on luku " << *(ptr+9) << endl;

```