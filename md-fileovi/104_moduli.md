# Moduli: Proširenja mogućnosti

Programski jezici tipično u svojoj osnovnoj specifikaciji definiraju
samo osnovne mogućnosti i vrste vrijednosti. Specifičnije radnje (poput
kopiranja datoteka, trigonometrijskih ili statističkih izračuna ili
slanja elektroničke pošte), vrste vrijednosti (poput datuma ili putanje
na disku) i konstante (poput broja $`pi`$) se ne nalaze u osnovnoj
specifikaciji već u proširenjima jezika. Ova proširenja se vrlo često na
engleskom zovu knjižnice (eng. *libraries*), a u Pythonu se zovu moduli
(eng. *modules*).

Python modul, dakle, unosi dodatne mogućnosti u jezik. To je ranije
napisan kôd čije elemente možemo ponovno koristiti u novim programima. U
računalnom slengu, modul možemo shvatiti kao *plug-in*. Već smo upoznali
jedan takav modul: `math`. Kako bi mogli početi koristiti modul,
potrebno ga je "uvesti" u vlastiti kôd.

``` python
Korištenje modula pomoću naredbe importlisting:moduli_import import math print(math.sqrt(2)) print(math.pi)
```

Rezultat koda gore je ispis korijena iz dva i pi konstante, ali to nije
zašto ga ovdje prikazujemo. Linija `import math` govori Pythonu da uveze
modul `math` koji je ostatku koda u toj datoteci dostupan kroz ime
`math` i to ime se ponaša kao varijabla. Svi članovi tog modula
(funkcije, vrste vrijednosti i konstante) dostupni su pisanjem nakon
točke. Kao i kod metoda, točka označava članstvo odnosno članove modula
koristimo pisanjem točke nakon imena modula kao gore u linijama
`math.sqrt(2)` i `math.pi`.

Dvije stvari su nam ovdje važne. Prva je da se kod uvoza modula događa
slična stvar kao i u pridruživanju vrijednosti varijabli: neko ime se
"rezervira" za određenu upotrebu. Pogledajmo primjer:

Riječ "math", naravno, nema posebno značenje u Pythonu pored toga što je
naziv standardnog modula i smije se koristiti proizvoljno. Kada ne
koristimo modul math, ovo nije problem. Ukoliko prikazano jest problem,
jer imamo vlastitu varijablu koju želimo zvati isto kao i neki modul
koji želimo koristiti, najbolje je promijeniti ime varijable, ali
postoji i mogućnost promjene naziva modula prilikom uvoza:

Također, Python dozvoljava i uvoz samo jednog člana nekog modula.

``` python

>>> from math import pi 
>>> print(pi) 3.141592653589793 
>>> pi = 100 
>>> print(pi) 100
```

Na ovaj način, ne uvozimo ime `math` već direktno ime `pi`. To znači da
nam ime `math` u ostatku koda nije relevantno, ali ako redefiniramo
varijablu `pi`, izgubiti ćemo vrijednost koju smo uvezli iz modula
`math`. Ovaj način uvoza je koristan kada želimo koristiti samo jedan
ili mali broj članova nekog modula jer možemo koristiti naziv člana
modula direktno (na primjer `pi`) radije nego u obliku `math.pi` (na
primjer `math.pi`). Kao i kod uvoza cijelih modula, članove možemo
preimenovati koristeći se riječi `as`.

``` python

>>> from math import pi as x 
>>> print(x) 3.141592653589793
```

## Standardna knjižnica

Kako to da smo nakon osnovne instalacije Pythona mogli jednostavno
napisati `import math` i modul `math` je dostupan? Kao što smo već u
uvodu spomenuli, jedna od odluka Pythona je da su “baterije uključene“.
To znači da Python dolazi s velikim brojem modula koji su uključeni u
instalaciju Pythona. Te module zajednički nazivamo “standardnom
knjižnicom“ i ona dolazi s velikim brojem modula koji proširuju Python s
kojekakvim mogućnostima. Popisu modula i dokumentaciji možete pristupiti
[ovdje](https://docs.python.org/3/library/index.html).

S mnogim korisnim modulima ćemo se upoznati kroz tekst, a nabrajati ih
sve ovdje ne bi bilo svrsishodno jer u standardnoj knjižnici postoji
velik broj modula. Slijedi odabir često korisnih modula kako bi dobili
dojam o čemu se radi i informirali se o mogućnostima koje su dostupne
kroz standardnu instalaciju Pythona:

- **rad s tekstom**

  - `string` - znakovi definirani prema ASCII standardu i dodatne radnje
    s tekstom

  - `unicodedata` - UNICODE šifrarnik za kodiranje teksta

  - `re` - regularni izrazi

- **rad s brojevima**

  - `math` - dodatne matematičke funkcije i konstante

  - `statistics` - dodatne statističke funkcije

  - `random` - generacija slučajnih brojeva

- **rad s vremenom**

  - `time` - očitanje vremena

  - `datetime` - vrste vrijednosti za datume kao i sate, minute ...

- **rad s putanjama i datotekama**

  - `pathlib` - vrsta vrijednosti za putanje na disku

  - `shutil` - radnje s datotekama, kao što su kopiranje, preimenovanje
    i brisanje

- **rad s podatkovnim datotekama**

  - `csv` - čitanje i pisanje razgraničenog teksta

  - `json` - čitanje i pisanje JSON datoteka

- **rad s internetom i webom**

  - `email, smtplib, imaplib` - elektronička pošta

  - `html, xml` - rad s HTML-om i XML-om

  - `urllib` - rad s URL-ovima, uključujući i dohvat podataka s weba

- **zapisivanje i komprimiranje podataka**

  - `pickle` - zapisivanje Python objekata na disk i usnimavanje istih

  - `sqlite3` - stvaranje SQLite relacijskih baza podataka

  - `zipfile` - rad sa zip komprimiranim datotekama

Sa spomenutim modulima smo tek zagrebli površinu standardne knjižnice.
Ipak, prikazali smo mnoge korisne module, a velik dio standardne
knjižnice ima veze temama koje su nam za sada prenapredne, kao što su to
funkcijsko programiranje, testiranje, profiliranje i debagiranje kôda,
asinkrono i višeprocesorsko programiranje i tako dalje. Stoga ćemo se za
sada zaustaviti s prikazom standardne knjižnice, a kroz ovaj tekst ćemo
se upoznati s mnogim modulima u praksi.

## Instalacija dodatnih modula

Python, dakle, dolazi s mnogim zanimljivim mogućnostima sam po sebi, ali
što ako nam treba više? Što ukoliko želimo zapisati .pdf, .docx ili
.xlsx datoteku, crtati rasterske ili vektorske slike, raditi napredne
znanstvene analize ili pak isprogramirati aplikaciju s grafičkim
sučeljem ili video igru?

Pored standardne knjižnice za Python postoji izuzetno velik broj modula
koje razvijaju korisnici. Mnogi od ovih modula su veliki i kvalitetni
projekti koji se već dugo razvijaju i koji se često koriste u znanosti i
industriji. Katalog dodatnih modula je dostupan kroz [Python Package
Index](https://pypi.org/) (odnosno PyPi) i sadrži preko 200 000 modula.
