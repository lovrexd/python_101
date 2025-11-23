# Strukture podataka

### Strukture podataka

*Strukture podataka* valja shvatiti kao *zbirke vrijednosti*, a ova dva
termina se često koriste i na engleskom (*data structure* i
*collection*). Upotrebe ovog koncepta su višestruke. Ponekad se neka
vrijednost po svojoj prirodi sastoji od više pod-vrijednosti. Spomenuli
smo već tekst koji je zapravo "niz znakova", a možemo tome dodati i
kojekakve složene vrijednosti poput datuma (tri cijela broja: dan,
mjesec i godina) ili osobnog imena (dva niza znakova: ime i
prezime[^1]).

Uz to, ponekad želimo provesti istu radnju na više objekata iste vrste.
Na primjer, recimo da želimo promijeniti kodnu stranicu svih tekstualnih
datoteka u nekom direktoriju: Prvo nam je potreban popis svih putanja do
datoteka koje planiramo procesirati (što je najčešće jednostavno popis
tekstualnih nizova), a zatim za svaku putanju usnimavamo datoteku i
zapisujemo tekst u drugu datoteku koja ima drugačiju kodnu stranicu.
Također, kad radimo s računalnim podacima, na primjer podacima o
knjigama ili o računima s blagajni, po prirodi stvari radimo sa
strukturama podataka. Kako bi uopće počeli raditi sa spomenutim
konceptima potrebno nam je prvo usvojiti neke osnove vezane uz strukture
podataka.

Postoje posebne *vrste vrijednosti* koje služe upravo strukturiranju
drugih vrijednosti odnosno koje nam omogućuju da okupljamo vrijednosti
bilo koje vrste u zbirke vrijednosti. Vrlo je korisno proučiti dvije
osnovne vrste struktura u Pythonu: popis (`list`) i rječnik (`dict`).
Učenjem ovih koncepata približavamo se i temeljima razmjene podataka u
mnogim web uslugama. Tome možemo dodati i skup (`set`) koji se nešto
manje koristi od popisa i rječnika, ali je u nekim slučajevima vrlo
korisna struktura.

#### Popis

*Popis* je niz objekata u kojem se svaki objekt može identificirati
putem indeksa pozicije na kojoj se nalazi. Već smo vidjeli da je string
zapravo popis znakova, ali ovo je poseban slučaj popisa koji dozvoljava
samo tekstualne znakove kao članove. Najčešće korištena struktura pomoću
koje se implementira popis bilo kojih vrsta vrijednosti u Pythonu je
`list`. Ovako definiran popis se može mijenjati i vjerojatno je najčešće
korištena struktura podataka u Python programima. Pogledajmo kako možemo
stvoriti popis i dohvatiti neki element iz njega.

``` python

>>> boje = ["crvena", "zelena", "plava"] # popis definiramo uglatim zagradama 
>>> print(boje) ["crvena", "zelena", "plava"]# elemente dohvaćamo uglatim zagradama i indeksom pozicije # indeksi počinju od 0, odnosno prvi element popisa se nalazi na indeksu 0 
>>> prva_boja = boje[0] 
>>> print(prva_boja) crvena
```

Primjer je prikazao najjednostavniji način stvaranja popisa. Zarezom
odvojeni objekti unutar uglatih zagrada stvaraju popis. Vrijedi
napomenuti i da unutar popisa, kao i u ostalim zagradama u Pythonu,
možemo dodavati nove retke radi preglednosti. Na primjer:

``` python

>>> boje_a = ["crvena", "zelena", "plava"] # popis definiramo uglatim zagradama# popis boje_b identičan je popisu boje_a, samo je raspisan drugačije 
>>> boje_b = [ "crvena", "zelena", "plava" ]
>>> boje_a == boje_b True
```

Mogućnost pisanja struktura u više redaka je korisna za osiguranje
preglednosti kod većih struktura (na primjer, popisa s 10 i više
elemenata).

Također, većina struktura pruža način kako dohvatiti neki individualni
objekt koji se u njoj nalazi. U mnogim slučajevima to je i poanta
korištenja Uglate zagrade odmah nakon imena neke varijable u Pythonu (i
mnogim drugim jezicima) označavaju upravo to: dohvati objekt(e) iz
strukture podataka putem vrijednosti u uglatim zagradama. Kod popisa je
to indeks, odnosno cijeli broj koji označava poziciju elementa u popisu,
gdje je indeks prvog objekta 0, a zadnji je jednak broju objekata u
popisu -1. Drugim riječima, validni indeksi za popis od četiri objekta
su 0, 1, 2 u 3. Obzirom da su adrese u popisu jasno definiran raspon
brojeva, kao indekse možemo koristiti i negativne brojeve i raspone
brojeva:

``` python

>>> boje = ["crvena", "zelena", "plava", "žuta", "ljubičasta"]# dohvati drugu boju iz popisa, odnosno boju na indeksu 1 
>>> druga_boja = boje[1] 
>>> print(druga_boja) zelena# dohvati zadnju boju iz popisa 
>>> zadnja_boja = boje[-1] 
>>> print(zadnja_boja) ljubičasta# dohvati raspon vrijednosti iz popisa 
>>> neke_boje = boje[1:4] # dohvaća vrijednosti pod indeksima 1, 2 i 3 
>>> print(neke_boje) ["zelena", "plava", "žuta"] # kod raspona indeksa, vrijednost prvog indeksa je uvijek # uključena u rezultat, a zadnja nije# ukoliko ispustimo zadnji indeks u rasponu, to znači "odaberi do kraja" 
>>> sve_osim_prve = boje[1:] 
>>> sve_osim_prve ["zelena", "plava", "žuta", "ljubičasta"]# ukoliko ispustimo prvi indeks u rasponu, to znači "odaberi od početka" 
>>> sve_osim_zadnje = boje[:-1] 
>>> sve_osim_zadnje ["crvena", "zelena", "plava", "žuta"]
```

Jedan od problema sa strukturama podataka je što je riječ o apstraktnim
konceptima za koje je pri prvom susretu teško prikazati praktične
primjere. Ipak, kako bismo se barem približili praksi pogledajmo kako
dobiti popis članova nekog direktorija:

``` python

>>> import os 
>>> os.listdir(’c:/test’) [’dat_a.pdf’, ’dat_b.docx’, ’dat_c.txt’, ’dir_a’, ’dir_b’]
```

Primjer prikazuje kako dobiti popis članova nekog direktorija odnosno
popis stringova koji su imena datoteka i pod-direktorija u nekom
direktoriju. U prikazanom slučaju na disku `c` postoji direktorij `test`
koji sadrži tri datoteke (`dat_a.pdf`, `dat_b.docx` i `dat_c.txt`) i dva
poddirektorija (`dir_a` i `dir_b`). Jednostavno dobiti popis članova
nekog direktorija, kao što vidimo, nije teško. Ipak, dok je samo po sebi
jasno kako bi ovakav popis mogao biti koristan, ima još puno posla kako
bi s ovime mogli učiniti nešo konkretno: razlikovati datoteke od
direktorija, izraditi pune putanje od imena, razlikovati različite vrste
datoteka, pristupati sadržaju datoteke i slično. Drugim riječima,
problem prvog dodira sa strukturama podataka je što su one vrlo važne za
programiranje gotovo bilo čega, ali primjeri koji bi prikazali njihovu
praktičnu uporabu su često preopširni ili prekompleksni za prvi susret.
Ovaj dio skripte će se, stoga, usredotočiti na jednostavne apstraktne
primjere rada sa strukturama podataka, a njihova praktična uporaba će se
prikazati u kasnijim većim primjerima koji rade nešto konkretno ili
zabavno.

##### Funkcija `list`

Kao i kod tzv. primitivnih vrsti vrijednosti u Pythonu (`int`, `float`,
`bool`, `str`), nazivi struktura vrijednosti su također i funkcije s
kojima možemo druge objekte pretvarati u tu strukturu. Funkcija `list`
prima jedan parametar i raščlanjuje poslanu vrijednost na sastavne
elemente te vraća rezultat kao popis.

Pogledajmo primjere:

U zadnjoj liniji prijašnjeg primjera vidimo grešku koja se javlja kada
pokušamo pretvoriti u popis nešto što se ne da raščlaniti na sastavne
djelove. U ovom slučaju radi se o cijelom broju. Kao što vidimo, poruka
kaže "objekt vrste int nije iterativan". Sjetimo se, kada je vrijednost
"iterativna", to znači da se po njoj ne može prebirati što je upravo
zahtjev da bi se nešto moglo pretvoriti u popis. Vrijednost moramo moći
"izlistati".

##### Promjene popisa

Najjednostavnija promjena popisa je promjena vrijednosti koja se nalazi
na nekom indeksu. Pogledajmo primjer:

``` python

>>> boje = ["crvena", "zelena", "plava"] 
>>> boje[1] = "ljubičasta" # postavi drugi element popisa na vrijednost "ljubičasta" 
>>> print(boje) ["crvena", "ljubičasta", "plava"]
```

Ostale promjene popisa se provode putem metoda koje pruža vrsta
vrijednosti *list*. Ovih metoda nema puno i većina ih provodi relativno
jednostavne i očekivanje radnje. Pogledajmo koje su to:

- *append* - dodaj novi član na kraj popisa

- *clear* - obriši sve članove popisa, odnosno isprazni popis

- *copy* - napravi neovisnu kopiju popisa u memoriji

- *extend* - proširi popis svim članovima drugog popisa

- *insert* - ubaci novi član u popis na određeni indeks

- *pop* - izbaci zadnji član iz popisa ili izbaci član na nekom indeksu

- *remove* - izbaci prvi član koji je pronađen u popisu

- *reverse* - obrni redoslijed članova popisa

- *sort* - sortiraj popis

Pogledajmo primjere:

``` python

>>> boje = ["crvena", "zelena", "plava"]# dodaj vrijednost na kraj popisa 
>>> boje.append("žuta") 
>>> print(boje) ["crvena", "zelena", "plava", "žuta"]# proširi popis svim vrijednostima iz drugog popisa 
>>> druge_boje = ["crna", "bijela"] 
>>> boje.extend(druge_boje) 
>>> print(boje) ["crvena", "zelena", "plava", "žuta", "crna", "bijela"]# ubaci vrijednost na određeni indeks 
>>> boje.insert(2, "zelena") 
>>> print(boje) ["crvena", "zelena", "zelena", "plava", "žuta", "crna", "bijela"]# dohvati i izbaci zadnju vrijednost u popisu 
>>> zadnja_boja = boje.pop() 
>>> print(zadnja_boja) bijela 
>>> print(boje) ["crvena", "zelena", "zelena", "plava", "žuta", "crna"]# dohvati i izbaci vrijednost u popisu na nekom indeksu 
>>> boje = ["crvena", "zelena", "zelena", "plava", "žuta", "crna"] 
>>> peta_boja = boje.pop(4) 
>>> print(peta_boja) žuta 
>>> print(boje) ["crvena", "zelena", "zelena", "plava", "crna"]# izbaci PRVU pronađenu vrijednost 
>>> boje.remove("zelena") 
>>> print(boje) ["crvena", "zelena", "plava", "crna"]# sortiraj popis 
>>> boje.sort() 
>>> print(boje) ["crna", "crvena", "plava", "zelena"]
```

##### Informacije o članstvu popisa

Uz navedene metode za promjene popisa, postoje i neke koje služe
informiranju o članovima popisa:

- *index* - dohvati prvi indeks na kojem se nalazi neki objekt ili javi
  grešku ukoliko taj objekt nije u popisu

- *count* - prebroji koliko se puta neki vrijednost pojavljuje u popisu

##### Prebiranje i funkcija *range*

Petlja "za svaki", naravno, normalno radi s popisima.

``` python

>>> boje = ["crvena", "zelena", "plava"] 
>>> for boja in boje: print(boja)
```

Rezltat:

``` python
crvena zelena plava
```

Uz navedeno, često je korisno prebirati po **indeksima**, a ne po
vrijednostima popisa. U tu svrhu, vrlo nam je korisna funkcija `range`.
Ta funkcija služi stvaranju niza brojeva od nekog početnog do nekog
završnog. Pogledajmo primjere:

``` python

>>> r = range(2, 10) 
>>> print(r) range(2, 10) # range nije popis! 
>>> print(list(r)) # ali bilo koji range možemo pretvoriti u popis [2, 3, 4, 5, 6, 7, 8, 9]
>>> r = range(0, 5) 
>>> print(list(r)) [0, 1, 2, 3, 4]
>>> r = range(5) # ako pošaljemo samo jedan broj, smatra se da je početni broj 0 
>>> print(list(r)) [0, 1, 2, 3, 4]
>>> boje = ["crvena", "zelena", "zelena", "plava", "crna"] 
>>> broj_boja = len(boje) 
>>> for i in range(broj_boja): print("Na indeksu", i, "nalazi se", boje[i])Na indeksu 0 nalazi se crvena Na indeksu 1 nalazi se zelena Na indeksu 2 nalazi se zelena Na indeksu 3 nalazi se plava Na indeksu 4 nalazi se crna
```

Kao što vidimo, funkcija `range` posebno je korisna za generiranje
validnih indeksa za popis. Kao i kod indeksa popisa, ova funkcija
uključuje prvu vrijednost, a zadnju ne. Na primjer, `range(0, 4)`
generira brojeve 0, 1, 2 i 3. Ukoliko traženi brojevi počinju od 0,
funkcija range se može pozvati sa samo jednim parametrom koji označava
do kojeg broja se generira. Ovo nam omogućuje da ukoliko želimo
generirati sve validne indekse za neki popis to možemo učiniti
jednostavnim izrazom `range(len(neki_popis))`.

Osim definiranja minimuma i maksimuma, `range` prima i opcionalni treći
parametar: korak (eng. *step*). Ovaj parametar je zadan na 1 i definira
pomak između dva broja koja se generiraju funkcijom `range`. Navedeno je
možda teže shvatiti kroz definiciju nego kroz primjer pa pogledajmo
jedan:

<div class="minipage">

``` python

>>> r = range(1, 10) 
>>> print(r) range(1, 10) 
>>> print(list(r)) [1, 2, 3, 4, 5, 6, 7, 8, 9]# range sa zadanim minimumom, maksimumom i korakom 
>>> r = range(1, 10, 2) 
>>> print(r) range(1, 10, 2) 
>>> print(list(r)) [1, 3, 5, 7, 9]
```

</div>

##### *list* i *tuple*

Do sada smo radili samo s popisom vrste `list`, ali to nije jedina vrsta
popisa. Glavna distinkcija između popisa u Pythonu ovisi o tome da li je
popis promjenjiv ili nepromjenjiv. `list` je, kao što smo vidjeli iz
primjera, promjenjiv popis. Postoji i nepromjenjivi popis koji se naziva
`tuple`. Dohvaćanje elemenata iz obje vrste popisa je identično, ali
`tuple` se ne definira kroz uglate već kroz oble zagrade, a u mnogim
slučajevima se može pisati i bez zagrada.

Kao što vidimo, razlika između prikazane dvije vrste popisa je u tome
što je `list` moguće mijenjati, a `tuple` ne. Sve što možemo raditi s
popisom vrste `tuple`, dakle, vrijedi i za popise vrste `list`, ali
`list` pruža mogućnost promjena u popisu, a `tuple` ne. Pokušaj
dodavanja nove vrijednosti u `list` je, na primjer, normalan postupak, a
pokušaj dodavanja nove vrijednosti u `tuple` javlja grešku jer je tuple
nepromjenjiv. S druge strane, dohvaćanje vrijednosti putem indeksa
funkcionira identično i za `list` i za `tuple`.

Dok je “popis” relativno jednostavan koncept, kada bismo se dublje
skoncentrirali na popis kao strukturu podataka u odnosu na računalo,
vidjeli bismo da postoje različite implementacije istog koncepta koje se
razlikuju u efikasnosti i mogućnostima. Neke implementacije, na primjer,
su visoko efikasne, ali ne dopuštaju nikakve promjene. Kod
implementacija koje omogućuju promjene, različite radnje mogu biti
različito efikasne (u računalnom žargonu “različito koštaju”) ovisno o
načinu implementacije popisa. Pythonov `list`, na primjer, je visoko
efikasan u dodavanju nove vrijednosti na kraj popisa kao i u izbacivanju
te vrijednosti, ali neefikasan u dodavanju vrijednosti na početak popisa
ili izbacivanja vrijednosti s početka popisa. Da situacija bude još
gora, dodavanje odnosno izbacivanje vrijednosti je tim manje efikasno
čim ima više objekata u popisu nakon objekta koji se dodaje ili
izbacuje.

Ukoliko želimo efikasno dodavati i izbacivati vrijednosti iz sredine
popisa, Python ima uključenu i treću implementaciju popisa koja je
dostupna iz modula `collections` i zove se `deque`. Zašto onda ne bismo
uvijek koristili `deque`? Zato jer za dodatne mogućnosti uvijek postoji
cijena pa je tako popis vrste `deque` manje memorijski efikasan od
popisa vrste `list`. U svakom slučaju, modul `collections`, kao što ime
kaže, donosi dodatne strukture podataka koje su specijaliziranije u
naravi od osnovnih struktura koje se prikazuju u ovom poglavlju i
uglavnom su njihove varijante.

#### Broj objekata u strukturi i provjera članstva

Osim spomenutih posebnih metoda koje dozvoljava struktura `list`,
postoje i dva općenita pitanja koja često želimo postaviti bilo kojoj
strukturi podataka. Ta pitanja su:

- Koliko ima vrijednosti u nekoj strukturi?

- Da li neka struktura sadrži neki određeni objekt?

##### Broj objekata u strukturi

Broj objekata u nekoj strukturi podataka često se naziva i “duljinom” te
strukture. Python funkcija `len` vraća upravo taj broj.

``` python

>>> boje = ["crvena", "zelena", "plava"] 
>>> n_boja = len(boje) 
>>> print(n_boja) 3
```

`len` je funkcija koja radi na svim vrstama objekata za koje je pitanje
"Koliko ima elemenata (tj. podobjekata) u ovom objektu?" validno. Ako
pitanje nije validno, odnosno objekt koji je poslan kao parametar ga ne
podržava, `len` javlja grešku.

Kao što je za očekivati, poziv funkcije `len` s cijelim brojem kao
parametrom javlja grešku koju možemo čitati kao "cijeli brojevi nemaju
broj elemenata". `len` teksta, međutim, vraća vrijednost jer je kod
teksta to "broj znakova".

##### Provjera članstva neke strukture

Također, postoji univerzalan način provjere da li se neka vrijednost
nalazi u određenoj zbirci vrijednosti i to putem operatora `in`.
Pogledajmo primjere:

``` python

>>> if "š" in "Krešimir": print(’"Krešimir" sadrži "š".’)"Krešimir" sadrži "š".
>>> boje = ["crvena", "zelena", "zelena", "plava", "crna"] 
>>> "zelena" in boje True
>>> "žuta" in boje False
```

#### Rječnik

Rječnik je skup “ključ: vrijednost“ parova. Za razliku od popisa,
rječnik nema značajan redoslijed objekata, već svaki objekt koji se
pohranjuje kao vrijednost ima vlastiti ključ odnosno “šifru” ili “ime”
po kojem ga se može dohvatiti. Rječnik se definira vitičastim zagradama
i s dvotočkom kao znakom koji razgraničuje ključeve od vrijednosti.
Pogledajmo primjer:

``` python

>>> data = "boja": "plava", "visina": 30 # rječnik s dva elementa # svaki element se sastoji od ključa # i vrijednosti koja mu je pridružena 
>>> print(data["boja"]) plava 
>>> print(data["visina"]) 30
```

Rječnik je vrlo intuitivna struktura za opis nekog predmeta odnosno za
strukturiranje metapodataka. Na primjer, metapodaci ugrađeni u neku
glazbenu datoteku mogli bi se prikazati kao:

``` python
Rječnici i metapodacilisting:dict_metapodaci track_data =  "artist": "Monty Python", "title": "Lumberjack Song", "album": "Monty Python Sings", "year": 1989
```

Osim toga, rječnik je, kao što ime kaže, koristan i za “prevođenje”
vrijednosti. Pogledajmo doslovan primjer. Recimo da dobivamo podatke
poput varijable “track_data” u primjeru niže iz neke vanjske usluge i
želimo prevesti ključeve (odnosno nazive polja) na neke naše nazive.

``` python
```

Prikazan kod ispisuje:

``` python
"album": "Monty Python Sings", "godina": 1989, "naslov": "Lumberjack Song", "umjetnik": "Monty Python"
```

Također, primijetimo da prebiranje po rječniku s petljom `for` prebire
po ključevima. Što ako želimo prebirati po vrijednostima ili po
ključevima i vrijednostima odjednom?

``` python
Prebiranje po vrijednostima rječnikalisting:dict_values for value in track_data.values(): # prebire po vrijednostima print(value)
```

Rezultat:

``` python
1989 Lumberjack Song Monty Python Sings Monty Python
```

Redoslijed vrijednosti po kojima se prebire za razliku od liste nije
konzistentan. U drugom prebiranju, redoslijed ispisanih vrijednosti može
biti drugačiji. Drugim riječima, adresa vrijednosti nije određena
pozicijom već imenom. Radi toga je često korisno i prebirati po
ključevima i vrijednostima odjednom. Pogledajmo kako:

``` python
for key, value in track_data.items(): # prebire po (ključ, vrijednost) parovima print(key, value)
```

Rezultat:

``` python
year 1989 title Lumberjack Song album Monty Python Sings artist Monty Python
```

##### Funkcija *dict*

Funkcija `dict` služi stvaranju rječnika. Kao i sve ostale funkcije koje
označavaju vrstu vrijednosti, poziv bez parametara stvara prazan
rječnik.

``` python

>>> d = dict() # isto što i d = 
>>> print(d)
```

Poziv na `dict` s imenovanim parametrima stvara novi rječnik s tim
parametrima kao ključevima.

``` python
Funkcija dict i imenovani parametrilisting:dict_imenovani_parametri d = dict(a=1, b=2) print(d)
```

*dict* može primiti i popis parova, odnosno popis popisa gdje svaki
pod-popis ima dva člana: ključ i vrijednost.

``` python
Funkcija dict i popis parovalisting:dict_parovi popis_parova = [ ["a", 1], ["b", 2], ["c", 1] ] d = dict(popis_parova) print(d) popis_parova = list(d.items()) # popis parova možemo i dohvatiti iz rječnika print(popis_parova)
```

#### Skup

Skup je implementacija matematičkog koncepta skupa: zbirka jedinstvenih
vrijednosti bez značajnog redoslijeda. U smislu onoga što već znamo o
Pythonu, skup možemo shvatiti kao samo ključeve rječnika bez pridruženih
vrijednosti.

``` python

>>> s = set() 
>>> s.add(1) 
>>> print(s) 1 
>>> s.add(2) 
>>> print(s) 1, 2 
>>> s.add(2) # skup već sadrži vrijednost 2 pa nema promjene 
>>> print(s) 1, 2
```

Skup je rjeđe korištena struktura od popisa i rječnika, ali je vrlo
korisna u nekim slučajevima.

##### Funkcija *set* i stvaranje novih skupova podataka

Kao i u matematici, skup se označava vitičastim zagradama. Razlika od
rječnika je što se skup ne sastoji od "ključ: vrijednost" parova, već od
individualnih elemenata. Nažalost, obzirom da se vitičaste zagrade
koriste i za rječnik i za skup, prazan skup **moramo** definirati pomoću
funkcije *set*. Kada želimo definirati skup postojećih vrijednosti,
možemo koristiti i vitičaste zagrade. Pogledajmo neke primjere
definicije skupova:

``` python

>>> s = # pažnja! prazan rječnik 
>>> print(s)
>>> s = set() # prazan skup 
>>> print(s) set()
>>> s = "a", "b", "c" # skup s članovima 
>>> print(s) "a", "c", "b"
>>> s = set("ana") # napravi skup od elemenata vrijednosti (npr, tekst) 
>>> s "a", "n"
>>> s = set(["ana"]) # napravi skup od elemenata popisa 
>>> s "ana"
>>> d = "a": 1, "b": 2, "c": 1 # definiraj neki rječnik 
>>> set(d) # ključevi rječnika kao skup "a", "c", "b" 
>>> set(d.values()) # sve različite vrijednosti u rječniku 1, 2
```

##### Operacije sa skupovima

Za razliku od popisa i rječnika, skup ne pruža način dohvata neke
odabrane vrijednosti iz zbirke. Drugim riječima, vrijednosti u skupu ne
možemo jednoznačno adresirati jer vrijednosti nemaju niti konzistentan
redoslijed (pa ne možemo koristiti poziciju neke vrijednosti kao indeks)
niti se vrijednosti mogu identificirati putem kakvog ključa. Zašto bismo
onda prikupljali vrijednosti u skupove? Skupovi omogućuju matematičke
operacije sa skupovima poput unije, presjeka i razlike, odnosno
operacije koje su vrlo korisne u radu s podacima. Pogledajmo primjere:

``` python

>>> a.intersection(b) # ili a & b "c", "b" 
>>> a & b # isto što i a.intersection(b) "c", "b" 
>>> a.union(b) # ili a | b "a", "d", "c", "b" 
>>> a.difference(b) # ili a - b "a" 
>>> b.difference(a) # ili b - a "d"
```

Također, svojstvo skupa da sadrži samo različite vrijednosti je često
korisno. Sljedeći primjer prikazuje kako ga možemo jednostavno
iskoristiti da prebrojimo sve jedinstvene vrijednosti u nekoj zbirci
vrijednosti.

``` python

>>> boje = ["crvena", "plava", "crvena", "zelena", "plava"] 
>>> skup_boja = set(boje) 
>>> print("N boja:", len(boje)) N boja: 4 
>>> print("N različitih boja:", len(skup_boja)) N različitih boja: 3
```

Prikazane strukture podataka izvrsan su prvi susret s temom i već samo
prikazani koncepti nas opunumoćuju ne samo u programiranju već i u
općenitom radu s podacima kao i u razumijevanju vezane tematike. U
idućem poglavlju je upravo riječ o osnovama korištenja ovih struktura za
obradu podataka.

### Uvod u programiranje s podacima

Strukture podataka su sastavan dio programiranja bez kojih nije moguće
zamisliti mnoge algoritme. Između ostalog, strukture podataka omogućuju
rad s podacima za potrebe analitike ili upravljanja. Dapače, jedna od
popularnijih namjena Pythona je upravo rad s podacima poput onih iz baza
podataka ili dohvaćenih kroz sučelja za razmjenu podataka.

U nastavku teksta slijede prvi koraci u razumijevanju obrade podataka u
odnosu na ranije opisane strukture, odnosno prvi koraci za korištenje
popisa (`list`, `tuple`) i rječnika (`dict`) za potrebe obrade podataka.
Spomenute strukture, uz bogate mogućnosti rada s tekstom te ostale
značajke Pythona, nam pružaju vrlo kvalitetnu platformu za rad s
podacima bilo koje vrste. Za razliku od specijaliziranih rješenja, lako
se prilagoditi kojekakvim specifičnostima podatkovnih zapisa s kojima
radimo te osmišljati rješenja za neočekivane probleme. Također, u nekim
slučajevima je vrlo korisno odraditi pripremu podataka u Pythonu (na
primjer dohvat i potrebne transformacije), a zatim podatke prebaciti u
specijaliziraniji statistički softver u kojem je lakše provesti
kompleksnije analitičke postupke.

Prilikom analitičkog rada s podacima, često se koriste dodatni Python
moduli koji donose nove strukture i mogućnosti (popularni su npr. Numpy
i Pandas). Ipak, za razumijevanje rada sa strukturiranim podacima, vrlo
je korisno osnovne koncepte usvojiti kroz jednostavne vrste vrijednosti
i strukture podataka pa tek zatim krenuti koristiti strukture fokusirane
na efikasnost ili gotova specijalizirana rješenja.

Prije no što krenemo u samo programiranje, pogledajmo neke strukturirane
podatke. Najčešća struktura s kojom se srećemo i koja nije striktno
vezana za računala je tablica. Pogledajmo pojednostavljen primjer
bibliografskih metapodataka u tabličnom obliku.

<div id="table:primjer">

| **Naslov** | **Autor** | **Godina** | **Izdavač** | **ISBN** |
|:---|:---|:---|:---|:---|
| Good Omens | Terry Pratchett & Neil Gaiman | 1990 | Gollancz | 0-575-04800-X |
| Interesting times | Terry Pratchett | 1994 | Gollancz | 0-575-05800-5 |
| Neverwhere | Neil Gaiman | 1996 | BBC Books | 0-7472-6668-9 |

Primjer jednostavne tablice

</div>

Započnimo jednostavnim pitanjem: "Kako postaviti tablične podatke u
oblik iskoristiv za programiranje?".

Rješenju možemo, naravno, pristupiti na više načina, a razumijevanje
mogućih rješenja i transformacija među njima je najvažniji početni korak
u radu sa strukturiranim podacima u Pythonu. Ovakav pristup nam pomaže
usvojiti strukture podataka za reprezentaciju samih podataka, a zatim i
kako se koristiti tim istim strukturama za potrebu transformiracije,
odabira i grupiranja podataka.

#### Tablica kao popis popisa

Prikazana tablica se sastoji od tri podatkovne jedinice (ovdje vrste
"knjiga") svaka od kojih je opisana s pet svojstava (naslov, autor,
godina, izdavač, ISBN) svako od kojih prima vrijednost. Sve vrijednosti
su u ovom početnom slučaju jednostavne, odnosno nemaju internu
strukturu[^2]. U prijašnjim rečenicama se namjerno ne koriste izrazi
"redak" i "stupac". Navedeno predstavlja općenito viđenje podataka koje
želimo postići ovom skriptom te povezati s programskim konceptima. Ipak,
krenimo prvo s poznatim konceptima svojstvenima tablici, a razlog
općenitijoj terminologiji gore će postati vidljiv kroz primjere odnosno
strukture podataka koje ćemo koristiti za kodifikaciju informacija na
različitim razinama.

Razmislimo o izjavi "U prikazanoj tablici svaki redak je knjiga, a
autori se nalaze u drugom stupcu". Jedan način na koji možemo definirati
tablicu je popis redaka[^3]. Redak možemo definirati kao popis
vrijednosti u dogovorenom redoslijedu koji je zadan naslovima
stupaca[^4]. Kako bi znali koja vrijednost se nalazi u kojem stupcu
potrebno nam je "zaglavlje" tablice odnosno popis naziva stupaca. Kad
nam je definirano zaglavlje, na isti način možemo definirati i neki
redak u tablici.

Pogledajmo primjer:

```
zaglavlje = ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
redak = ['Interesting times',  'Terry Pratchett',  1994, 'Gollancz', '0-575-05800-5']
```

Tablica nam je onda jednostavno popis redaka:

```
zaglavlje = ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
tablica = [
    ['Good Omens',  'Terry Pratchett & Neil Gaiman',  1990, 'Gollancz', '0-575-04800-X'],
    ['Interesting times',  'Terry Pratchett',  1994, 'Gollancz', '0-575-05800-5'],
    ['Neverwhere',  'Neil Gaiman',  1996, 'BBC Books', '0-7472-6668-9']
]
```

Na ovaj način možemo početi raditi s ovim podacima. Ova struktura nam
već, na primjer, dopušta odgovor na jednostavna pitanja poput "Koliko
ima knjiga u našim podacima?" s izrazom `len(tablica)`. Ovo je dobar
trenutak i da se zapitamo zašto zaglavlje držimo izdvojeno. Mogli smo ga
uključiti kao što je uobičajeno u raznom softveru kao "prvi redak u
tablici":

```
tablica = [
    ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
    ['Good Omens',  'Terry Pratchett & Neil Gaiman',  1990, 'Gollancz', '0-575-04800-X'],
    ['Interesting times',  'Terry Pratchett',  1994, 'Gollancz', '0-575-05800-5'],
    ['Neverwhere',  'Neil Gaiman',  1996, 'BBC Books', '0-7472-6668-9']
]
```

Ipak, ovakav pristup je problematičan. Uključili smo zaglavlje, odnosno
dio sheme podataka, u same podatke! Zaglavlje ne predstavlja "jednu
knjigu". Kada razmislimo o tome što sada znači rezultat izraza
`len(tablica)` greška postaje očita. Drugim riječima, valja jasno
odvajati "shemu podataka" ili "metapodatke" od samih "podataka o nečemu"
jer ćemo tako imati znantno manje problema u kasnijoj obradi i pohrani
ovakvih podataka.

Kako funkcionira adresiranje u ovakvoj strukturi? Jednostavno, indeks u
glavnom popisu ("tablici") je broj retka, a indeks u svakom pod-popisu
("retku") je broj stupca. Pročitajmo, na primjer, drugi redak i
vrijednost svojstva "Godina" tog retka.

```
drugi_redak = tablica[1]  # prvi redak je na indeksu 0!
godina = drugi_redak[2]   # treći stupac

# ili jednostavno
godina = tablica[1][2]
# odnosno dohvati element na indeksu 1 i zatim dohvati element na 
# indeksu 2 u dohvaćenom elementu
```

Ako se prisjetimo nekih dodatnih radnji s popisima, sjetit ćemo se i da
je moguće dohvatiti indeks neke poznate vrijednosti u popisu. Pogledajmo
kako iskoristiti ovaj trik u kontekstu prikazanih struktura.

```
# dohvati indeks za godinu putem indeksa naziva u zaglavlju
i_godina = header.index('Godina')
# dohvati element na indeksu 1 i zatim dohvati element na istom indeksu na kojem 
# se nalazi 'Godina' u zaglavlju
godina = tablica[1][i_godina]
```

#### Tablica kao rječnik popisa

Do sada smo, kao i u npr. Excelu, vrijednosti identificirali putem
indeksa retka i indeksa stupca. Veliki problem s identifikacijom putem
indeksa je to što su promjenjivi. Ako se, na primjer, referiramo na
jedinicu u retku pod indeksom 5, ta jedinica će se promijeniti nakon
sortiranja tablice! Drugim riječima, indeksi ne identificiraju
jednoznačno neku jedinicu ili svojstvo, već trenutačnu poziciju te
jedinice odnosno svojstva u odabranoj strukturi podataka. U tipičnim
tablicama se redoslijed stupaca relativno rijetko mijenja pa su indeksi
svojstava često stabilni, ali reci se često dodaju i sortiraju pa
indeksi redaka nisu dobar identifikator individualnih zapisa.

Što ako želimo tablicu strukturirati tako da retke, odnosno individulne
zapise, možemo dohvaćati preko neke stabilne šifre? Iskoristimo za
primjer polje ISBN i postavimo tablicu tako da je struktura koja čuva
retke rječnik te u kojem su ključevi ISBN vrijednosti, a reci, isto što
i prije, odnosno popis vrijednosti kod kojeg je redoslijed zadan
zaglavljem.

```
zaglavlje = ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
tablica = {
    '0-575-04800-X': ['Good Omens',  'Terry Pratchett & Neil Gaiman',  1990, 'Gollancz', '0-575-04800-X'],
    '0-575-05800-5': ['Interesting times',  'Terry Pratchett',  1994, 'Gollancz', '0-575-05800-5'],
    '0-7472-6668-9': ['Neverwhere',  'Neil Gaiman',  1996, 'BBC Books', '0-7472-6668-9']
}
```

Individualna podatkovna jedinica nam je ostala identična kao i u prvoj
strukturi tabličnih podataka (popis vrijednosti), ali struktura koja
sabire podatkovne jedinice se promijenila kako bi omogućila direktno
adresiranje putem nekog jedinstvenog identifikatora.

Kako adresirati podatke u ovakvoj strukturi podataka možemo vidjeti u
primjeru
<a href="#listing:rjecnik_popisa_dohvat" data-reference-type="ref"
data-reference="listing:rjecnik_popisa_dohvat">[listing:rjecnik_popisa_dohvat]</a>.

```
# dohvati redak pomoću ISBN-a
redak_za_isbn = tablica['0-575-05800-5']  
# dohvati treći "stupac"
godina = redak_za_isbn[2] 

# ili jednostavno
godina = tablica['0-575-05800-5'][2] 
```

Što ako imamo podatke kao popis popisa, a želimo rječnik popisa? Upravo
ćemo podatke zapakirane kao popis popisa često dobivati prilikom
komunikacije s relacijskim bazama ili usnimavanja podataka izvezenih iz
relacijskih baza ili softvera koji funkcionira na razini tablica poput
Excela i SPSS-a. Proceduru za pretvaranje iz jedne strukturu u drugu
možemo vidjeti u primjeru
<a href="#listing:pp_u_rp1" data-reference-type="ref"
data-reference="listing:pp_u_rp1">[listing:pp_u_rp1]</a>.

```
zaglavlje = ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
tablica = [
    ['Good Omens',  'Terry Pratchett & Neil Gaiman',  1990, 'Gollancz', '0-575-04800-X'],
    ['Interesting times',  'Terry Pratchett',  1994, 'Gollancz', '0-575-05800-5'],
    ['Neverwhere',  'Neil Gaiman',  1996, 'BBC Books', '0-7472-6668-9']
]

# napravi prazan rječnik u koji će se dodavati podaci
tablica_rjecnik = {}

for redak in tablica:
    # dohvati vrijednost koju koristimo kao ključ
    isbn = redak[4]
    # postavi redak u tablica_rjecnik kao vrijednost
    tablica_rjecnik[isbn] = redak

godina = tablica_rjecnik['0-575-05800-5'][2] 
```

Što ako ne postoji vrijednost koja se može koristiti kao šifra u
tablici? Najjednostavnija strategija izrade jedinstvene šifre je
dodjelom tekućeg broja. Ova strategija je prikazana u primjeru
<a href="#listing:pp_u_rp2" data-reference-type="ref"
data-reference="listing:pp_u_rp2">[listing:pp_u_rp2]</a> :

```
# tablica je ista kao i u prošlom primjeru

# napravi prazan rječnik u koji će se dodavati podaci
tablica_rjecnik = {}
# postavi šifru na neku početnu vrijednost
sifra = 0

for redak in tablica:
    # povećaj šifru za jedan (čime svaki redak garantirano dobiva jedinstven broj za šifru)
    sifra += 1
    # postavi redak u tablica_rjecnik kao vrijednost
    tablica_rjecnik[sifra] = redak
    
# pažnja: broj 1 u sljedećem izrazu izrazu nije indeks već šifra!
godina = tablica_rjecnik[1][2] 
```

Ovako dodijeljene šifre inicijalno su jednake indeksima redaka u ulaznoj
tablici, ali nisu osjetljive na promjene u sortiranju. Drugim riječima,
imaju prednost da ako zapamtimo neki skup šifri poput {3, 7} kao, na
primjer, rezultat pretrage, taj popis šifri je garantirano trajno
validan jer identifikacija redaka ne ovisi o trenutačnom poretku
tablice. Dapače, ako nam je tablica rječnik, redoslijed redaka
jednostavno više ne postoji! [^5].

Također, vrijedi i dobro razmisliti koju vrijednost koristiti kao šifru.
ISBN, na primjer, nam često ne zadovoljava potrebe za šifru jer jedno
djelo može imati više ISBN identifikatora ovisno o digitalnoj ili
papirnatoj inačici, tvrdom i mekom uvezu te ISBN 10 i 13 varijantama.
Drugim riječima, može postojati takav ISBN broj koji mi ne koristimo kao
ključ, a koji identificira knjigu "Neverwhere" u nekom njezinom obliku.
Možda i želimo da jedan naš "redak" sadrži sve ISBN-ove koje se prema
našim kriterijima odnose na isti entitet odnosno, u ovom slučaju, djelo.
Ako je tako, tada bi također dodijelili svoje šifre kao u prijašnjem
primjeru.

#### Tablica kao rječnik rječnika

U prošloj seriji primjera, riješili smo se redoslijeda redaka za potrebe
identifikacije i dodijelili svoje šifre. Fokusirajmo se sada na redak.
On nam je dosada bio popis vrijednosti, odnosno popis "stupaca". Svaki
od ovih stupaca međutim, već ima svoje ime. Možemo li se unutar retka
referencirati na vrijednosti putem naziva vrijednosti, a ne putem
indeksa "stupca"? Dapače, vrijeme je da se odmaknemo od koncepta
"stupca" i krenemo pričati o atributima, odnosno svojstvima.

Postavimo redak kao rječnik u kojem su ključevi nazivi svojstava (i.e.
"stupaca u tablici"), a vrijednosti u rječniku su upravo vrijednosti tih
svojstava.

```
redak = {
   'Naslov': 'Interesting times', 
   'Autor': 'Terry Pratchett',
   'Godina': 1994,
   'Izdavač': 'Gollancz',
   'ISBN': '0-575-05800-5'
}

godina = redak['Godina']
```

"Tablica" ovakvih predmeta može biti bilo popis ovakvih rječnika ili
rječnik ovakvih rječnika. Upravo nam je rječnik rječnika posebno korisna
struktura. Recimo da smo sve retke postavili kao u primjeru gore i zatim
ih postavili kao vrijednosti u rječnik gdje su ključevi ISBN
identifikatori, tada bi godinu neke knjige mogli adresirati kao u
sljedećem primjeru:

```
tablica_rjecnik = {
    '0-575-05800-5': {
       'Naslov': 'Interesting times', 
       'Autor': 'Terry Pratchett',
       'Godina': 1994,
       'Izdavač': 'Gollancz',
       'ISBN': '0-575-05800-5'
    },
    # ... ostali reci ispušteni iz primjera
}

godina = tablica_rjecnik['0-575-05800-5']['Godina'] 
```

Kao što vidimo, u ovoj strukturi se na sve referiramo preko šifri
odnosno naziva radije nego preko redoslijeda što je često prirodnije i
manje podložno greškama. Ovaj oblik je također puno bliži načinu na koji
se danas razmijenjuju podaci na webu, odnosno formatu JSON koji je
nastao upravo kako bi ovakve strukture mogli razmijenjivati među
sustavima.

Naravno, čest je slučaj da podatke primamo u tabličnoj strukturi (na
primjer, prilikom usnimavanja iz razgraničenog teksta ili pri dohvatu iz
relacijskih baza podataka) pa ako želimo raditi s podacima u ovom
obliku, moramo ih prvo restrukturirati. Pogledajmo prvo kako pretvoriti
individualan popis vrijednosti u rječnik vrijednosti.

```
# ulazni podaci
zaglavlje = ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
redak = ['Good Omens',  'Terry Pratchett & Neil Gaiman',  1990, 'Gollancz', '0-575-04800-X']

# izradi prazan rječnik koji ćemo popuniti ulaznim podacima
redak_rjecnik = {}

# zaglavlje i redak po definiciji imaju jednak broj vrijednosti
# vrijednost na indeksu "i" u retku odgovara svojstvu na indeksu "i" u zaglavlju
for i in range(len(header)):
    naziv = zaglavlje[i]  # dohvati naziv
    vrijednost = redak[i]  # dohvati vrijednost
    redak_rjecnik[naziv]  = vrijednost  # postavi vrijednost pod specifičan naziv u rječnik
```

Kao što vidimo, ne trebaju nam nikakvi novi koncepti s kojima već nismo
radili. U ovom istom primjeru mogli smo istim tim konceptima i
preimenovati i/ili ispustiti neke atribute. Evo varijante koja ujedno i
preimenuje atribute:

```
# ulazni podaci
zaglavlje = ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
redak = ['Good Omens',  'Terry Pratchett & Neil Gaiman',  1990, 'Gollancz', '0-575-04800-X']

# rječnik preimenovanja atributa
prevedi = {
    'Naslov': 'title',
    'Autor': 'author',
    'Godina': 'year',
    'Izdavač': 'publisher',
    'ISBN': 'ISBN'  # ovdje nema promjene u nazivu 
}

# izradi prazan rječnik koji ćemo popuniti ulaznim podacima
redak_rjecnik = {}  

# zaglavlje i redak po definiciji imaju jednak broj vrijednosti
# vrijednost na indeksu "i" u retku odgovara svojstvu na indeksu "i" u zaglavlju 
for i in range(len(header)):
    naziv = zaglavlje[i]    # dohvati naziv
    naziv = prevedi[naziv]  # prevedi naziv
    vrijednost = redak[i]   # dohvati vrijednost
    redak_rjecnik[naziv]  = vrijednost  # postavi vrijednost pod specifičan naziv u rječnik
```

Pogledajmo sad kako ovo primijeniti na cijelu tablicu. Primjer niže
jednostavno spaja primjere
<a href="#listing:pp_u_rp2" data-reference-type="ref"
data-reference="listing:pp_u_rp2">[listing:pp_u_rp2]</a> i
<a href="#listing:popis_u_rjecnik" data-reference-type="ref"
data-reference="listing:popis_u_rjecnik">[listing:popis_u_rjecnik]</a>.

```
# ulazni podaci
zaglavlje = ['Naslov', 'Autor', 'Godina', 'Izdavač', 'ISBN']
tablica = [
    ['Good Omens',  'Terry Pratchett & Neil Gaiman',  1990, 'Gollancz', '0-575-04800-X'],
    ['Interesting times',  'Terry Pratchett',  1994, 'Gollancz', '0-575-05800-5'],
    ['Neverwhere',  'Neil Gaiman',  1996, 'BBC Books', '0-7472-6668-9']
]

# rječnik preimenovanja atributa
prevedi = {'Naslov': 'title', 'Autor': 'author', 'Godina': 'year', 
'Izdavač': 'publisher', 'ISBN': 'ISBN'}

# izradi prazan rječnik za sve podatke
podaci = {}
# postavi brojač za šifre na 0
sifra = 0
# zaglavlje i redak po definiciji imaju jednak broj vrijednosti
# vrijednost na indeksu "i" u retku odgovara svojstvu na indeksu "i" u zaglavlju 
for redak in tablica:
    # izradi prazan rječnik koji ćemo popuniti ulaznim podacima
    redak_rjecnik = {}  
    for i in range(len(header)):
        # postavi vrijednost pod prevedeni naziv u rječnik
        prevedeni_naziv = prevedi[zaglavlje[i]]
        redak_rjecnik[prevedeni_naziv] = redak[i] 
    podaci[sifra] = redak_rjecnik
    sifra += 1
```

Sada kada možemo raditi s podacima na ovoj razini, relativno je lako
doraditi gore prikazan proces da, na primjer, ispušta neke atribute
i/ili jedinice koje nas ne zanimaju ili pak priprema vrijednosti
određenih atributa i slično.

#### Tablica vs. strukturirani podaci

Kako napredujemo mogućnostima u reprezentaciji tabličnih podataka,
možemo vidjeti da se sve više udaljavamo od koncepta tablice. Ovo i
želimo jer je struktura tablice često previše ograničavajuća, a i pomalo
neprecizna. "Tablica" je koncept koji se koristi šire od strukture
podataka, te je pitanje da li dopušta na primjer, koncepte poput
"spojenih ćelija" ili ugniježdenih struktura (na primjer popis
vrijednosti ili tablica kao vrijednost u "ćeliji").

Usredotočimo se stoga na redak. Ako ne razmišljamo o tome što on
predstavlja u kontekstu tablice već u kontekstu strukturiranih podataka,
možemo ga nazvati podatkovna jedinica, entitet, zapis ili što slično.
Naši podaci su skup tih jedinica, a jedinice dijele zajedničku
strukturu.

Vrijednosti nekih svojstava podatkovne jedinice također mogu biti
strukture vrijednosti, što tu podatkovnu jedinicu čini sve manje nalik
na redak u tablici. Promotrimo u našem primjeru vrijednosti za atribut
"autor". "Terry Pratchett & Neil Gaiman" nije neobična vrijednost budući
da neko djelo može imati više autora. To nam samo po sebi već govori da
je vrijednost atributa "autori" zapravo struktura vrijednosti i to popis
autora (odnosno stringova).

Pogledajmo kako postaviti naš bibliografski zapis za neku knjigu kako bi
dopuštao koautorstvo.

```
zapis = {
   'Naslov': 'Good Omens', 
   'Autor': ['Terry Pratchett', 'Neil Gaiman'],  # atribut Autor sad dopušta više vrijednosti!
   'Godina': 1990,
   'Izdavač': 'Gollancz',
   'ISBN': '0-575-05800-5'
}
# funkcija len sad računa broj imena autora, a ne broj slova u polju autori
broj_autora = len(zapis['Autor'])
# također, možemo dohvatiti npr. prvog autora
prvi_autor = zapis['Autor'][0]
```

Jednostavno rečeno, ako postavimo atribut "Autor" da može primati više
vrijednosti, tada u podacima dopuštamo koautorstvo i omogućavamo
odgovore na pitanja poput "Koliko autora je potpisano na neku
publikaciju?" i "Na koliko je publikacija neki autor potpisan?".
Također, individualna podatkovna jedinica nam sada ima ugniježđene
strukture (vrijednosti nekih svojstava su strukture vrijednosti, a ne
jedinične vrijednost) pa se više ne može zapisati kao redak u
tablicu![^6]

Ovu ideju je ne samo moguće već i preporučeno odvesti dalje. Na primjer,
kada razmislimo o individualnom imenu autora primijetiti ćemo da se ono
(najčešće) sastoji od imena i prezimena. Čim smo utvrdili da neka
vrijednost ima svoje dijelove, utvrdili smo da je vrijednost složena te,
shodno tome, da je struktura podataka primjeren način za reprezentaciju
ovakvih vrijednosti. Na primjer, osobno ime možemo prikazati kao:

```
osoba = {
    'ime': 'Terry', 
    'prezime': 'Pratchett'
}
```

Kako ovu ideju iskoristiti u našim podacima?

```
zapis = {
    'Naslov': 'Good Omens', 
    'Autor': [
        {'ime': 'Terry', 'prezime': 'Pratchett'},
        {'ime': 'Neil',  'prezime': 'Gaiman'},
    ],  
    'Godina': 1990,
    'Izdavač': 'Gollancz',
    'ISBN': '0-575-05800-5'
}

# još uvjek možemo sve što i prije
broj_autora = len(zapis['Autor'])
prvi_autor = zapis['Autor'][0]
# ali i više
prezime_prvog_autora = zapis['Autor'][0]['prezime']
```

Kao što vidimo, ovakvo strukturiranje nam omogućava nove radnje s
podacima jer se sada možemo referirati na individualne dijelove osobnih
imena. Sada nam je, na primjer, lakše generirati stringove u obliku "Ime
Prezime", "Prezime, Ime" ili "Prezime, I." za različite potrebe.

Zbirka ovakvih podatkovnih jedinica su naši "strukturirani podaci" s
kojima nam sada postaje idealno za raditi u programskom okruženju. Kako
ćemo konkretno postaviti podatke (popis popisa, rječnik rječnika, itd.)
ovisi o zadatku, odnosno o tome kako nam je najlakše pristupiti rješenju
nekog problema.

[^1]: Osobna imena mogu imati još djelova i upravljanje podacima o
    osobnim imenima je vrlo kompleksno, ali najjednostavniji slučaj nam
    je ovdje dovoljno dobar primjer.

[^2]: Pored toga što sam tekst već možemo shvatiti kao strukturu,
    odnosno niz znakova.

[^3]: Svaki redak je jedna "podatkovna jedinica" odnosno "instanca
    entiteta".

[^4]: Svaki stupac označava svojstvo.

[^5]: Naravno, uvijek ga možemo stvoriti po potrebi

[^6]: Strukturu podataka možemo zapisati kao **text** u ćeliju, ali ne
    možemo adresirati unutar tog teksta, što poražava svrhu. Također,
    neke relacijske baze poput PostgreSQLa od nedavno dopuštaju pohranu
    strukturiranih vrijednosti unutar ćelije i adresiranje unutar
    ćelije, što ih čini hibridnim radije no relacijskim bazama.
