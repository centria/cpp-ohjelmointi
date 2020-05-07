---
title: "Perusrakenteita"
permalink: /part1/3/
nav_order: 3
published: true
parent: "C++ lyhyesti, 1. ohjelma ja perusrakenteet"
---


## C++ kielen perusrakenteita

Ohjelmamme ei nyt varsinaisesti tee vielä mitään, tehdään siihen muutamia muutoksia. Mutta aluksi muutamia perusteita joiden varaan C++ -ohjelma rakentuu.

### Lauseet ja lausekkeet

- Lause on koodin yksikkö, joka tekee jotain
- Lauseke on lause, jolla on arvo - esimerkiksi "Hello World", 42, 4 + 2.

Jokainen lause ei välttämättä ole lauseke, sillä lause ei välttämättä tuota arvoa, kuten _**#include**_

### Aritmeettiset operaattorit

Voimme suorittaa aritmeettisiä laskelmia operaattoreiden avulla. Operaattorit toimivat osana lausekkeita, ja ne tuottavat uuden lausekkeen kunnes lopullinen arvo muodostuu. Esimerkiksi (8 + 10) / 2 lauseke sisältää operaattoreita ja tuottaa lopulta tuloksen 9. Voisit sijoitaa _**(8 + 10) / 2**_ , korvaamaan _**"Hello World"**_ tekstin edellisessä esimerkissämme ja saisit ruudulle tulostumaan arvon 9.

Lausekkeessa _**(8 + 10) / 2**_, ovat operaattorit + sekä / ja operandit 8, 10, 2. Huomaa että C++:san laskujärjestys noudattaa matematiikan sääntöjä.

**Operaattorityyypit:**

- Matemaattiset: +, -, *, /, ja sulkeet (), toimivat kuten ne toimivat muissa ohjelmointikielissä tai matematiikassa. Jakojäännöksen voi toteuttaa % operaattorilla, esim 6 % 5 tuottaa tuloksen 1

- Loogiset: 
    - && (ja, and)
    - \|\| (tai, or)
    - ! (not, epätosi)

- Bittien käsittely: 
    - \& \| \^ vertaavat alkioita bitti kerrallaan ja palauttavat
    - \<\< \>\> siirtävät bittejä sanan sisällä
    - \~ yhden komplementti 0-> 1 ja 1-> 0

### Tietotyypit

Jokainen lauske päättyy tulokseen jossa arvo jonka lauseke tuottaa edustaa jotain tietotyyppiä. Näin koodia suorittava suoritin tietää miten muistissa olevaa tietoa pitäisi tulkita. 

Esimerkiksi koodissa olevat arvot voidaan tulkita seuraavasti:

- 0 on kokonaisluku (int)
- 3.1415 on liukuluku (float) 
- "Hello, world!" on tekstiä (string)

C++:ssan sisäänrakennetut suosituimmat tietotyypit ovat seuraavat, koko määritelty 32-bittisessä järjestelmässä:

| Nimi | Kuvaus | Koko | Arvoalue 
|----------|-------------|-------------|-------------|
| bool | Totuusarvo, voi olla tosi (true) tai epätosi (false), määritellään sanoilla true/false koodissa | 1 tavua | true tai false
| char | Pieni kokonaisluku tai kirjaimen numeerinen arvo, määritellään koodissa ''-merkkien sisään, esim _**'a'**_ tai _**'3'**_ | 1 tavua | signed: -128 ... 127 sekä unsigned: 0 ... 255
| int | Kokonaisluku | 4 tavua | signed: -2147483648 ... 2147483647 unsigned: 0 .. 4294967295
| double | Tuplatarkkuuden liukuluku | 8 tavua | +/- 1.7e +/- 308 ( 15 merkkiä)

_**signed**_ tarkoittaa että luku voi esittää negatiivisia ja/tai positiviisia lukuja, kun taas _**unsigned**_ tarkoittaa että luku voi esittää vain positiivisia lukuja. Jos tätä ei määritetä suurinosa käyttjistä tulkitsee luvun _**signed**_ versiona.

C++:ssa on oikeasti 3 kokonaislukutyyppiä, _**short**_, _**int**_ ja _**long**_. Jos on tarve säästää muistia voi käytää _**short**_ tyyppistä muuttujaa (-32768 ... 32767) tai jos olet varma että on tarve isoille luvuille voit käyttää _**long**_ tyyppistä muuttujaa.

Sama koskee myös liukuluku tyyppejä, C++:ssä on mahdollista käyttää _**float**_, _**double**_, ja _**long double**_ tietotyyppejä. Nämä eroavat tarkkuuden puolesta.

Lisää tietoa tietotyypeistä löydät esim: https://www.tutorialspoint.com/cplusplus/cpp_data_types.htm


### Operaatiot ja tietotyypit

Operaatiot voidaan toteuttaa vain niillä tietotyypeillä, jotka ovat tuettuina operaation toimesta. Esimerkiksi kokonaisluvusta ei voida ottaa jakojäännöstä liukuluvulla.

C++ muuttaa eri tilanteissa automaattisesti tyyppiä tarvittaessa. Jos operaattorin eri puolilla käytetään eri tietotyyppiä, laajennetaan suppeampi/pienempi tyyppi. Laajentamista on havainnollistettu seuraavassa:

```c++
4/8

Tässä tapauksessa toteutetaan kokonaislukujen 4 ja 8 jakolasku, jolloin vastaukseksi saadaan 0. Tämä sen vuoksi, että molemmat laskettavat ovat kokonaislukuja ja tuloksen kokonaisluku osuus on 0. Vaikka lopputulos liukulukuna olisi 0.5 niin C++:ssa loppuosa katkaistaan pois kun tehdään kokonaisluvuilla jakamista.

Jos lasku toteutettaisiin seuraavasti:

4.0/8 

Laajennetaan kokonaisluku 8 liukuluvuksi, jolloin tulokseksi saadaan 0.5. Laajentamista ei tarvita, jos molemmat luvut ovat valmiiksi liukulukuja.

Tietotyypille voidaan pakottaa muutos, laittamalla haluttu tyyppi sulkujen kanssa muutettavan arvon eteen. Sulut voidaan laittaa joko muutettavan arvon tai tyypin ympärille:

double(4)/8 

Tuottaa tuloksen 0.5, samoin kuin 

(double)4/8 


```


### Numerojärjestelmät

C++:ssa kuten muissakin ohjelmointikielissä käytetään numerojärjestelmää jossa kantalukuna on 10, jos haluat käyttää muuta numerojärjestelmää kuten 8 tai 16, se onnistuu seuraavasti:

Jos haluat esittää luvun numerojärjestelmässä jossa 8 on kantaluku, kirjoita numeron ensimmäiseksi numero 0. Tämä jälkeen numero 8-järjestelmässä:

_**esim. 0123 vastaa kymmenjärjestelmän lukua 83**_

Vastaavasti hexagonaalijärjestelmässä, missä kantaluku on 16, luvut esitetään laittamalla niiden alkuun 0x.

_**esim. 0x123 vastaa kymmenjärjestelmän lukua 291**_


### Oppimistehtäviä:

- Testaa erilaisia matemaattisia laskutoimituksia korvaavammalla seuraavassa lausekkeessa X, jolloin matemaattisella lauskeella: _**cout << X << endl;**_ 
esim. _**cout << 2/4 << endl;**_ 

- Testaa myös tulosta mistä oktagonaali ja hexagonaali luvuilla

## Muuttujat

Jotta voisimme järkevästi käyttää arvoja, emmekä laskea niitä aina uudestaan, tarvitsemme tavan jolla säilytämme ja nimeämme niitä.  Tätä arkoitusta varten on olemassa erityisiä "laatikoita", joita kutsutaan muuttujiksi. Kuten nimi muuttuja viittaava, säiliön sisältöä voidaan muuttaa (melkein) millään tavalla tahansa. 

![](/assets/images/muuttujat.png)
_Muuttujat, kuva Cisco Networking Academy_

C++:ssa jokaiselle muuttujalle tulee määrittää:
- nimi
- tietotyypi
- arvo

Periaatteessa arvo voidaan jäättää määrittämättä, tällöin arvo on satunnainen. Tämä johtuu siitä, että jokaiselle muuttujalle varataan muistista tilaa ja jos emme alusta muuttujaa arvolla saa se arvoksi sen mitä kyseissä muistiosoitteessa on tietona sillä hetkellä.

Yksinkertainen esimerkki muuttujan käytöstä, on seuraavassa. Määrittelemme _(declaration)_ kokonaisluku _**(int)**_ tyyppisen muuttujan, ja annamme sille nimen _**x**_ sekä alustamme _(initialization)_ arvoksi laskutoimituksen _**4 + 2**_ tuloksen. Arvo sijoitetaan muuttujaan aina _**=**_ operaattorilla. 

```c++
int x = 4 + 2;
cout << "X:n arvo on: " << x << endl;

float y = 4.0 / 2.0;
cout << "Y:n arvo on: " << y << endl;
```

Muuttujien nimeämisessä on seuraavat säännöt:
- Nimi voi sisältää ISOJA ja pieniä kirjamia sekä niiden sekoituksia, numeroita ja muita latinalaisen aakkoston merkkejä. Myös alaviiva _ on sallittu muuttujan nimessä.
- Muuttujan nimen tulee alkaa kirjaimella tai alaviivalla
- Isot ja pienet kirjaimet ovat eriarvoisia, eli auto1 ja AuTo1 ovat eri muuttujat.

Nämä säännöt itseasiassa pätevät kaikkiin nimeämisiin joita C++:ssa tehdään, funktiota, luokat, jne...

Esimerkkejä oikein nimetyistä (mutta ei välttämättä käytännöllisistä) muuttujista seuraavassa:
```
i
t10
Exchange_Rate
counter
DaysToTheEndOfTheWorld
TheNameOfAVariableWhichIsSoLongThatYouWillNotBeAbleToWriteItWithoutMistakes

```

Kun taas seuraavat eivät ole sallittuja:

```
10t (ei ala kirjaimella)
Adiós_Señora (vääriä merkkejä)
Exchange Rate (sisältää välilyönnin)

```

Voit määritellä kerralla yhden muuttujan tai monta saman tietotyypin muuttujaa.

```c++
//Määritellään kolme int -tyyppistä muuttujaa
int autojen_lkm, mopojen_lkm, pyorien_lkm;

```

**HUOM!** C++:ssa muuttujia ei alusteta (muutamaa poikkeusta lukuunottamatta), joten niiden arvoksi tulee se muistipaikan sisältö johon ne osoittavat. 

### Varatut sanat (keywords)

C++:ssa on jonkinverran varattuja sanoja, näitä sanoja ei voi käyttää yksinään muuttujan tai funktion nimessä. Seuraavassa kuvassa on listattuna nämä sanat.

![](/assets/images/keywords.png)

### Syötteen pyytäminen käyttäjältä

Komentoriviohjelmissa voidaan käyttäjältä pyytää syöte käyttämällä iostream-kirjaston _**cin -funktiota**_. Tämä funktio toimii kuten _**cout**_, mutta sille annetaan muuttuja, johon käyttäjän syöttämä arvo sijoitetaan. 

Esimerkiksi seuraava kysyy käyttäjältä x:n arvoa:

```c++
#include < iostream >
using namespace std;

int main () 
{
    cout << "Anna x:n arvo: ";
    int x ;
    cin >> x ;
    cout << "Lukusi jaettuna 3:lla: " << x / 3 << ", kerrottuna kahdella: " << x * 2;

    return 0;
}

```

### Vakiot

Vakio on lauseke jolla on määritetty (vakio) arvi0. Vakiot voidaan jakaa seuraaviin tyyppeihin:
- Literaalit, esim, luvut, tekstit, tottuusarvot
- Määritellyt vakiot, käyttäjän määrittelemät vakiot joita ei sijoiteta muuttujiin. Nämä määritellään _**#define**_ esikääntäjä lausekkeella. Ja esikääntä korvaa ilmentymät vakiolla kun löytää sen koodin seasta. 

Määritelty vakio toimii seuraavasti.
```c++
#define PII 3.1415
#define NEWLINE ’\n’

double r = 5.0;
double circle ;

circle = 2 * PI * r; // circle = 2 * 3.14159 * r;
cout << circle << NEWLINE ; // cout << circle << ’\n ’;

```

Määritellyillä vakiolla on muutakin käyttöä, mutta niihin palataan myöhemmin.

- Esitellyt vakiot (const): ohjelmoija voi esitellä muuttujan vakiona, jolloin sen arvoa ei voi vaihtaa.

```c++
const int r = 100;
r = 200; //Aiheuttaa virheen
circle = 2 * PI * r; // circle = 2 * 3.14159 * r;
cout << circle << endl;

```

### Vasemmat ja oikeanpuoleiset arvot (left hand side value, L-values, R-values)

Vasemman ja oikeanpuoleisten arvojen ymmärtäminen, ei C++:san osaamistavoitteiden kannalta ole merkityksellisiä. Mutta niiden ymmärtämisestä on hyötyä kun tulkitaan kääntäjän virheilmoituksia.

Vasemman puoleisen arvot toimivat lausekkeiden vasemmanlla puolella, esimerkiksi seuraavat ovat vasemman puoleisia arvoja:
- int var 
- float x

Periaatteessa vasemmanpuoleisia arvoja ovat sellaiset lauseet joihin voidaan sijoitaa arvo.

- var + 5 
- float / 3.00

### Lukujen kasvatus ja pienentäminen

Kokonaislukuja voidaan kasvattaa ja supistaa _**++**_ sekä _**--**_ operaattoreilla

Nämä operaattorit ovat toteuttavat kokonaisluvun kasvattamisen yhdellä tai pienentämisen yhdellä. Eli ne ovat vastaavat kuin:
- _**a = a + 1 -> a++**_
- _**b = b - 1 -> b--**_

Kasvattamis ja pienentämis operaatioida voidaan käyttää joko etu- tai jälkikäteen.

++a kasvattaa a:n arvoa aluksi ja sitten palauttaa sen arvon.
a++ palauttaa aluksi a:n arvon ja sen jälkeen kasvattaa muuttujan arvoa.

--a pienentää a:n arvoa aluksi ja sitten palauttaa sen arvon.
a-- palauttaa aluksi a:n arvon ja sen jälkeen pienentää muuttujan arvoa.


```c++
int a = 1;
cout << "1. A:n arvo:" << a++ << endl; //Tulostaa 1
a = 1;
cout << "2. A:n arvo:" << ++a << endl; //Tulostaa 2
```

### Sijoittamisoperaatorit

Käytimme aikaisemmin sijoittamisoperaatiota

```c++
int a = 1;
int b = 2;
int c = a + b;
```

Sijoittamisoperaatio voidaan myös lyhentää seuraavasti:
- += ,lisäätään ja muuttujan arvoon toinen arvo (c = a + b)
- -= ,vähennetään ja muuttujan arvosta toinen arvo (c = a - b)
- /= ,jaetaan muuttujan toisella toinen arvo (c = a / b)
- *= ,kerrotaan muutuja toisella arvolla (c = a */* b)


### Tyyppimuunnokset

Tyyppimuunnoksia käytetään vaihtamiseen tietotyyppien välillä. Englanniksi niitä kutsutaan nimellä _**cast**_ .  Tyyppimuunnokset ovat implisiittisiä
kun siirrytään pienemmästä tietotyypistä suurempaan tai samankokoiseen tietotyyppiin (esim. float doubleksi tai int floatiksi). Tämä tarkoitaa että muutos tapahtuu automaattisesti, eikä sitä tarvitse määritellä,

Tyyppimuunnokset on yleensä ilmoitettava (eksplisiittinen muunnos) kun laajempaa tietotyyppiä supistetaan (esim. float to int), muulloin kääntäjä antaa virheen.

```c++
int x = (int) 5.0; // vaatii eksplisiittisen muunnoksen
short s = 3;
long l = s; // eksplisiittistä muunnosta ei tarvita
float y = s + 3.4; // kääntäjä toteuttaa implisiittisen muunnoksen short-arvolle
```

### Suoritusjärjestykset

Kuten artimetiikassa, C++:ssa on järjestys missä operaatiot suoritetaan. Laskujärjestys seuraa pitkältä matemaattisia laskusääntöjä.

| Järjestys | Operaattori | Selite 
|----------|-------------|-------------|
| 1. | () [] -> . :: | Ryhmittelyt, funktiokutsut
| 2. |  ˜ * & sizeof (tyyppimuunnos) ++ –- | Unaarioperaatiot
| 3. | * / % | Kertolasku, jakolasku, jakojäännös
| 4. | + -  | Yhteen- ja vähennyslasku
| 5. | << >> | Bittisiirrot
| 6. | < <= > >= | Vertailuoperaatiot
| 7. | == != | Yhtäsuuruus, erisuuruus operaatiot
| 8. | & | Bittivertailu JA (AND)
| 9. | ˆ | Bittivertailu poissulkeva TAI  (XOR)
| 10. | \| | Bittivertailu TAI (OR)
| 11. | && | Looginen JA (AND)
| 12. | \|\| | Looginen TAI (OR)
| 13. | ?: | Konditionaalinen ehto
| 14. | = += -= *= /= %=, jne... | Sijoitusoperaatiot
| 15. | , | Pilkkuoperaatiot

### Kommentointi

C++:ssa on seuraavat kommentointi ominaisuudet. Kääntäjä ei huomioi tekstiä, joka on kommentoitua. 

_**//**_ näiden merkkien jälkeen rivillä oleva loppu teksti on kommentoitu tekstiä, tämä on ns. yhden rivin kommentti 


_**/***_ merkki aloitaa vastaavasti kommentin, joka voi olla useita rivejä
_***/**_ merkit päättävät pitkän kommentin. 

```
// Hei tässä on lyhyt kommentti

/* Tämä kommentti on pitkä ja voi jakaantua
usealle riville */

```
## Oppimistehtäviä:

- Lisää esimerkkitehtävään kommentti joka on usemman rivin mittainen ja kertoo kuka koodin on tehnyt sekä _**return 0;**_ lauseen perään yhden rivin kommentti, jossa kuvataan miksi pitää palauttaa 0

