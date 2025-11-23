# Definicija vlastitih funkcija

Do sada smo već koristili mnoge funkcije koje dolaze ugrađene u Python
(npr. `print` ili `sum`) kao i one koje su dostupne kroz module
(`math.floor`).

Funkcije su jedan od osnovnih građevnih elemenata suvremenih programskih
jezika i primarna svrha im je implementacija "jedne radnje", koja se
zatim može koristiti na više mjesta u nekom programu. Navedeno smanjuje
kompleksnost programa i sprječava ponavljanje kôda što samo po sebi čini
programe preglednijim te olakšava testiranje i umanjuje mogućnosti
grešaka u kôdu. Definicija vlastitih funkcija je stoga ne samo uobičajen
nego i praktički nužan postupak prilikom implementacije većih programa.
Pogledajmo jednostavan primjer:

```
# "def" služi definiciji novih funkcija
def sum(numbers):
    total = 0
    for n in numbers:
        total += n
    # "return" označava kraj izvršavanja funkcije te vraća vrijednost koja se se smatra rezultatom
    return total
```

Primjer prikazuje definiciju funkcije koja prima jedan parametar koji
mora biti popis brojeva, zbraja sve brojeve te vraća njihov zbroj.
Drugim riječima, ova funkcija oponaša ugrađenu funkciju `sum`. Riječ
`def` označava definiciju funkcije te se nakon nje piše naziv funkcije
koji podliježe pravilima imenovanju varijabli. Nakon naziva funkcije se
u oblim zagradama nabrajaju parametri funkcije. Parametri funkcije su
jednostavno varijable putem kojih korisnik funkciji šalje vrijednosti
potrebne za izračun. Funkcija iz primjera prima jedan parametar koji je
nazvan `numbers`. Nazivi parametara su zapravo nazivi varijabli koje
možemo koristiti unutar tijela funkcije. Tijelo funkcije se podvlači pod
samu liniju koja označava početak definicije funkcije kao što je slučaj
i kod kondicionala i petlji.

## Apstrakcija

U mnogim jezicima funkcija je temelj apstrakcije, a u nekim jezicima i
glavna organizacijska paradigma. Ovakvi jezici se nazivaju *funkcijski
jezici* i u njima je funkcija glavni temelj apstrakcije, a izbjegavaju
se promjene u stanjima i promjenjivi podaci.

Funkcije se u mnogim jezicima vežu uz klase odnosno nove vrste objekata.
Time funkcije najčešće postaju metode tih objekata kao što je, na
primjer, metoda `upper` vezana uz vrstu `str`. Navedeni pristup
programiranju se naziva *objektno orijentirano programiranje*, a jezici
koji se na njemu zasnivaju *objektno orijentirano jezici* i uvod se može
pronaći u poglavlju TODO.

Pogledajmo prvo osnove definicije vlastitih funkcija i detalje oko
postavljanja parametara, pa ćemo zatim prikazati korištenje funkcija u
praktičnom primjeru.

Već smo rekli da funkcija prima nula ili više parametara, na temelju
njih izvršava određen kôd te vraća rezultat. Pogledajmo kako ovo izgleda
u praksi prilikom definicije jednostavne vlastite funkcije.

Prije no što krenemo s primjerima korištenja funkcija u praksi, nužno je
naučiti kako se ponašaju varijable u tijelu funkcije odnosno koncept
"imenskog prostora" te neke detalje oko postavljanja parametara.

Abstrakcija

## Imenski prostor

Kôd koji sačinjava tijelo funkcije se izvršava vlastitom *imenskom
prostoru* odnosno nazivi varijabli se ne miješaju s nazivima varijabli
izvan funkcije. Prije no što krenemo u detalje pogledajmo primjer koji
prikazuje što ovo znači u praksi:

## Identifikacija parametara redoslijedom i imenom

## Posebne vrste parametara

### Niz od n parametara

### Parametri s arbitrarnim imenima

Kako bismo mogli definirati funkciju koja zbraja više od jednog broja
odnosno koja oponaša već postojeću funkciju `sum`?
