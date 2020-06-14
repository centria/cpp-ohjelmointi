---
title: "Osa 6. Luokat"
permalink: /part6/
nav_order: 8
published: true
has_children: true
has_toc: true
---

# Osa 6 - Luokat

## Johdanto

Jos haluamme käsitellä koodissa monimutkaisempia rakenteita kuin yksittäisiä arvoja, tarvitsemme järeämpiä tietotyyppejä. Tähän tarkoitukseen C++ tarjoaa luokat ja rakenteet. Omien tietotyyppien kautta monimutkaisempia rakenteita voidaan kehittää ja näin ollen mallintaa reaalimailmaa paremmmin. Tämä tekee C++ :sta myös olio-ohjelmointi kielen.

## Olio-ohjelmointi (lyhyesti)

Olio-ohjelmoinnissa ongelma jaetaan pienempiin osiin, yrittäen simuloida todellisen maailman objekteja. Olioista tulee näin ollen ohjelmoijan rakennuskomponentteja. Hyvin toteutettuja ja testattuja olioita voidaan käyttää eri projekteissa. 

Kun olio on luotu ohjelmoijan ei tarvitse jatkossa tietää miten olio toimii, vaan tietää miten sitä käytetään. Näin ohjelmoija voi keskittyä uusien ominaisuuksien ja olioiden luomiseen, tämä tehostaa koodaustyötä sekä antaa mahdollisuuden luoda laajoja kokonaisuuksia. Yksittäisten olioiden toiminallisuus on myös helpompi testata oikeaksi.

Olio-ohjelmoinnissa keskitytään ns. perusyksiköiden eli olioiden käsittelyyn. Oliot ovat C++: san  tapauksessa luokista/rakenteista luotuja instansseja. Olio sisältää joukon loogisesti yhteenkuuluvia:
- tietoja (attribuutteja)
- toiminnallisuuksia (metodeja)

Oliot voivat kommunikoida keskenään lähettämällä viestejä tai kutsumalla toisen olioiden metodeja. Viestin vastaanottaminen suorittaa määritellyn toiminnon vastaanottavassa oliossa. 

Oliolla on määritelmä, josta käytetään nimeä luokka. Luokka määrittelee jonkun tietyn oliojoukon yhteiset piirteet. Olio luodaan laatimalla luokan ilmentymä eli instanssi.

## Käsitteet  (lähde: http://jkorpela.fi/olio-ohj.html)

Seuraavassa määritellään muutamia luokkiin liittyviä käsitteitä, voit palata näihin myöhemmin kun ne tulevat vastaan tehtävissä.

### Luokka

Luokka on olio-ohjelmoinnissa olion methodien ja attribuuttien määritelmä. Luokka koteloi (encapsulation) sekä olion attribuutit että methodit. Luokan ilmentymän (olio/object) rakenteen määräävät tietokentät, attribuutit, voivat olla myös olioita. Luokan perimät ja luokassa määritellyt ominaisuudet määräävät luokan ilmentymän toiminnan. 

Luokan määrittelyssä käytetään tiedon kätkentää, ne ominaisuudet, joita luokan asiakkaan ei ole tarkoitus käyttää, määritellään joko yksityisiksi tai suojatuiksi. Yksityiset ja suojatut ominaisuudet eivät näy luokan asiakkaalle. Ominaisuudet, joihin luokan asiakkaan on tarpeellista päästä käsiksi, määritellään julkisiksi.

Luokka voi olla toteutukseltaan joko abstrakti tai konkreetti (palaamme abstakteihin luokkiin myöhemmin). Abstrakti luokka sisältää ainakin yhden viivästetyn (virtual) menetelmän. Menetelmä on viivästetty, jos menetelmästä on luokan kuvauksessa ainoastaan esittely, mutta ei toteutusta. Abstraktista luokasta ei voida luoda ilmentymiä, vaan luokkaa on tarkoitus käyttää periytymisessä yliluokkana. Konkreeteissa luokissa kaikki menetelmät ovat toteutettuja ja konkreeteista luokista voidaan luoda ilmentymiä.

Seuraavassa kuvassa havainnollistettu Car-luokka
![](/assets/images/class_figure_1.png)

### Periytyminen

Periytyminen on kahden luokan välinen relaatio. Periytyminen mahdollistaa yliluokkassa määriteltyjen ominaisuuksien käytettämisen aliluokassa. Periytyminen on transitiivista eli aliluokka perii ominaisuudet myös kaikilta yliluokkansa esivanhemmilta. Luokan esivanhempia ovat luokan yliluokka ja yliluokan esivanhemmat. Vastaavasti luokan jälkeläisluokkia ovat luokan aliluokka sekä aliluokan jälkeläiset.

Johdettaessa uusi luokka jostakin toisesta luokasta, johdetun luokan ilmentymän katsotaan sisältävän yliluokan ilmentymän aliolionaan. Aliluokassa voidaan yliluokasta perittyjä ominaisuuksia kumota eli määritellä uudestaan. Luokat ja niiden väliset periytymissuhteet muodostavat luokkahierarkian.

Periytyminen jaetaan yksittäisperiytymiseen ja moniperiytymiseen. 
- Yksittäisperiytymisessä aliluokalla on ainoastaan yksi yliluokka, jolta se perii ominaisuudet. 
- Moniperiytymisessä aliluokalla voi olla useita yliluokkia. Moniperiytyminen voi olla riippumatonta, jolloin luokan yliluokilla ei ole yhteisiä esivanhempia, tai haarautuvaa, jolloin luokka perii jonkin esivanhemman ominaisuudet useampaa kuin yhtä reittiä. Kun jälkeläisluokka perii esivanhempiluokkansa useampaa eri reittiä, puhutaan toistuvasta periytymisestä. Jos aliluokka perii saman luokan yliluokkana useampaan kertaan, on toistuva periytyminen välitöntä.

Periytymistä käytetään olio-ohjelmoinnissa hyvin eri tavoin ja hyvin erilaisiin tarkoituksiin. Erikoistaminen on periytymisen lajeista yleisin ja tärkein. Erikoistavassa periytymisessä aliluokan ilmentymä on yliluokan ilmentymän erikoistapaus (Halbert & O'Brien 1987). Erikoistavan periytymisen erityistapauksena pidetään määrittelyä (Budd 1991). Määrittelevässä periytymisessä kaikki käytettävät menetelmät, luokan liitymä, kuvataan jo yliluokassa, mutta niiden toteutus jätetään avoimeksi eli yliluokat ovat abstrakteja. Myös toteutus on yleisesti käytetty periytymisen laji. Toteutuksessa yliluokan ilmentymät ovat yksinään käyttökelvottomia, mutta niitä käytetään aliluokan llmentymän osana (Halbert & O'Brien 1987). Moniperiytyminen periytymisen lajina on yhdistävää periytymistä (Halbert & O'Brien 1987).

Periytymisen lajeista yleistäminen ja muuntelu ovat jossain määrin periytymisen väärinkäyttöä (Halbert & O'Brien 1987), mutta tarpeellisia joissakin tapauksissa. Yleistävä periytyminen on erikoistavan periytymisen vastakohta, jota joudutaan käyttämään, kun yliluokkaa ei jostain syystä voida muuttaa (yliluokka on esimerkiksi kirjastoluokka). Kahden luokan välinen periytyminen on muuntelevaa periytymistä, jos yli- ja aliluokan välillä ei ole erikoistamissuhdetta, mutta niillä on paljon yhteisiä ominaisuuksia. Tällaisessa tilanteessa tulisi luokkien yhteiset ominaisuudet siirtää näiden yhteiseen yliluokkaan. Muuntelevan periytymisen käyttäminen on soveliasta, jos edellä kuvatuille luokille ei voida luoda yhteistä yliluokkaa (alkuperäinen yliluokka on esimerkiksi kirjastoluokka). Periytyminen on laajentavaa (Budd 1991) jos aliluokka lisää yliluokkaan uusia ominaisuuksia ja rajoittavaa (Budd 1991) jos aliluokka ei tarjoa omille aliluokilleen tai asiakkailleen kaikkia kaikkia yliluokkansa näkyviä ominaisuuksia.

![](/assets/images/inheritance.png) Perintä, kuva https://www.raywenderlich.com/599-object-oriented-programming-in-swift

### Monikäyttöisyys

Budd (1991) määrittelee monikäyttöisyyden muuttujan ominaisuudeksi, jonka ansiosta muuttujan arvoksi voidaan asettaa eri tyyppejä olevia arvoja. Menetelmä on monikäyttöinen, jos sillä on ainakin yksi monikäyttöinen argumentti (implisiittinen itseviite mukaanlukien). Myös menetelmän, jonka nimeä on kuormitettu tekemällä siitä useita eri toteutuksia, katsotaan olevan monikäyttöinen.

Luokkahierarkiaan kuuluvien luokkien ilmentymät ovat monikäyttöisiä, koska luokasta periytymisellä johdetun aliluokan ilmentymää voidaan käsitellä myös yliluokan ilmentymänä aliluokan ilmentymän sisältäessä kaikki yliluokan ilmentymän ominaisuudet. Edellämainitun ansiosta voidaan sekä yli- että aliluokan ilmentymiin soveltaa yliluokan menetelmiä. Koska yliluokan menetelmät voidaan kumota aliluokassa, voidaan luokkien ilmentymiin soveltaa myös samannimisiä, mutta toteutukseltaan erilaisia menetelmiä.

Monikäyttöisyys voi olla joko yleistä tai erityistä (Cardelli & Wegner 1985). Yleisessä monikäyttöisyydessä toteutukseltaan samaa menetelmää voidaan soveltaa eri luokkien ilmentymiin. Erityisessä monikäyttöisyydessä suoritetaan samannimisen menetelmän eri toteutuksia eri luokkien ilmentymille. Erityisestä monikäyttöisyydestä esimerkkejä ovat menetelmien ja operaattoreiden kuormitus sekä yksinkertaisimmillaan automaattinen tyypinmuunnos. Yleinen monikäyttöisyys jaetaan sisältyvään ja parametriseen monikäyttöisyyteen. Sisältyvää monikäyttöisyyttä esiintyy periytymisessä yliluokan menetelmien periytyessä aliluokalle. Yliluokan menetelmät ovat käytössä myös aliluokissa ja menetelmiä kutsuttaessa suoritetaan aina sama yliluokassa toteutettu koodi. Parametrisessa monikäyttöisyydessä menetelmät voidaan toteuttaa tietämättä argumenttien todellista tyyppiä. Parametrista monikäyttöisyyttä esiintyy esimerkiksi geneeristen luokkien toteutuksissa.

![](/assets/images/monikaytto.png)  Monikäyttöisyys, kuva https://www.freecodecamp.org/news/object-oriented-programming-concepts-21bb035f7260/

### Lisämateriaali

Hyvää lisämateriaali ovat esim seuraavat linkit:
https://www.freecodecamp.org/news/object-oriented-programming-concepts-21bb035f7260/
https://learntocodetogether.com/what-the-heck-is-oop/ (Java-kielellä)

### Luokkien käyttö

Tutustutaan seuraavaksi luokkien käyttöön esimerkin kautta. Jos tarvitsemme monimutkaisemman muuttujan esim. Vektorin joka osoittaa pisteestä x1,y1 pisteeseen x2,y2. Jos tekisimme tällaisen toteutuksen tarvitsisimme neljä erillistä muuttujaa, ja joutuisimme manuaalisesti ylläpitämän niiden suhdetta.

![](/assets/images/class_1.png) 

Koodissa tämä tarkoittaisi vaikeasti ylläpidettävää ratkaisua.

```c++

void printVector(double x0, double y0, double x1, double y1) {
 cout << "(" << x0 << "," << y0 << ") -> ("
 << x1 << "," << y1 << ")" << endl;
}

int main() {
 double x1 = 0.0;
 double y1 = 0.0;
 double x2 = 10.0;
 double y2 = 2.5;
 printVector(x1, y1, x2, y2);
}
```

Voimme yksinkertaistaa toteutusta määrittelemällä oman luokkamme nimeltä **Vector**.
Tässä luokassa meillä on käytössä, attribuutit:
- x0,y0,x1,y1
Methodit:
- printVector

Seuraavassa luokka Vector on kuvattu UML-kielellä. UML:llä voidaan mallintaa suurinosa ohjelmoinnissa käytettävistä malleista, esim. luokan osalta UML-tietoa löytyy: https://tietokantojen-perusteet-19.mooc.fi/osa-3/1-tiedon-kuvaaminen

![](/assets/images/class_model.png) 

#### Luokan määrittely

Luokka määritellään seuraavan syntaksin mukaisesti. Tässä määrittelemmen uuden Vector luokan.
Määrittely alkaa aina sanalla class, jota seuraa luokan nimi (isolla kirjotettuna on hyvä käytäntö)

![](/assets/images/class_def1.png) 

Luokan määrittelyssä esittellään luokan jäsenmuuttujat (attribuutit) sekä niiden näkyvyysalue. Jäsenmuuttujien osalta esimerkissä käytetään double -tietotyyppiä, mutta tämä tietotyyppi voi olla mikä tahansa, myös toinen luokka.

![](/assets/images/class_def2.png) 

Jäsenmuuttujat kuten myöhemmin jäsenfunktio voivat olla:
- julkisia (public), eli kaikilla on oikeus käyttää niitä. 

Voidaan määritellä myös ne yksityisiksi (private) tai suojatuiksi (protected).  

- Yksityiset jäsenet ovat käytössä vain luokan omissa jäsenfunktioissa, sekä erikseen määriteltyjen ystävien käytössä.  **Oletuksena luokan jäsenmuuttujat/-funktiot ovat yksityisiä**

- Suojattuja jäseniä voivat edellä mainittujen lisäksi käyttää johdetut toiset luokat, tätä käsitellään myöhemmin.  

Kun käytämme näkyvyysalueita oikein, piilotamme luokkamme käyttäjiltä turhat muuttujat ja funktiot. Näin käyttäjät voivat keskittyä vain niihin ominaisuuksiin joita haluamme heidän käyttävän. Eivätkä he pääse esimerkiksi vaikuttamaan luokan sisäiseen toimintaan. 

#### Luokan käyttäminen

Kun käytämme luokkaa luomme siitä olion (instance), jokainen olio elää omaa elämäänsä omassa muistialueessaan, ja näin ollen jokainen olio sisältää eri tietoa.

Olioiden luominen tapahtuu seuraavasti:

```c++

//Määritellään Vector luokka
class Vector 
{ 
       public: 
        double x0; 
        double y0; 
        double x1; 
        double y1; 
}; // <-- HUOM! Luokan määrittely päättyy ;

int main() 
{
    Vector v1; //Olio v1
    Vector v2; //Olio v2
}

```

Nyt oliot v1 ja v2 varataan omina muistialueinaan ja niiden arvot ovat satunnaiset, koska emme alusta luokan jäsenmuuttujien arvoja.

![](/assets/images/object_1.png) 

Nyt voimme käyttää olioita ja niiden jäsenmuuttujia. Kun haluamme käsitellä jäsenmuuttujia käytetään piste -syntaksia. esim. **olio.muuttujan_nimi**, sama koskee myöhemmin kun haluamme kutsua olion funkioita.

```c++
int main() 
{
    Vector v1; //Olio v1
    Vector v2; //Olio v2

    v1.x0 = 0;
    v1.y0 = 0;

    v1.x1 = 10;
    v1.y1 = 5;
}
```

Tämän myötä olio v1 saa jäsenmuuttujilleen arvot, ja olion v2 jäsenmuuttujien arvot pysyvät alustamattomina

![](/assets/images/object_2.png) 

Voimme käyttä nyt uutta luokkaamme myös funktiossa, muista että kääntäjä lukee koodi ylhäältä alas, joten luokan tulee olla määritelty ennen sen käyttöä.

```c++
 //Määritellään Vector luokka
    class Vector
    {
           public:
            double x0;
            double y0;
            double x1;
            double y1;
    }; // <-- HUOM! Luokan määrittely päättyy ;

    void tulostaVektori(Vector v);

    int main()
    {
        Vector v1; //Olio v1
        Vector v2; //Olio v2

        v1.x0 = 0;
        v1.y0 = 0;

        v1.x1 = 10;
        v1.y1 = 5;

            tulostaVektori(v1);
    }

    void tulostaVektori(Vector v)
    {
        cout << "start:" << v.x0 << "," << v.y0 << " end:" << v.x1 << "," << v.y1 << endl;
    }

```

Oliot voidaan sijoittaa myös samantietotyypin oliohin, näin oliossa olevat tieto kopioituu kohdeolioon

```c++
v2 = v1;
tulostaVektori(v2);
```


#### Luokat funktion parametreina

Luokat välitetään funktioille arvopohjaisesti kuten muutkin tietotyypit, jos halutaan muutaa olion arvoja funktiossa käytetään viittauksia.

Esimerkiksi vektorin alustaminen viittauksia käyttäen

```c++
void alustaVektori(Vector& v)
{
    v.x0 = 0;
    v.y0 = 0;
    v.x1 = 0;
    v.y1 = 0;
}
```

### Luokkien jäsenfunktiot

Koska funktion jäseniä ja toiminnallisuutta käsitteleävät funktiot liittyvät tiukasti funktion arvoihin ja sisäiseen toiminnallisuuteen on järkevää sijoittaa nämä luokan omiin funktioihin. 

Jäsenfunktioiden osalta noudatetaan samaa syntaksia kuin mitä olemme käyttäneet funktioiden määrittelyssä aiemmin. Jäsenfunktioissa voimme käsitellä jäsenmuuttujia suoraan (ilman viittausta olioon) ja vaikka kutsua toista jäsenfunktiota.

Jäsenfuktiot toimivat rajapintana luokan käyttämiselle, näin voimme piilottaa jäsenmuuttujat käyttäjiltä.

```c++
    //Määritellään Vector luokka
    class Vector
    {
           private: //Yksityiset jäsenmuuttujat
            double x0;
            double y0;
            double x1;
            double y1;


            public: //Julkiset jäsenfunktiot

            void tulostaVektori()
            {
                cout << "start:" << x0 << "," << y0 << " end:" << x1 << "," << y1 << endl;
            }

            void alustaVektori()
            {
                x0 = 0;
                y0 = 0;
                x1 = 0;
                y1 = 0;

                tulostaVektori();
            }

            //HUOMAA, jos parametrit ovat samannimiset kuin jäsenmuuttujat
            // viitataan jäsenmuuttujiin this-> operaatiolla
            void aseta(double x0, double y0, double x1, double y1)
            {
               this->x0 = x0;
                this->x1 = x1;
                this->y0 = y0;
                this->y1 = y1;
            }



    }; // <-- HUOM! Luokan määrittely päättyy ;


    int main()
    {
        Vector v1; //Olio v1
        Vector v2; //Olio v2

         //v1.x = 0; << EI SALLITTU ENÄÄ

        v2.alustaVektori();
        v1.alustaVektori();

        v1.aseta(5,5,10,10);

    }

```

### Luokkien konstruktorit (ja destruktori)

C++:ssa on kaksi erikoisjäsenfunktiota. Nämä ovat rakentaja (constructor) sekä hävittäjä (destructor). Nämä kaksi funktiota ovat tärkeässä roolissa luokan alustamisessa (rakentaja) sekä kun luokan elinaika päättyy ja se tuhotaan (destructor). Nämä funktiot nimetään aina: 

 
```
Rakentaja =  luokan_nimi  

Hävittäjä = ~luokan_nimi.  
```

Rakentajaa kutsutaan, kun luokasta tehdään olio ja hävittäminen vastaavasti kun se olio tuhotaan. Rakentajalla voi olla useita muotoja, hävittäjällä vain yksi. Rakentajalla voidaan välittää parametreja tai olla välittämättä. Hävittäjää tarvitaan erityisesti silloin, jos oliomme käyttää dynaamisesti varattuja resursseja (tästä aiheesta myöhemmin). 

**Huomaa että rakentaja (kuten ei myöskään hävittäjä) palauta mitään arvoa.** 

Luokalla voi olla useita rakentajia ja rakentaja funktiot voivat olla paramterillisia.

```c++
//Määritellään Vector luokka
class Vector
{
        private: //Yksityiset jäsenmuuttujat
        double x0;
        double y0;
        double x1;
        double y1;


        public: //Julkiset jäsenfunktiot

        //Perusrakentaja, alustaa arvot 0:lla
        Vector()
        {
            alustaVektori();
        }

            //Rakentaja, alustaa arvot parametreilla
        Vector(double x0, double y0, double x1, double y1)
        {
            this->x0 = x0;
            this->y0 = y0;
            this->x1 = x1;
            this->y1 = y1;
        }

            //Rakentaja, kopioi arvot toisesta olios
        Vector(Vector& v)
        {
            this->x0 = v.x0;
            this->y0 = v.y0;
            this->x1 = v.x1;
            this->y1 = v.y1;
        }

        //MUUT
        void tulostaVektori()
        {
            cout << "start:" << x0 << "," << y0 << " end:" << x1 << "," << y1 << endl;
        }

        void alustaVektori()
        {
            x0 = 0;
            y0 = 0;
            x1 = 0;
            y1 = 0;

            tulostaVektori();
        }

        //HUOMAA, jos parametrit ovat samannimiset kuin jäsenmuuttujat
        // viitataan jäsenmuuttujiin this-> operaatiolla
        void aseta(double x0, double y0, double x1, double y1)
        {
            this->x0 = x0;
            this->x1 = x1;
            this->y0 = y0;
            this->y1 = y1;
        }



}; // <-- HUOM! Luokan määrittely päättyy ;


int main()
{
    Vector v1; //Olio v1



    //v1.x = 0; << EI SALLITTU ENÄÄ

    //v1.alustaVektori();

    v1.aseta(5,5,10,10);
    v1.tulostaVektori();

    Vector v2(v1); //Alustetaan uusi vektori V1 arvoilla
    v2.tulostaVektori();


    Vector v3(1,2,4,6); //Alustetaan uusi määritetyillä arvoilla
    v3.tulostaVektori();
}

```

Esimerkkikoodi löytyy linkistä: https://github.com/centria/cpp-ohjelmointi-harjoitukset/blob/master/osa6_malli.cpp