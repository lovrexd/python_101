# Definicija vlastitih funkcija

Do sada smo već koristili mnoge funkcije koje dolaze ugrađene u Python
(npr. `print` ili `sum`) kao i one koje su dostupne kroz module
(`math.floor`).

Funkcije su jedan od osnovnih građevnih elemenata suvremenih programskih
jezika i primarna svrha im je implementacija "jedne radnje", koja može
biti vrlo jednostavna, ali i vrlo kompleksna. Definicija vlastitih
funkcija je stoga uobičajen postupak i služi smanjenju kompleksnosti
koda time što pruža definicije potrebnih radnji koje se zatim mogu
koristiti više puta. Pogledajmo prvo osnove definicije vlastitih
funkcija i detalje oko postavljanja parametara, pa ćemo zatim prikazati
korištenje funkcija u praktičnom primjeru.

Već smo rekli da funkcija prima nula ili više parametara, na temelju
njih izvršava određen kôd te vraća rezultat. Pogledajmo kako ovo izgleda
u praksi prilikom definicije jednostavne vlastite funkcije.

```
# def služi definiciji novih funkcija
def sum_two(x, y):
    # return označava kraj izvršavanja funkcije kao vrijednost koja se se smatra rezultatom
    return x + y
```

Primjer prikazuje definiciju funkcije koja prima dva parametra, zbraja
ih te vraća njihov zbroj. Drugim riječima, ova funkcija odgovara
operatoru `+`. Riječ `def` označava definiciju funkcije te se nakon nje
piše naziv funkcije koji podliježe pravilima imenovanju varijabli. Nakon
naziva funkcije se u oblim zagradama nabrajaju parametri funkcije.
Parametri funkcije su jednostavno varijable putem kojih korisnik
funkciji šalje vrijednosti potrebne za izračun. Funkcija iz primjera
prima dva parametra, `x` i `y`, koje se unutar tijela funkcije mogu
normalno koristiti kao varijable. Tijelo funkcije se podvlači pod samu
liniju koja označava početak definicije kao i kod npr. kondicionala i
petlji. Prije no što krenemo s primjerima korištenja funkcija u praksi,
nužno je naučiti kako se ponašaju nazivi varijabli te neke detalje oko
postavljanja parametara.

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

def sum(numbers): total = 0 for n in numbers: total += n return total
