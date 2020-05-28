---
title: "Osa 4. Taulukot and teksti"
permalink: /part4/
nav_order: 6
published: true
has_children: true
has_toc: true
---

# Osa 4 - Taulukot and teksti

## Taulukot

Taulukoihin voidaan tallentaa useita arvoja samaan laajempaan muistialueeseen. Muistinhallinnan osalta taulukko ei juurikaan eroa muuttujista, muuttuja varaa käyttöönsä muistiosoitteen X tietyn kokoisena. Vastaavasti myös taulukko varaa muistiosoitteen X, että siihen mahtuu Y kertaa määritetyn kokoinen tietotyyppi.

Taulukko on kiinteän kokoinen muistialue, jossa saman tietotyypin arvot ovat tallennettuina peräkkäisiin muistipaikkoihin. Taulukon indeksointi alkaa 0:sta ja päättyy N-1, missä N on taulukon koko. Taulukon sijoittumista muistiin on havainnollistettu seuraavassa kuvassa.

![](/assets/images/array_example.png)

C++:ssa taulukko määritetään seuraavasti:

```c++
tietotyyppi taulukon_nimi[taulukon koko];

//esim. 10 kokoinen int arvoja sisältävä taulukko

int arvosanat[10];
```

Jos taulukkoon ei määritellä arvoja alustuksen yhteydessä sisältää taulukko satunnaisia arvoja. Arvot voidaan määritellä joko alustuksen yhteydessä tai sijoittamalla arvot taulukkoon.

```c++
//Sijoitetaan arvot taulukkoon
arvosanat[0] = 1;
arvosanat[1] = 2;
arvosanat[2] = 4;
arvosanat[3] = 4;

//Toinen tapa alustaa taulukko on antaa arvot määrittelyssä
int arvosanat[4] = { 1, 2, 4, 4 };

//Taulukon kokoa ei tarvitse antaa jos määrittelyssä annetaan arvot
int arvosanat[] = { 1, 2, 4, 4, 3, 5, 1, 3 };
```

Taulukon arvoihin viitataan indeksien kautta, taulukosta palautuu arvo joka voidaan sijoitaa muuttujaan tai käyttää suoraan. Viittauksena voidaan käyttää joko arvoa tai lauseketta (esim. muuttujat).

esim. seuraavat viittaukset toimivat

```c++
arvosanat[5];
arvosanat[i];
arvosanat[i+3];
```

```c++
//Haetaan taulukosta kolmas arvosana
int kolmas = arvosanat[2];

//Tulostetaan kaikki arvosanat
for(int i = 0; i < 10; i++)
    cout << "Arvosana indeksissä " << i << " on " << arvosanat[i];
```

Hyvä käytäntö on määritellä #define-lauseella taulukon koko näin voidaan varmistu siitä, että taulukon kokoon viitataan aina oikein. Pohdi seuraavan kahden esimerkin eroja.

```c++

//Esimerkki 1.
int pikselit[640];

for(int i = 0; i < 640; i++)
    pikselit[640-i] = nayton_pikseli[i]

//Esimerkki 2.
#define NAYTON_LEVEYS 640

int pikselit[NAYTON_LEVEYS];

for(int i = 0; i < NAYTON_LEVEYS; i++)
    pikselit[NAYTON_LEVEYS-i] = nayton_pikseli[i]
```


### Taulukko parametrina

Taulukot voidaan välittää funktioille kuten mikä tahansa muuttuja. Taulukot välitetään aina viittauksena. Kun taulukko välitetään funktiolle sitä käytetään normaalisti. Huomaa, kun taulukko välitetään funktiolle, tulee funktion tietää taulukon koko.

```c++
#include <iostream>
using namespace std;

int alustaTaulukko(int taulu[], const int koko) 
{
    for(int i = 0; i < length; taulu[i++] = 0);

     /*Edellä esitetty for -silmukka voidaan esittää myös
        for(int i = 0; i < length; i++)
        {
            taulu = 0;
        }
    */
}

int laskeSumma(const int taulu[], const int koko) 
{
    long sum = 0;
    for(int i = 0; i < length; sum += taulu[i++]);
        return sum;

    /*Edellä esitetty for -silmukka voidaan esittää myös
        for(int i = 0; i < length; i++)
        {
            sum += taulu[i];
        }
    */
}

int main() 
{
    int arr[10];
    alustaTaulukko(arr,10);

    cout << "Summa: " << laskeSumma(arr, 10) << endl;
    return 0;
}
```

### Moniuloitteinen taulukko

C++ taulukko voi olla moniulottinen, tällöin määrittelyssä annetaan haluttujen ulottuvuuksien määärä. Huomaa, että kaksiulotteista taulukkoa määritettäessä tulee ulottuvuuksien koot antaa aina.

tietotyyppi taulukon_nimi[koko_ulottuvuus_1][koko_ulottuvuus_2];

```c++
//Määritelään 10x10 kokoinen taulukko
int pikselit [10][10]
```

Kaksi ulotteiseen taulukkoon viitataan kuten yksiulotteiseen, antamalla ulottuvuuksien indeksit

```c++
#include <iostream>
using namespace std;

int main() 
{
    int twoDimArray[2][4];
    twoDimArray[0][0] = 6;
    twoDimArray[0][1] = 0;
    twoDimArray[0][2] = 9;
    twoDimArray[0][3] = 6;
    twoDimArray[1][0] = 2;
    twoDimArray[1][1] = 0;
    twoDimArray[1][2] = 1;
    twoDimArray[1][3] = 1;

    for(int i = 0; i < 2; i++)
        for(int j = 0; j < 4; j++)
            cout << twoDimArray[i][j];

    return 0;
}
```

Useampia ulottuvuuksia sisältävät taulukot pitää aina määritellä kokojen osalta, jotta kääntäjä tietää kuinka jaoitella taulukon muistialue. Samasta syystä kun useampi uloitteinen taulukko välitetään funktiolle pitää funktiolle kertoa kaikkien ulottuvuuksien koot.

```c++
int alustaMoniulotteinen(int arr[2][4])
{
     for(int i = 0; i < 2; i++)
        for(int j = 0; j < 4; j++)
            arr = 0;
}

```

Käytännössä moniulotteiset taulukot korvataan usein yksiulotteisella taulukolla, jota käytetään kuin se olisi moniulotteinen. 

![](/assets/images/1d_as_2d_array.png)
```c++
int arr2[4][3]; // Kaksi ulotteinen taulukko
int arr1[12]; //Samankokoinen yksiuloitteinen

int leveys = 4;
int korkeus = 3;

//Käyteään yksiulotteista kuin se olisi kaksi uloitteinen, indekseihin viitataan loogikalla
// ulottuvuus2_indeksi * ulottuvuuden1_koko + ulottuvuus1_indeksi 

for(int i = 0; i < korkeus; i++)
        for(int j = 0; j < leveys; j++)
            arr1[j*leveys+i] = 0;

//Näin voidaan hallita esim 10x10 kokoisen näytön pikseleitä yksi ulotteisessa taulukossa
```

## Merkkijono

C++:ssa merkkijonot käsitellään joko taulukkomuotoisina niin, että taulukon indekseihin tallennetaan char-tyyppisenä muuttujana kirjain tai teksti-olion (tästä myöhemmin). Ensiksi mainittu tapa juontaa juurensa C-kieleen.

```c++
#include <iostream>
using namespace std;

int main() 
{
    char hello[] = { 'H', 'e', 'l', 'l', 'o', '\0' };
    //Huom! jos \0 merkki kertoo että teksti loppuu ns. NULL-merkki
    cout << hello << endl;

    //Voidaan alustaa taulukkopohjainen merkkijono myös, tällöin kääntäjä lisää NULL-merkin
    char helloworld[] = “Hello, world!”;
    cout << helloworld << endl;

    return 0;
}
```

Yksittäisiä kirjaimia voidaan käsitellä suoraan kuten mitä tahansa taulukkoa, tai hyödyntäen kirjastoja. Nämä kirjastot lisätään ohjelmaan #include kommennolla.

- cctype (ctype.h): kirjainten käsittely
- cstdio (stdio.h): input/output operaatiot
- cstdlib (stdlib.h): yleisiä työkaluja
- cstring (string.h): merkkijonojen muokkaus

Seuraavassa esimerkissä hyödynnetään edellämainittua cctype -kirjastoa

```c++
#include <iostream>
#include <cctype>
using namespace std;

int main() 
{
    char sekavatMerkit[] = "Er8ikOI73nen.Merkk393jono";

    char current = sekavatMerkit[0];
    for(int i = 0; current != '\0'; current = sekavatMerkit[++i]) 
    {
        if(isalpha(current))
            cout << (char)(isupper(current) ? tolower(current) : current);
        else if(ispunct(current))
            cout << ' ';
    }

    cout << endl;
    return 0;
}
```

Edellisessä esimerkissä isalpha(), isupper(), ispunct() ja tolower() funktiot ovat cctype kirjastosta.
- isalpha, tarkistaa onko kirjain aakkonen
- isupper, tarkastaa onko kyseessä iso kirjain
- islower, tarkastaa onko kyseessä pieni kirjain
- ispunct, tarkastaa onko kyseessä piste
Jokainen näistä palauttaa joko true tai false arvon.
- tolower, palauttaa annetun merkin pienenä kirjaimena

Esimerkki siis käy tekstin (sekavatMerkit) läpi kirjain kirjaimelta ja tulostaa sen pienillä kirjaimille, korvaten pisteet välilyönneillä. Muut merkit ohitetaan.

Seuraavassa esimerkissä hyödynnetään edellämainittua cstring -kirjastoa

```c++
#include <iostream>
#include <cstring>
using namespace std;

int main() 
{
    char osa1[] = "I'm a s";
    char osa2[] = "tring!";
    char kopioitu[20];
    char lopullinen[20] = "";

    strcpy(kopioitu, osa1);
    strcat(lopullinen, kopioitu);
    strcat(lopullinen, osa2);

    cout << lopullinen;
    return 0;
}
```

Tässä esimerkissä luodaan kaksi merkkijonoa (osa1, osa2). Lisäksi vartaan tyhjä merkkijono (kopioitu), sekä toinen tyhjä merkkijono (lopullinen). Aluksi kopioidaan osa1 -> kopioitu (strcpy), sekä sen jälkeen yhdistetään merkkijonoon lopullinen merkkijonot kopioitu ja osa2 (strcat). 