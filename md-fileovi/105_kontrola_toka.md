# Kontrola toka: Kondicionali, petlje i pokušaji

U programiranju ne bismo daleko dogurali kada bismo jedino mogli po redu
izvršavati jedinične radnje. S jedne strane moramo moći prema određenim
uvjetima odabrati koje naredbe će se izvršiti, a koje ne. Ovo postižemo
*kondicionalima*. S druge strane moramo moći ponavljati iste naredbe.
Ovo postižemo *petljama*. U nastavku ćemo se upoznati s detaljima i
riječ je o standardnim komponentama gotovo svih programskih jezika. U
mnogim jezicima visoke razine postoji i treći koncept u kontroli toka, a
to je *pokušaj* provođenja određenih naredbi s jasno definiranim kôdom
koji će se izvršiti ako neka od naredbi ne uspije.

## Kondicionali: Ako ... onda ...

Kondicionali služe *odabiru* kôda koji će se izvršiti. Kada su neke
linije ovisne o kondicionalu, tada se neće izvršavati uvijek već samo
kada su određeni uvjeti zadovoljeni. Time dobivamo mogućnosti poput:
"ako se neki izraz evaluira kao True, napravi nešto; a ako ne, napravi
nešto posve drugo". Na taj način možemo reći stvari poput:

- Ako direktorij ne postoji, stvori ga.

- Ako datoteka postoji pitaj korisnika da li ju želi prepisati novom
  datotekom.

- Ako korisničko ime već postoji, javi da je zauzeto, a ako korisničko
  ime ne postoji, stvori novog korisnika.

- Ako je korisnik upisao odgovor "a", javi da je odgovor točan, a ako je
  korisnik upisao "b", "c" ili "d" javi da je odgovor netočan, a u svim
  ostalim slučajevima javi da odgovor nije prepoznat.

<div class="important">

Kondicionali Kondicionali služe uvjetnom izvršavanju kôda. Oni prema
određenim uvjetima odabiru koji će se reci izvršiti, a koji ne.

</div>

Kondicionale u programskim jezicima tipično reprezentiramo sa složenom
izjavom `if`, a minimalan oblik te izjave u Pythonu je:

``` python
Najjednostavniji oblik kondicionalalisting:kondicional1 if <izraz>: neka radnja
```

"Neka radnja" se izvršava samo ako izraz rezultira vrijednošću koja se
procjenjuje kao `True` (vidi poglavlje o booleovim vrijednostima za
detalje). Ova radnja se mora sastojati od barem jedne linije kôda, ali
može se sastojati i od više njih. Konkretnije, ispod svake `if` izjave
se očekuje uvučeni blok kôda. Taj blok koda, kao što je već rečeno, se
naznačuje tako što su sve linije u bloku jednako uvučene i izvršava se
samo ako je uvjet zadovoljen, a u suprotnom se preskače.

Što se uvlačenja kôda tiče, u Pythonu se uvijek uvlači nakon dvotočke
koja se, između ostalog, koristi u kondicionalima i petljama. Općenito
je pravilo da Python nakon retka koji završava s dvotočkom očekuje barem
jednu uvučen redak kôda odnosno minimalan blok kôda.

Standard u Pythonu je kôd uvlačiti sa četiri razmaka koji se u
prilagođenom softveru dobivaju pritiskom na tipku "tabulator" odnosno
"tab". Ovaj koncept se naziva "mekanim tabulatorom" (eng. *soft tab*)
jer služi istome čemu služi i sam znak tabulator, ali izbjegava taj znak
(što ima i smisla jer je tabulator po definiciji razmak varijabilne
dužine). Moguće je koristiti i znak tabulator, ali se treba pobrinuti da
se ne miješaju tabulatori i razmaci. Navedeno zvuči kompleksnije no što
je slučaj u praksi jer se za ujednačenost uglavnom pobrine softver u
kojem programiramo.

Moguće je napisati i kondicional koji će uvijek izvršiti neki kôd tako
što ga proširimo s komponentom `else` koja znači "u svim ostalim
slučajevima".

``` python
Kondicional koji će uvijek izvršiti radnjulisting:kondicional3 if <izraz>: neka radnja else: # u svim ostalim slučajevima neka druga radnja
```

U ovom obliku, "neka radnja" se izvršava kao i u prošlom, ali ako se ne
izvrši, tada će se izvršiti "neka druga radnja". Drugim riječima ovakav
kondicional će, za razliku od prošlog oblika, uvijek izvršiti neke
naredbe. Pogledajmo neke konkretne primjere:

Primjer prikazuje tri kondicionala. Prvi kondicional radi nešto samo ako
je uvjet zadovoljen. Druga dva kondicionala uvijek rade nešto jer imaju
komponentu `else` čiji kôd se izvršava kada niti jedan drugi uvjet nije
zadovoljen. Izvršavanje prikazanog koda, dakle, ispisati će dvije ili
tri rečenice jer prvi prikazani kondicional nema komponentu `else` dok
druga dva imaju. Koje su to?

<div class="pythonp">

<a href="#listing:kondicional4" data-reference-type="ref"
data-reference="listing:kondicional4">[listing:kondicional4]</a> x je
veće ili jednako y x + y je manje od 10

</div>

U prijašnjem primjeru svi izrazi koji se pojavljuju kao uvjeti se
evaluiraju u booleove vrijednosti. Kad želimo vidjeti rezultat određenog
izraza najjednostavnije je to probati u Python komandnoj liniji.

Što bi se dogodilo da smo koristili izraze koji se ne evaluiraju u
booleovu vrijednost poput `x + y`? U Pythonu je za potrebe kondicionala
moguće i implicitno pretvoriti bilo koju vrijednosti u booleovu
vrijednost. Drugim riječima, izjava `if vrijednost:` se izvršava kao da
smo pisali `if bool(vrijednost):`. Sjetimo se, izraz se uvijek evaluira
u vrijednost pa ranije napisano ujedno znači i `if bool(izraz)`.
Pogledajmo primjer:

<div class="pythonp">

<a href="#listing:kondicional5" data-reference-type="ref"
data-reference="listing:kondicional5">[listing:kondicional5]</a> bool(b)
se evaluira u True bool(x + y) se evaluira u True

</div>

Kako možemo napisati kondicional koji ima više od jednog eksplicitnog
uvjeta (ne računajući `else`)? U kondicionalima se često koriste dodatne
komponente *else if* koje služe upravo ovome. Python te riječi skraćuje
u riječ `elif`. Kondicional sa svim dozvoljenim komponentama izgleda
ovako:

``` python
Kondicional sa svim komponentamalisting:kondicional6 if <izraz1>: radnja 1 elif <izraz2>: radnja 2 elif <izraz3>: radnja 3 ... else: radnja n
```

A evo i konkretnog primjera kondicionala sa svim komponentama:

<div class="pythonp">

<a href="#listing:kondicional6" data-reference-type="ref"
data-reference="listing:kondicional6">[listing:kondicional6]</a> slučaj
"x je 3"

</div>

Drugim riječima, svaki kondicional ima nužno jedan `if` slučaj, a može
imati i bilo koji broj `elif` slučajeva i jedan `else` slučaj. Ovakav
kondicional smo već vidjeli u primjeru
<a href="#listing:kviz" data-reference-type="ref"
data-reference="listing:kviz">[listing:kviz]</a>, a u idućim poglavljima
ćemo za vježbu isprogramirati nešto konkretnije i iskoristiti
kondicionale. Upoznajmo se ipak prije toga i s petljama i pokušajima
kako bismo zaokružili koncept "kontrole toka".

## Petlje: ponavljanje naredbi

Petlje služe *ponavljanju* jedne ili više naredi. S petljama možemo dati
instrukcije poput "ponovi kôd za svaki element u popisu" ili "ponavljaj
neki kôd sve dok uvjet nije zadovoljen". Time možemo izraditi programe
koji na primjer crtaju geometrijske oblike, izrađuju bibliografski zapis
za svaku knjigu u nekoj bazi podataka ili čekaju korisnički unos i
ponavljaju se sve dok korisnik ne zatraži izlaz iz programa.

<div class="important">

Petlje Petlje ponavljaju naredbe. Iste naredbe treba ponavljati
petljama, a ne dupliciranjem kôda.

</div>

### Za svaki

Petlja koja se vrlo često koristi u programiranju, a u Pythonu je se
najčešće koristi petlja `for`. Kao i kod kondicionala, ovo je složena
izjava. Python koristi *for each* varijantu ove petlje koju skraćuje u
naziv `for`. Drugim riječima, `for` u Pythonu valja čitati "za svaki" i
ova petlja ponavlja naredbe za svaki element u nekom skupu
elemenata[^1]. Do sada jedina vrsta vrijednosti koju smo upoznali i koja
se može raščlaniti na elemente je `str`, odnosno niz znakova pa ćemo
upravo tu vrstu vrijednosti koristiti za primjere. Petlja `for` će
postati korisnija kada naučimo i strukture podataka o čemu je riječ u
zasebnom poglavlju.

Petljom `for` je dakle moguće provesti jednu ili više radnji za svaki
znak u nekom tekstu. Pogledajmo kako:

<div class="pythonp">

<a href="#listing:for_basic" data-reference-type="ref"
data-reference="listing:for_basic">[listing:for_basic]</a> t e k s t

</div>

Koncept "skupa vrijednosti po kojem se može prebirati" vrlo je važan pa
ima i vlastitu terminologiju. Prebiranje po nekom skupu vrijednosti
često nazivamo *iteracija* (eng. *iteration*), a vrsta vrijednosti po
kojoj se može prebirati je *iterabilna* (eng. *iterable*) vrsta
vrijednosti. Petlja `for` se "izvrti određen broj krugova" pa završi.
Jedan "krug" nazivamo jednom iteracijom. Iteracija kao proces je, dakle
proces prebiranja, a jedna iteracija je individualno izvršavanje naredbi
koje se ponavljaju. Jednu iteraciju unutar petlje često nazivamo i
korakom eng. *step* petlje.

O finijim detaljima spomenutog će biti riječ kasnije kada dođemo do
struktura podataka, ali terminologiju vrijedi znati i ranije jer se
često koristi u Python dokumentaciji i literaturi kao i u samom Python
jeziku prilikom, na primjer, javljanja pogrešaka.

<div class="important">

Iteracija Kada po nečemu iteriramo, tada po tome prebiremo jedan po
jedan element. Kada je nešto iterabilno tada se po tome može prebirati.
Ove riječi se često koriste u kôdu. Metode čiji naziv počinje s
prefiksom "iter" vraćaju rezultatu po kojem se može iterirati. Kada
Python javi grešku da nešto nije "iterabilno" tada pokušavamo prebirati
po vrsti vrijednosti koja se ne može raščlaniti na sastavne elemente.

</div>

U primjeru <a href="#listing:for_basic" data-reference-type="ref"
data-reference="listing:for_basic">[listing:for_basic]</a> smo vidjeli
kako možemo raditi sa svakim znakom u nekom tekstu odnosno sa svakim
elementom u nekom skupu vrijednosti. U retku `for znak in tekst:`,
`tekst` je skup vrijednosti po kojem se prebire, a `znak` je proizvoljan
naziv varijable koji unutar petlje možemo koristiti kako bi se
referirali na element u "ovoj iteraciji". U prvoj iteraciji, varijabla
`znak` je jednaka vrijednosti `"t"`. U drugoj iteraciji, jednaka je
vrijednosti `"e"` i tako dalje.

Što ukoliko samo želimo ponoviti neku radnju određen broj puta nevezano
za neki već postojeći skup vrijednosti poput vrijednosti `"tekst"`? Za
ovo nam je korisna funkcija `range` koja stvara niz brojeva od nekog
minimuma do nekog maksimuma. Ova funkcija je korisnija no što se na prvi
pogled možda čini pa ćemo je često susretati. Na primjer, često se
koristi u kombinaciji s petljom `for` kako bi odredila koliko puta će se
naredbe unutar petlje ponoviti. Pogledajmo primjer:

<div class="pythonp">

<a href="#listing:for_range" data-reference-type="ref"
data-reference="listing:for_range">[listing:for_range]</a> 0 tekst 1
tekst 2 tekst 3 tekst 4 tekst

</div>

Kao što vidimo, kada funkciji `range` pošaljemo jedan broj, ona stvara
niz brojeva od nule do poslanog broja, ne uključujući i taj broj. Ovdje
smo to iskoristili da bismo ponovili radnju 5 puta. Kako bi bilo jasnije
što se zbiva, ispisali smo i vrijednost varijable `i` svaki put, ali
varijablu `i` uopće ne moramo koristiti unutar petlje ako nam nije
potrebna.

### Dok se uvjet ne zadovolji

Druga vrsta petlje u Pythonu je petlja `while` koja je također često
vrlo korisna. Ova petlja ne prebire po nečemu već se izvršava sve dok
neki uvjet nije zadovoljen. Njome možemo izvesti isto što i u prošlom
primjeru:

<div class="pythonp">

<a href="#listing:while_basic" data-reference-type="ref"
data-reference="listing:while_basic">[listing:while_basic]</a> 0 tekst 1
tekst 2 tekst 3 tekst 4 tekst

</div>

Primjer <a href="#listing:for_basic" data-reference-type="ref"
data-reference="listing:for_basic">[listing:for_basic]</a> također
možemo postići ovom petljom, ali nešto zaobilaznijim putem:

<div class="pythonp">

<a href="#listing:while_index" data-reference-type="ref"
data-reference="listing:while_index">[listing:while_index]</a> t e k s t

</div>

U prikazanim primjerima svejedno je da li koristimo petlju `for` ili
petlju `while`, ali petlja `while` zahtijeva nešto više komponenata.
Također, ova petlja krije jednu opasnost koja se u `for` petlji može
teško dogoditi: lako je moguće da se `while` petlja krene izvršavati
zauvijek! Idući primjer prikazuje ovakvu grešku i ako ga pokrenete
pripremite se da će te morati nasilno ugasiti Python, jer se ovaj
program neće nikad završiti.

U prošlom primjeru je greškom ispuštena naredba `i += 1` pa se uvjet za
završetak ponavljanja kôda nikad neće zadovoljiti. Naredba
`print("nema kraja")` će se stoga pokušati izvrtiti beskonačan broj
puta. Izvršavanje ovog programa će završiti tek kad ga nasilno ugasimo
tako što smo prekinuli sistemski proces ili ugasili računalo.

Prikazana beskonačna petlja je rezultat greške i njezino ponašanje je
nepoželjno. Ipak, postoje situacije u kojem su beskonačne petlje zapravo
vrlo korisne i puno ih je lakše postići petljom `while` no petljom
`for`. Tipičan primjer su aplikacije koje kad se pokrenu čekaju
korisničke naredbe koje zatim izvršavaju na zahtjev. Navedeno stoji za
gotovo sve aplikacije s grafičkim sučeljem. U ovom slučaju, petlja se
nikad neće sama po sebi završiti, ali postoji mehanizam koji ju u
posebnim slučajevima može prekinuti. Pogledajmo prvo kako funkcioniraju
mehanizmi za prekidanje petlje, a konkretni primjeri korištenja `while`
petlji u ovom smislu su preneseni kasnije u tekstu.

Postoje dvije jednostavne Python izjave koje služe upravljanju petljama
i koje se smiju koristiti samo unutar petlji. Te izjave su `break`, koja
služi prekidanju petlje i `continue`, koja služi prelasku na idući korak
petlje.

### Prekini petlju

Jednostavna izjava `break` čim se izvrši završava petlju u kojoj se
nalazi. Ova izjava se koristi kada je potrebno izaći iz petlje prije no
što bi ona završila sama po sebi.

<div class="pythonp">

<a href="#listing:for_break" data-reference-type="ref"
data-reference="listing:for_break">[listing:for_break]</a> n e k i

</div>

Izjava "prekini petlju", odnosno `break`, je nužna u prije spomenutim
beskonačnim `while` petljama. Pogledajmo praktičan primjer:

Izvrši ovaj program. Kako se ponaša? Ne radi ništa korisno, ali je
program koji se ponaša bliže računalnim aplikacijama. Naš "prvi program"
odnosno primjer <a href="#kviz" data-reference-type="ref"
data-reference="kviz">[kviz]</a> se mogao izvršiti samo jednom i onda je
izašao. Prikazani mehanizam omogućuje da se program nastavlja, odnosno
ponavlja, sve dok korisnik ne odluči prestati raditi s njim.

Jedna zanimljivost kod prekida petlje u Pythonu je što petlja `for`
podržava i komponentu `else` koja se izvršava samo ako petlja nije
prekinuta s naredbom `break`. Ova mogućnost je često korisna prilikom
pretraživanja. Pogledajmo primjer koji provjerava da li se u nekom
tekstu nalazi traženo slovo:

<div class="pythonp">

<a href="#listing:for_else" data-reference-type="ref"
data-reference="listing:for_else">[listing:for_else]</a> kada je slovo
pronađeno Unesi neki tekst: riba ribi grize rep Unesi slovo koje se
traži: a Slovo "a" JE pronađeno!

</div>

<div class="pythonp">

<a href="#listing:for_else" data-reference-type="ref"
data-reference="listing:for_else">[listing:for_else]</a> kada slovo nije
pronađeno Unesi neki tekst: riba ribi grize rep Unesi slovo koje se
traži: x Slovo "x" NIJE pronađeno!

</div>

Za vježbu pokušajte izvesti prijašnji program bez da koristite
komponentu `else` petlje `for`!

### Preskoči korak u petlji

Jednostavna izjava `continue` čim se izvrši prelazi na idući korak
petlje u kojoj se nalazi. Ova izjava se koristi kada je potrebno
preskočiti korak u petlji.

<div class="pythonp">

<a href="#listing:for_continue" data-reference-type="ref"
data-reference="listing:for_continue">[listing:for_continue]</a> n k t k
s t

</div>

Na prikazani način možemo izvršiti petlju koja se izvršava za određen
broj slučajeva, ali se preskaču slučajevi koji (ne) zadovoljavaju
određene uvjete.

Pogledajmo još pobliže u pogreške i upravljanje njima pa se možemo
baciti i na konkretnije programe.

## Pogreške i pokušaji

Javljanje pogrešaka je normalna stvar u programiranju, a kod programskih
jezika viših razina se pokušava čim jasnije korisniku dati do znanja što
je i gdje je pošlo po krivu. Python omogućava i presretanje pogrešaka
što nam pruža nove mogućnosti za kontrolu toka programa. Pogledajmo prvo
pobliže Python pogreške, a zatim i kako ih presretati.

Što se dogodi kad Python prilikom izvršavanja kôda naiđe na pogrešku?
Recimo da smo pokušali izvršiti izraz `n + 1`, a varijabli `n` nije
pridružena vrijednost.

Usredotočimo se na zadnju liniju. Python javlja `NameError` s
`name 'n' is not defined` kao detaljima pogreške. U trenutku kad je
naišao na pogrešku Python je stvorio objekt vrste `Exception` (u ovom
slučaju `NameError`) s nekom porukom. Zatim je prijavio grešku opisanu
tim objektom korisniku te prekinuo izvršavanje. Sve linije prije zadnje
su ispis koda u kojemu se dogodila greška. Ovaj dio može biti vrlo
dugačak, ali važno je zapamtiti da nam je za opis greške najvažnija
zadnja linija i u mnogim slučajevima je dovoljno pročitati samo nju uz
informacije u kojoj se točno liniji kôda javlja pogreška. Ispis ranijeg
kôda služi lakšem pronalaženju greške u vlastitom ili tuđem kôdu i
posebno je koristan kod većih programa.

Također, postoji više vrsta grešaka koje je najlakše pronaći u
interaktivnom radu:

Dapače, ukoliko prilikom učenja Pythona ne vidite često kojekakve
pogreške, šanse su da trebate promijeniti pristup! Upravo prikazana
greška pojednostavljeno kaže "Greška u vrsti podataka: brojevi i tekst
se ne mogu zbrajati".

Najčešće pogreške koje Python javlja su:

- **SyntaxError** - javlja se kada kôd nije dobro formiran; najčešće
  pogreške ovog tipa su neujednačene zagrade ili navodnici, manjak
  zareza ili dvotočki na mjestima na kojima se moraju pojavljivati i
  slično

- **NameError** - javlja se kada koristimo neki naziv čija vrijednost
  nije poznata; na primjer pokušavamo koristiti varijablu `x` prije no
  što smo toj varijabli pridružili neku vrijednost

- **TypeError** - javlja se kada se operacija ili funkcija pokuša
  provesti s krivom vrstom vrijednosti; na primjer `"1" + 1` ili
  `round("tekst")`

- **ValueError** - javlja se kada se operacija ili funkcija pokuša
  provesti s točnom vrstom vrijednosti, ali s vrijednosti s kojom nije
  moguće provesti tu operaciju ili funkciju; na primjer `math.sqrt(-1)`

- **ImportError** - javlja se kada korisnik pokuša uvesti modul koji ne
  postoji (ili ga Python ne zna pronaći, što dođe na isto); na primjer
  **import nisamtu** (pod uvjetom da niste sami napisali Python modul
  koji se zove "nisamtu")

- **IndexError** - javlja se kada pokušamo dohvatiti element popisa koji
  nije prisutan; na primjer osmi znak iz stringa koji se sastoji od
  sedam znakova

- **KeyError** - javlja se kada pokušamo dohvatiti element rječnika koji
  nije prisutan; na primjer element pod nazivom "title" iz rječnika koji
  ne sadrži takav ključ[^2]

Kroz iskustvo rada u Pythonu, postaje sve lakše identificirati probleme
kroz vrste pogreški koje Python javlja. Uz to, kroz presretanje
pogrešaka možemo upravljati pogreškama u programiranju što je katkad
korisno. Ipak, dok su kondicionali i petlje standardan i prihvaćen dio
kontrole toka u programskim jezicima, presretanje pogrešaka nije do te
mjere. Ipak, može biti vrlo korisno i to pogotovo u slučaju kada želimo
presresti korisničke greške kako bi mu javili jasnije poruke i
spriječili "rušenje" programa. Na primjer, sljedeći program računa i
ispisuje drugi korijen iz unesenog broja.

Kada pokrenemo program i upišemo broj "2", program će ispisati:

<div class="pythonp">

<a href="#listing:pogreske_input_raw" data-reference-type="ref"
data-reference="listing:pogreske_input_raw">[listing:pogreske_input_raw]</a>
Program je započeo s radom.

Unesi broj: 9 Drugi korijen: 3.0

Pritisni \<enter\> za kraj

</div>

Prikazani program jednostavno računa drugi korijen iz korisničkog unosa.
Ali što ako korisnik unese nešto što se ne može interpretirati kao broj
ili unese negativan broj? Evo kako bi izgledao loš unos kada bismo ovaj
program pokrenuli u IDLE-u ili u komandnoj liniji.

<div class="pythonp">

<a href="#listing:pogreske_input_raw" data-reference-type="ref"
data-reference="listing:pogreske_input_raw">[listing:pogreske_input_raw]</a>
Program je započeo s radom.

Unesi broj: neću

Traceback (most recent call last): File "C:/code/try_except_a.py", line
7, in \<module\> broj = int(broj) ValueError: invalid literal for int()
with base 10: ’neću’

</div>

U prikazanom slučaju vidimo "sirovu" grešku koju je javio Python.
Međutim, da smo ovaj program pokrenuli duplim klikom, program bi
jednostavno završio prije no što korisnik može pročitati poruku o
grešci! Iz korisniče perspektive "program se srušio". U svakom slučaju,
što želimo postići je: 1) da korisnik uvijek vidi grešku koja se
dogodila i 2) da se korisniku ne prikazuje sirova greška kako ju javlja
programski jezik, već neka poruka specifično namijenjena za naš program.
Kako bismo postigli ovo, Python nam omogućuje korištenje riječi `try`.
Pogledajmo primjer:

Kada izvršimo program vidjet ćemo da se on ne gasi "sam od sebe"
prilikom pogreške, a povratna informacija korisniku nije više interna
poruka od programskog jezika već nešto dizajnirano za ovu specifičnu
namjenu.

<div class="pythonp">

<a href="#listing:pogreske_input_try" data-reference-type="ref"
data-reference="listing:pogreske_input_try">[listing:pogreske_input_try]</a>
Program je započeo s radom.

Unesi broj: neću Iz vrijednosti "neću" nije moguće izračunati drugi
korijen.

Pritisni \<enter\> za kraj

</div>

Slično se ponaša i kada unesemo negativan broj.

<div class="pythonp">

<a href="#listing:pogreske_input_try" data-reference-type="ref"
data-reference="listing:pogreske_input_try">[listing:pogreske_input_try]</a>
Program je započeo s radom.

Unesi broj: -1 Iz vrijednosti "-1" nije moguće izračunati drugi korijen.

Pritisni \<enter\> za kraj

</div>

Ovaj primjer demonstrira korištenje naredbe `try` u praksi.
Najjednostavnije korištenje ove naredbe može se sažeti na sljedeći
način:

<div class="pythonp">

Najjednostavniji oblik pokušajalisting:pokusaj_1 try: \<naredbe koje će
se pokušati izvršiti\> except VrstaGreške: \<ako se dogodi bilo kakva
greška u kôdu napisanom pod try, izvršiti će se kôd napisan ovdje\>

</div>

`except` dio može i ne mora primiti neku vrstu pogreške (poput
ValueError). Ako ne napišemo niti jednu vrstu pogreške tada će se kôd
pod `except` izvršiti u slučaju bilo koje greške. Ako pak specificiramo
neku vrstu greške, kao u primjeru
<a href="#listing:pogreske_input_try" data-reference-type="ref"
data-reference="listing:pogreske_input_try">[listing:pogreske_input_try]</a>,
tada će se kôd napisan pod `except` izvršiti samo u slučaju te vrste
greške. Ne specificirati vrstu greške je dopušteno, ali se u načelu
smatra lošom praksom jer na taj način naredba `try` može "sakriti"
greške za koje nismo pretpostavili da se mogu dogoditi što znatno
otežava traženje problema u programima. Zato je dijelu `except` dobro
specificirati točno koje vrste pogreške hvata. Ako želimo hvatati više
vrsta pogrešaka, možemo ponoviti `except` komponentu naredbe `try`. Kao
što smo vidjeli, ovoj naredbi je moguće dodati i `else` komponentu koja
služi odvajanju kôda koji će se izvršiti samo ako su naredbe u `try`
komponenti uspješno provedene, odnosno suprotan slučaj od onog u kojem
se izvršava `except` dio kôda. Zadnja komponenta naredbe `try` je
komponenta `finally`. Naredbe napisane u ovom dijelu će se uvijek
izvršiti bez obzira da li je kôd pod `try` prouzročio grešku ili ne.

<div class="pythonp">

Širi oblik pokušajalisting:pokusaj_2 try: \<naredbe koje će se pokušati
izvršiti\> except VrstaGreške1: \<ako se dogodi greška vrste
VrstaGreške1 u kôdu napisanom pod try, izvršiti će se kôd napisan
ovdje\> ... except VrstaGreške2: \<ako se dogodi greška vrste
VrstaGreške2 u kôdu napisanom pod try, izvršiti će se kôd napisan
ovdje\> else: \<naredbe koje se izvršavaju samo ako je kôd napisan pod
try uspješno izvršen\> finally: \<naredbe koje se uvijek izvršavaju, bez
obzira da li je došlo do greške ili ne\>

</div>

Ipak, potpuno raspisanu `try` naredbu se rijetko vidi i dapače, primjer
koji prikazuje sve ove komponente u praksi bi bio ili vrlo
specijaliziran ili umjetno osmišljen samo kako bi postojao takav
primjer. Također, neke situacije u kojima se tipično koristila
komponenta `finally` je Python 3 riješio na bolji način. U daleko
najčešćem slučaju, naredba `try` će koristiti samo jednu `except`
komponentu i potencijalno `else` komponentu kao u primjeru
<a href="#listing:pogreske_input_try" data-reference-type="ref"
data-reference="listing:pogreske_input_try">[listing:pogreske_input_try]</a>.

Kao što vidimo, složena izjava `try` ima dosta naprednih mogućnosti.
Ipak, ovaj mehanizam se koristi znatno manje nego kondicionali i petlje.
Dapače, ukoliko je nešto moguće izvesti s izjavom `try`, ali i s
kondicionalima i/ili petljama, kao općenito pravilo se izbjegava `try`
jer za razliku od kondicionala i petlja ima više sitnica na koje treba
paziti i detalja koji mogu poći po krivu.

## Korištenje više mehanizama kontrole toka

Proučimo sljedeći jednostavan primjer:

Iako korisniku javljamo `'Unesi broj: '`, ništa ga ne sprječava da unese
tekst ili bilo što drugo što se ne može interpretirati kao broj. Česta
greška na hrvatskim tipkovnicama je, na primjer, unos "7ž" gdje je slovo
"ž" slučajno utipkano radi smještaja uz tipku enter, a na nekim
tipkovnicama čak i zauzima dio te tipke. Ako se ovo dogodi, program će
se srušiti jer će redak `n = int(n)` javiti grešku i komandna linija će
se odmah ugasiti. Kako bismo spriječili takvo ponašanje i korisniku
javili grešku možemo koristiti izjavu `try`.

Sada smo presreli pogrešku i prikazali korisniku odgovarajuću poruku.
Ipak, nakon pogreške moramo prekinuti izvršavati program jer bi
hipotetski ostatak programa očekivao da je n broj. Kako bismo ovo
spojili s petljom `while` da korisniku ponavljamo pitanje sve dok ne
unese cijeli broj?

<div class="pythonp">

<a href="#listing:input_number_try_while" data-reference-type="ref"
data-reference="listing:input_number_try_while">[listing:input_number_try_while]</a>
Unesi broj: neću neću se ne može interpretirati kao cijeli broj, pokušaj
ponovo. Unesi broj: 17ž 17ž se ne može interpretirati kao cijeli broj,
pokušaj ponovo. Unesi broj: 17

</div>

Prikazani mehanizam možemo koristiti kada želimo osigurati unos cijelog
broja i ponavljati pitanje korisniku sve dok ne unese validan broj. Sada
znamo dovoljno o mehanizmima kontrole toka kako bismo ih iskoristili u
konkretnijim primjerima.

[^1]: U mnogim drugim jezicima se petlja `for` ponaša drugačije, a
    petlja o kojoj je sada riječ se naziva `foreach`, `for_each` ili što
    slično.

[^2]: Rječnici su prikazani kasnije u tekstu.
