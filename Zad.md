\\section{Rad s tekstom u Pythonu}

Digitalan tekst je dakle niz znakova i uz brojeve je najčešća vrsta
vrijednosti. Kada razmislimo, niz znakova nije jednostavna vrsta
vrijednosti jer se može raščlaniti na sastavne dijelove odnosno
znakove\\footnote{Dapače, neki jezici razlikuju vrstu podataka "znak"
(\\textit{char}) od vrste podataka "niz znakova" odnosno
\\textit{string}.}. Ipak, kad radimo s tekstom vrlo često ga promatramo
kao vrijednost koja može sadržavati nula ili više znakova. Tekst od nula
znakova se naziva "praznim tekstom" (eng. \\textit{empty string}) i na
neki način odgovara konceptu nule kod brojeva.

U Pythonu se tekst čuva kroz vrstu podataka
\\mintinline{python}{str}\\index{vrsta podataka!str}, što je skraćeno od
engleske riječi \\textit{string} odnosno \\textquotedblleft
niska\\textquotedblright{}. Svaka vrijednost koja je zapisana pod
navodnicima se smatra tekstom. Ovo je vrlo važno zapamtiti jer vrijedi
za mnoge računalne tehnologije: ako je nešto pod navodnicima, to se
smatra točno tim tekstualnim znakovima i ne stoji za nešto drugo. Jedina
razlika među tehnologijama je koji se navodnici dopuštaju za označavanje
teksta, a Python i mnogi suvremeni jezici dopuštaju korištenje bilo
apostrofa ili navodnika i korištenje oba znaka ima isto značenje. Koje
znakove ćemo koristiti za označavanje teksta, najviše ovisi o tome da li
sam tekstovni niz već sadrži apostrofe ili navodnike. Ovo je
najjednostavnije objasniti primjerima:

\\begin{python}{Tekst u Pythonu}{listing:tekst1}\
\>\>\> tekst = "ovo je u navodnicima pa se smatra tekstom"\
\>\>\> tekst = 'ovo je u apostrofima pa se isto smatra tekstom'\
\>\>\> tekst = "ako je ' u tekstu moramo koristiti navodnike"\
\>\>\> tekst = 'ako je " u tekstu koristi apostrofe'\
\>\>\> tekst = "ovaj "tekst" nije validno zapisan"\
SyntaxError: invalid syntax\
\\end{python}

U primjeru gore su prikazani najčešći načini zapisivanja teksta u Python
kôdu. U ovom slučaju, samo zadnji redak nije valjan jer koristi iste
navodnike unutar teksta kao i za obilježavanje teksta. U sljedećem
primjeru su prikazane neke početničke greške koje su katkad teško
uočljive.

\\begin{python}{Česte pogreške s tekstom}{listing:tekst2}\
\>\>\> tekst = "ovo je string"\
\>\>\> print(tekst) \# ispiši vrijednost varijable tekst\
ovo je string\
\>\>\> print("tekst") \# ispiši tekst "tekst", a ne vrijednost varijable
tekst\
tekst\
\>\>\> ovo_nije_broj = "1" \# pažnja: navodnici!\
\>\>\> print(ovo_nije_broj)\
1 \# na ekranu izgleda kao broj\
\>\>\> ovo_nije_broj + 1 \# ali zapravo nije broj nego tekst\
Traceback (most recent call last):\
File "\<pyshell#33\>", line 1, in `<module>`{=html}\
ovo_nije_broj + 1\
TypeError: Can't convert 'int' object to str implicitly\
\\end{python}

Svaki niz znakova u Python kôdu, kao i općenito u računalnim
tehnologijama, koji je omeđen navodnicima smatra se tekstom odnosno
točno tim slijedom znakova koji ne stoje za nešto drugo. Na primjer,
\\mintinline{python}{print(tekst)} će ispisati vrijednost pridruženu
varijabli \\mintinline{python}{tekst} ili javiti grešku ako varijabla
tekst nije definirana, a \\mintinline{python}{print('tekst')}
jednostavno ispisuje tekst \\mintinline{python}{"tekst"}. Također,
vrijednost \\mintinline{python}{'1'} se smatra tekstom, a ne brojem, jer
je pod navodnicima. Zbrajanje ove vrijednosti s brojem javlja grešku jer
se pokušavaju zbrojiti tekst i broj što nije definirana radnja. Drugim
riječima, računalu je ovo kao da smo mu zadali operaciju "broj 1 + znak
a" koja nije definirana među ovim vrstama vrijednosti.

\% TODO jesmo li se se sada prvi put sreli s pogreškom?

Sada smo se i prvi put formalno sreli s pogreškom. Prilikom
programiranja to je posve normalno i tko god da programira proizvodi i
pogreške. Ako do sada niste vidjeli ni jednu, šanse su da niste
eksperimentirali s vlastitim kôdom. Kako jezik prijavljuje pogreške i
kako možemo time upravljati će biti prikazano u zasebnom poglavlju, ali
recimo za sada da je prilikom javljanja pogreške najvažnije pročitati
zadnju liniju jer je upravo ta linija krajnja poruka korisniku što se
zapravo dogodilo. U primjeru ranije to je
\\mintinline{python}{TypeError: Can't convert 'int' object to str
implicitly} što možemo prevesti kao "Greška u vrsti vrijednosti: int se
ne može implicitno pretvoriti u str". Drugim riječima,
\\mintinline{python}{int} vrijednost moramo prvo eksplicitno pretvoriti
u tekst ako ju želimo spajati s tekstom jer radnja koja se provodi putem
operatora \\mintinline{python}{+} nije definirana između vrsti
vrijednosti \\mintinline{python}{int} i \\mintinline{python}{str}.
Linije prije zadnje su početnicima manje važne, često ih ima znatno više
no u ovom primjeru i služe pronalaženju gdje se greška dogodila u kôdu
što je posebno korisno kod većih programa.

Primijetimo također da je prikazan način označavanja teksta primjeren za
kraće tekstove u jednom retku. Što ukoliko želimo definirati tekst koji
se sastoji od više redaka? Osim označavanja teksta jednostrukim
navodnicima ili apostrofima, tekst je moguće označiti i s trostrukim
navodnicima odnosno trostrukim apostrofima. Trik kod ovog načina
označavanja teksta je upravo da između trostrukih znakova možemo
normalno pisati prijelome retka, prazne linije i koristiti navodnike
kako hoćemo. Pogledajmo primjer:

\\begin{python}{Slobodan unos dužeg teksta}{listing:tekst3}\
dugi_tekst = """\
Ovdje možemo pisati tekst\
koji može normalno prelaziti u druge retke,

ostavljati prazne retke,\
koristiti "duple navodnike" i 'apostrofe' unutar teksta

jednostavno uvlačiti tekst\
i slično!\
"""\
\\end{python}

Jedini tekst koji ne smijemo koristiti u prošlom primjeru su tri
navodnika jedan za drugim. Da smo baš morali iskoristiti tri uzastopna
navodnika u tekstu, mogli smo iskoristiti trostruke apostrofe umjesto
trostrukih navodnika. U tom slučaju, naravno, ne bi smjeli koristiti tri
uzastupna navodnika, ali ovo su vrlo rijetki slučajevi.

Vrijedi spomenuti da je Python 3 orijentiran na Unicode tekst (odnosno
vrsta vrijednosti \\textit{str} podržava znakove iz svih jezika
uključujući i, na primjer, kinesko pismo i ćirilicu), a ne samo ASCII
znakove (odnosno uglavnom znakove iz engleskog govornog
područja)\\footnote{Pažnja, ovo vrijedi za Python 3 ne i za Python 2.}.
Što se naših posebnih slova tiče, u sljedećem primjeru vidimo da ih
možemo koristiti bez posebnih koncepata:

\\begin{python}{Hrvatska slova i drugi znakovi}{listing:tekst4}\
\>\>\> tekst = "Python 3 radi bez problema s čžšćđ"\
\>\>\> print(tekst)\
python radi bez problema s čžšćđ\
\\end{python}

Isto vrijedi i za druga pisma poput ćirilice ili kineskog pisma.

Za razliku od brojeva, najosnovnije radnje s tekstom se provode putem
\\textit{metoda}, a ne putem \\textit{operatora}. Metoda je funkcija
koja je vezana uz neku određenu vrstu vrijednosti jer radi samo s tom
vrstom vrijednosti. Razlika između metode i funkcije je što se metoda
uvijek koristi nakon točke te prima vrijednost prije točke kao prvi
implicitan parametar. Korištenje metoda je zapravo vrlo intuitivno pa
pogledajmo prvo primjere koji prikazuju najčešće radnje s tekstom.

\\subsection{Posebni znakovi i izbjegavanje posebnog značenja određenih
znakova}

\% TODO

\\subsection{Česte radnje s tekstom}\
\\subsubsection{Dohvat dijelova teksta}

Tekst je zapravo niz znakova te iz tog niza možemo dohvatiti
individualne znakove kao i djelove teksta. To činimo koristeći se
pozicijom, odnosno indeksima, individualnih znakova i uglatim zagradama.
Pogledajmo primjer:

\\begin{python}{Dohvat dijelova teksta}{listing:tekst_indeksiranje}\
\>\>\> tekst = "Monty Python i značenje života."\
\>\>\> tekst\[0\] \# dohvati prvi znak\
'M'\
\>\>\> tekst\[1\] \# dohvati drugi znak\
'o'\
\>\>\> tekst\[0:5\] \# dohvati znakove 0, 1, 2, 3, 4\
'Monty'\
\>\>\> tekst\[6:12\] \# dohvati znakove 6, 7, 8, 9, 10, 11\
'Python'\
\>\>\> tekst\[--1\] \# dohvati zadnji znak\
'.'\
\>\>\> tekst\[--2\] \# dohvati predzadnji znak\
'a'\
\# dohvati od prvog znaka pa sve dok se ne pojavi znak y prvi put\
\>\>\> tekst\[0:tekst.find('y')\]\
'Mont'\
\\end{python}

Kao što vidimo dijelove tekstualnog niza možemo dohvatiti tako što nakon
tekstualne vrijednosti (odnosno varijable koja se na takvu vrijednost
referira) pišemo uglate zagrade u kojima se možemo koristiti pozicijama
znakova u tekstu. Prvi znak se smatra da je na poziciji 0. Ovo može
djelovati nelogično, ali na taj način neke stvari jednostavno "klikću"
bez da se mora dodavati ili oduzimati 1. Obzirom da je ovaj mehanizam
općenitiji od korištenja za dohvat dijelova stringova, imati ćemo
prilike dobiti dojam o svemu ovome još kasnije.

Ukoliko želimo dohvatiti raspon znakova tada u uglate zagrade pišemo
raspon indeksa gdje prvi i zadnji razdvajamo dvotočkom. Kod raspona
indeksa je pravilo da se prvi uvijek uključuje, a zadnji ne. Rješenje da
je prvi indeks 0 te da se kod raspona zadnji indeks ne uključuje je
dosta često u programskim jezicima.

Indeksima možemo brojati i unazad. --1 znači zadnji znak, --2 predzadnji
i tako dalje. Ovo je zgodna mogućnost jer kada nešto želimo dohvatiti s
kraja teksta, na ovaj način ne moramo znati koliko je tekst dugačak.

Također, neke metode stringova, poput metode
\\mintinline{python}{str.find}, vraćaju indekse kao rezultat pa su vrlo
korisne u ovom smislu.

Vrijedi i spomenuti da je dohvat nekog dijela vrijednosti (kod vrsta
vrijednosti koje to podržavaju) putem uglatih zagrada standardan način
"adresiranja" dijelova neke vrijednosti pa ćemo se s ovom mogućnošću još
više puta sresti kroz ovaj tekst i, kao što ćemo vidjeti kod struktura
podataka, riječ je o vrlo važnom konceptu.

\\subsubsection{Promjena veličine slova}

Vrlo česta radnja s tekstom je promjena iz velikih slova u mala i
obratno. Pogledajmo koje mogućnosti nam dopušta sama vrsta
\\textit{str}:

\\begin{python}{Promjena veličine slova}{listing:tekst5}\
\>\>\> tekst = "cvrči CVRČI 10-ak cvrčaka"\
\>\>\> tekst.lower() \# pretvori sva slova u mala slova\
'cvrči cvrči 10-ak cvrčaka'\
\>\>\> tekst.upper() \# pretvori sva slova u velika slova\
'CVRČI CVRČI 10-AK CVRČAKA'\
\>\>\> tekst.capitalize() \# pretvori prvo slovo u veliko, a ostala u
mala\
'Cvrči cvrči 10-ak cvrčaka'\
\>\>\> tekst.title() \# pretvori prvo slovo svake riječi u veliko, a
ostala u mala\
'Cvrči Cvrči 10-Ak Cvrčaka'\
\>\>\> tekst.swapcase() \# velika slova u mala, a mala u velika\
'CVRČI cvrči 10-AK CVRČAKA'\
\\end{python}

Kao što vidimo, postoji više metoda za promjenu veličine slova i iz
samih naziva kao i prethodnog primjera je poprilično jasno što rade. Sve
ove metode ignoriraju sve znakove u tekstu za koje "promjena veličine"
nema smisla, poput brojeva i interpunkcije.

Što se samih metoda tiče, glavna razlika od funkcije je što metode
hijerarhijski pripadaju određenim vrstama vrijednosti i što implicitno
primaju vrijednost prije točke kao prvi parametar. Kada izvršimo
\\mintinline{python}(tekst.upper()) to je isto kao da smo izvršili
nepostojeću funkciju \\mintinline{python}(upper(tekst)). Razlog
postojanju metoda je organizacija kôda. Na ovaj način, metoda
\\mintinline{python}{upper} je svrstana pod vrstu vrijednosti
\\mintinline{python}{str} što je i jedina vrsta vrijednosti s kojom ova
metoda može raditi. Kada bi \\mintinline{python}{upper} bila funkcija,
imali bi jako velik broj funkcija i za svaku bi morali pamtiti na koju
vrstu vrijednosti se odnos. Na ovaj način se izbjegao taj problem jer su
metode koje rade s određenom vrstom vrijednosti hijerarhijski
organizirane pod tu vrstu vrijednosti.

\% TODO how not to be case sensitive

\\subsubsection{Micanje znakova s početka i kraja teksta}

Vrlo česta radnja kod pripreme teksta (posebno iz korisničkog unosa) je
micanje znakova s početka (lijeve strane) teksta i/ili kraja (desne
strane) teksta, ali ne i iz sredine. Najčešći slučaj u ovom kontekstu je
brisanje praznog prostora. Pogledajmo primjer:

\\begin{python}{Izbacivanje praznog prostora s početka i kraja
teksta}{listing:tekst6}\
\>\>\> tekst = ' korisnički unos '\
\>\>\> tekst.lstrip() \# left strip, ukloni prazan prostor s početka\
'korisnički unos '\
\>\>\> tekst.rstrip() \# right strip, ukloni prazan prostor s kraja\
' korisnički unos'\
\>\>\> tekst.strip() \# strip, ukloni prazan prostor s obje strane\
'korisnički unos'\
\\end{python}

Metode \\mintinline{python}{lstrip}, \\mintinline{python}{rstrip} i
\\mintinline{python}{strip} pozvane bez parametara, dakle, miču
\\textit{prazan prostor} s lijeve, desne ili obje strane teksta. Prazan
prostor sačinjavaju različite vrste razmaka (ukjučujući, na primjer,
tabulator i tzv. razmak bez rastavljanja) i znakova za prijelom retka.
Ovakvi znakovi se često neželjeno nađu u tekstu koji je došao iz
korisničkog ručnog unosa, bilo radi pogrešnog unosa ili radi
\\textit{copy/pasteanja}. Budući da su ovi znakovi nevidljivi, korisnici
ih često ne primijete tako da u mnogim programima čim radimo s
korisničkim unosom preventivno uklanjamo razmake kako isti ne bi
završili u zapisanim podacima.

Što ako želimo na ovaj način izbaciti neke druge znakove, a ne samo
razmake? Pogledajmo kako u sljedećem primjeru.

\\begin{python}{Izbacivanje znakova s početka i kraja
teksta}{listing:tekst7}\
\>\>\> tekst = '.! 2000 .!'\
\>\>\> tekst.strip('.') \# ukloni točku s početka i kraja\
'! 2000 .!'\
\>\>\> tekst.strip('.!') \# ukloni bilo koju kombinaciju točke i
uskličnika s početka i kraja\
' 2000 '\
\>\>\> tekst.strip(' .!') \# ukloni kombinacije razmaka, točke i
uskličnika s početka i kraja\
'2000'\
\\end{python}

Metoda \\mintinline{python}{strip}, dakle, prima jedan parametar koji je
niz znakova i zatim miče sve \\textit{kombinacije znakova} uključenih u
taj niz s početka i kraja teksta. Sve što vrijedi za metodu
\\mintinline{python}{strip}, vrijedi i za metode
\\mintinline{python}{lstrip} i \\mintinline{python}{rstrip}, a jedina
razlika je da li će se znakovi micati s početka, kraja ili s obje
strane.

\\subsubsection{Posebni znakovi i izbjegavanje posebnog značenja}

U radu s tekstom je često potrebno raditi s posebnim znakovima koje ne
možemo reprezentirati s nekim individualnim vidljivim znakom. Najčešći
takvi slučajevi su vjerojatno znak za novi redak i znak za tabulator.
Kako uključiti ove znakove u stringove? Pogledajmo primjer:

\\begin{python}{Novi redak i tabulator u tekstu}{listing:tekst8}\
\>\>\> tekst = 'Ovaj tekst\\nsadrži\\nprijelome redaka'\
\>\>\> print(tekst)\
Ovaj tekst\
sadrži\
prijelome redaka\
\>\>\> tekst = '\\tOvaj tekst počinje s tabulatorom'\
\>\>\> print(tekst)\
Ovaj tekst počinje s tabulatorom\
\\end{python}

Važan koncept pri radu s posebnim znakovima je korištenje znaka
\\textit{backslash}, odnosno "\\textbackslash". Ovaj znak je u ASCII
tablicu uvršten upravo radi programiranja i to zato jer se rijetko
koristi u jeziku. U suvremenim programskim jezicima ovaj znak se često
koristi kako bi označio da znak nakon njega treba tretirati posebno. U
primjeru \\ref{listing:tekst8} vidimo kako se koristi kako bi promijenio
značenje znaka "n" u "novi red" (znak koji se na engleskom zove
\\textit{newline}) i značenje znaka "t" u "tabulator". Ova dva znaka bi
nam inače bilo teško zapisati u tekst budući da se radi o tzv.
nevidljivim znakovima odnosno praznom prostoru u tekstu.

Osim navedenog, \\textit{backslash} se koristi kao takozvani
\\textit{escape character}. To znači da ga koristimo kako bi negirali
značenje nekog znaka koji bi se inače posebno tretirao. Drugim riječima,
ukoliko je znak nakon neki poseban znak, tada se njegovo posebno
značenje ignorira i tretira se kao normalan znak. Na primjer,
\\textbackslash\\textbackslash unosi znak \\textit{backslash} u tekst, a
\\textbackslash\\textquotedbl{} unosi navodnik u tekst koji neće
poremetiti normalno korištenje navodnika za označavanje teksta.

\\begin{python}{Korištenje znaka \\textbackslash za negiranje posebnog
značenja}{listing:tekst9}\
\>\>\> tekst = "Ovaj tekst sadrži \\\\, \\" i \\' bez da ti znakovi
imaju posebno značenje"\
\>\>\> print(tekst)\
Ovaj tekst sadrži \\, " i ' bez da ti znakovi imaju posebno značenje\
\\end{python}

\\subsubsection{Umetanje dijelova teksta}

Vrlo česta i važna radnja s tekstom je umetanje dinamičnih dijelova
teksta u veći statičan tekst. Ovo je nalik popunjavanju tiskanih
formulara koji umjesto nekih dijelova teksta (gdje, na primjer, treba
upisati ime i prezime) imaju prazan prostor za to koji se često
naznačuje s "\\*\\*\\*\\*\\*\\*\\*\\*\\*\\*\\*\\*". Pogledajmo primjer:

\\begin{python}{Umetanje teksta u drugi tekst 1}{listing:tekst10}\
\>\>\> tekst = ' Bi{} sam {} i {}'\
\>\>\> tekst.format('o', 'vani', 'ludo sam se zabavio!')\
'Bio sam vani i ludo sam se zabavio!'\
\>\>\> tekst.format('la', 'na predavanju', 'bilo mi je dosadno :( !')\
'Bila sam na predavanju i bilo mi je dosadno :( !'\
\\end{python}

U prikazanom primjeru, znakovi "\\{\\}" se koriste u smislu
"\\*\\*\\*\\*\\*\\*\\*\\*\\*\\*\\*\\*" u tiskanim formularima, odnosno
označavaju rezervirano mjesto gdje se dodaje tekst. Vitičaste zagrade u
tekstu služe kako bi se putem metode \\mintinline{python}{format} na
njihovo mjesto ubacilo neki tekst. U prethodnom primjeru, koristimo samo
dva rezervirana mjesta i poziv na metodu \\mintinline{python}{format}
ubacuje vrijednosti na njihovo mjesto prema redoslijedu. Ovaj slučaj je
praktičan kod kraćih tekstova, ali nije podoban kad imamo puno mjesta u
tekstu na koji želimo ubaciti vrijednosti jer ih je lako zamijeniti.
Metoda \\mintinline{python}{format} nam stoga dopušta i da imenujemo
mjesta za ubacivanje i zatim u njih ubacujemo vrijednosti prema tim
imenima. Pogledajmo primjer:

\\begin{python}{Umetanje teksta u drugi tekst 2}{listing:tekst11}\
\>\>\> tekst = """\
Bio sam u {mjesto}.

Tamo sam {radnja}. Bilo mi je {kako} jer je vrijeme u {mjesto} bilo
{vrijeme}.\
"""\
\>\>\> t = tekst.format(mjesto = 'Zadru', radnja='se kupao',
kako='sjajno', vrijeme='lijepo')\
\>\>\> print(t)

Bio sam u Zadru.

Tamo sam se kupao. Bilo mi je sjajno jer je vrijeme u Zadru bilo lijepo.

\\end{python}

\% TODO primjer pokraj "uglavnom primali jedan do dva parametra"\
U ovom primjeru pojavljuje nam se novi koncept: \\textit{imenovani
parametri funkcija} (odnosno metoda). Svi parametri koje smo do sada
koristili slali smo funkcijama prema njihovim pozicijama jer se radilo o
jednostavnim slučajevima koji su uglavnom primali jedan do dva
parametra, a u ovom slučaju šaljemo ih imenovano. Metoda
\\textit{format} prima onoliko imenovanih parametara koliko smo ih
naveli u tekstu koji se "formatira". Imena u tekstu koji se formatira
moraju, stoga, biti validna imena za Python varijable!

Prikazani način slaganja teksta možda na prvi pogled djeluje samo kao
zgodan način spajanja različitog teksta, ali u praksi je vrlo često
korisna. Na primjer, na ovaj način možemo stvarati HTML ili XML kao i
stvarati razne izvještaje o radu programa ili njegovim rezultatima.

\\subsubsection{Članstvo i zamjena}

Postoji naravno još niz radnji koje možemo provoditi nad tekstom.
Dapače, tekst je vrlo kompleksna tvorevina za čiju obradu je moguće
napisati niz knjiga ovisno o vrsti teksta, procesima koje koristimo za
njegovu obradu te našim ciljevima. Pogledajmo zato ovdje samo još neke
česte radnje s tekstom:

\\begin{python}{Druge česte radnje s tekstom}{listing:tekst_ostalo}\
\>\>\> tekst = 'Ne da mi se ovo čitati.'

1.  zamijeni sve znakove "a" sa znakom "x"\
    \>\>\> tekst.replace('a', 'x')\
    'ne dx mi se ovo čitxt'
2.  može i s duljim nizovima\
    \>\>\> tekst.replace('ne da mi se', 'želim')\
    'želim ovo čitat'

<!-- -->

1.  da li neki tekst sadrži znak ili drugi manji tekst\
    \>\>\> 'o' in tekst\
    True\
    \>\>\> 'u' in tekst\
    False\
    \>\>\> 'ovo' in tekst\
    True

<!-- -->

1.  prebroji koliko se puta pojavljuje neki tekst u duljem tekstu\
    \>\>\> tekst.count('a')\
    2
2.  pronađi poziciju na kojoj se prvi put pojavljuje neki tekst u duljem
    tekstu\
    \>\>\> tekst.find('a')\
    4\
    \\end{python}