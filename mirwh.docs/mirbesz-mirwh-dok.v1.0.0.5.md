# MirWH raktári rendszer

-----------------------------------------
## Telepítés, beállítások, bejelentkezés, főmenü

### Telepítés, beállítások

Első lépés, hogy az androidos eszközünkön csatlakozzunk arra a hálózati adapterre (wifi), amivel a Mirbesz helyi hálózatát el tudjuk érni. Az alkalmazás letöltéséhez internet elérésére is szükség lesz.

Az alkalmazást első alkalommal le kell tölteni, és telepíteni kell az eszközre. A böngészőben nyissuk meg a https://SpecSD.github.io/mirbesz címet, innen tölthető le a mindenkori aktuális alkalmazás.
A letöltött fájl egy apk, amit elindítva a program települni fog. Ehhez persze engedélyeznünk kell az ismeretlen forrásból történő telepítést. Ha pl. Chrome böngészőben töltöttük le az apk-t, és onnan indítottuk el,
akkor a Chrome alkalmazást kell hozzáadni az "Ismeretlen alkalmazások telepítése" engedélyhez.

A kézi eszközhöz kapcsolt vonalkódolvasó működtetéséhez szükség van a DataWedge programra. A Mirbesznél lévő kézi eszközökön ez alapból rajta van, nincs vele teendő. Bármilyen más android eszközre is
(legalább Android 9-es verzió legyen rajta) telepíthető, de a DataWedge hiányában a vonalkódolvasás nem fog működni.

### Verziófrissítés módszere

Egyelőre automatikus verziófrissítés nincs. Az elkészült programból egy új apk-t készítünk, amit felteszünk a https://SpecSD.github.io/mirbesz oldalra, és az új telepítéshez hasonlóan kell eljárni:
Le kell tölteni az apk-t, el kell indítani, telepítés után az új verzió fog elindulni. Az aktuális verziószám az alkalmazás bal felső sarkában folyamatosan látható, itt tudjuk ellenőrizni, hogy a legfrissebb verzió fut-e.
*Megjegyzés: Egyelőre nincs erre ellenőrzés, egy elavult verziót is el lehet indítani. Ha az elindított verzió óta csak apróbb felületi módosítások történtek, akkor ez nagyobb gondot nem okoz a munkában. Ha viszont lényegi változások történtek, akkor ez komoly hibákhoz vezethet. Ezért fontos erre odafigyelni. (A későbbiekben be fogunk vezetni erre egy ellenőrzést, csak a legaktuálisabb verziót lehet majd elindítani.)*

A program neve MirWH. Előfordul, hogy éles publikálás előtt egy teszt verziót publikálunk. Ez MirWHTeszt néven fut, telepítés után ilyen néven fogjuk megtalálni az eszközünkön. Ez külön elindítható,
és az éles adatbázis helyett egy teszt adatbázishoz csatlakozik.

### Háttérfolyamat - backend

Ahhoz, hogy a kézi eszközre telepített alkalmazás tudjon kapcsolódni az adatbázishoz, egy háttérszolgáltatásra van szükség, a backend-re. Ez a háttérszolgáltatás a helyi hálózatban egy olyan szerveren (bár technikailag
bármilyen hálózatra kapcsolt windows pc alkalmas erre) kell, hogy legyen, ami el tudja érni a Mirbesz MSSQL adatbázisát a 10.10.10.34-es szerveren. (Akár ugyanezen a szerveren is futhat.)

A c:\spc\mirwh_backend és c:\spc\mirwh_backend_teszt mappákba másoltuk ennek a háttérszolgáltatásnak a programfájljait. Ez kétféleképpen indítható:
- A mappában található MBHBackend.exe elindításával. Amíg azt külön le nem állítjuk, addig futni fog, és fogadja a bejövő kéréseket. Egy technika ennek az állandó fenntartására, hogy egy ütemezett feladatot indítunk rá
, aminek feladata x percenként ennek az újraindítása, de olyan beállítással, hogy ha már fut, akkor ne indítsa el mégegyszer. Így ha valamilyen külső ok miatt leállna, vagy a szerver újraindításánál is biztosak lehetünk benne, hogy a backend újra fog indulni.
- IIS site-ként definiáljuk ezt a szolgáltatást. A lényeg, hogy a site útvonalaként a backend mappáját kell megadni, és azon a http-s porton figyeljen, amit megbeszélünk.

Mivel ez a program az egyik porton (jelenleg ez a 4100, de másra is átállíthatjuk, ha ez nem felel meg) várja a beérkező hívásokat, ezért ezt a portot a tűzfalon át kell engedni, kívülről elérhetővé kell tenni.

A backend futásának előfeltétele a .net6 keretrendszer futtatókörnyezetének megléte. Ez a következő oldalról tölthető le: https://dotnet.microsoft.com/en-us/download/dotnet/6.0
Itt az "ASP.NET Core Runtime 6.x.x" és a ".NET Runtime 6.x.x" letöltésére és telepítésére van szükség.

### Bejelentkezés

Raktári felhasználók alapján történik. Az eddig is használt Ifsz-es funkcióval tartjuk karban. Ugyanazzal a felhasználónév / jelszóval be tudunk lépni, amivel a korábbi WinCE-s eszközökre beléptünk.

Rögtön induláskor feljön a felhasználónév jelszó bevitelére két mező, és a belépés gomb.

Bejelentkezés után a MirCE-től eltérően nem egy nyomógombos főmenü fogad, hanem az SPC-s oldalmenü, ami viszont ráfed a középső tartalomra, nem megosztja vele a képernyő területét.
A felső sor tartalma, ami mindig látható:
- Hamburgermenü ikonja, amivel előjön, vagy eltűnik az oldalmenü, benne a menüpontokkal
- A program neve. (MirWH, illetve MirWHTeszt lehet)
- A program verziószáma.
- A bejelentkezett user és egy kilépés gomb, ami visszavezet a bejelentkező képernyőre
- Egy vonalkód ikon, amire kattintva feljön egy mező, ahová kézzel beírhatunk egy vonalkódot. Ez akkor hasznos, ha nem működik, vagy nem tudjuk leolvasni scannerrel a vonalkódot.

Egy fél órányi tétlenség után a program automatikusan kilépteti magát, és visszavisz a bejelentkező képernyőre.

Ez a felső sor az, ami fix, mindenhol látszik, alatta van az aktuális menüpontnak megfelelő tartalom.
A főképernyőn ez csak egy üdvözlő képernyőt jelent, ahol a lényeges bejelentkezési adatokat láthatjuk, esetleg néhány összesítő adatot.
A menüpontok a hamburger menügombra nyomva jönnek elő, ami oldalról bekúszik, és a menüpont kiválasztása után újra eltűnik.

### Főmenü

Nyomógombok helyett oldalmenü:
- Árubeérkezés
- Betárolás
- Tárhely cikkei
- Bontásra Kom.
- Bontás
- Kiszedési jav.
- Kocsira pakol
- Leltár
- Kilép

### Vonalkódok fogadása

A felső sor jobb oldalán mindig látszik egy vonalkód ikon, arra kattintva előjön egy kis beviteli mező, oda be lehet írni bármit. A beírt szöveget a program úgy tekinti, mintha vonalkódolvasóval lőttük volna le.
Ezzel akármilyen androidos eszközön tudjuk használni az alkalmazást, illetve ez akkor is hasznos lehet, ha valami miatt nem jól olvasható a vonalkód.

Egyébként a kézi eszközre telepített DataWedge-et használja a program. Első induláskor a program létrehoz egy új profilt a DataWedge-ben "SPC-MirWH" néven. Ezt a profilt használja a program, és ezzel lesz megoldva,
hogy a vonalkódolvasón lelőtt vonalkódot tudja értelmezni az alkalmazás. (Egyelőre kézzel kell ebben a profilban átállítani a "Keystroke output" részben az Enabled értéknél ki kell venni a pipát. TODO: Ezt a programnak kellene már ennek megfelelően beállítania.)

### Billentyűzet kezelése

Amikor az alkalmazás használata során beviteli mezőbe lépünk, akkor megjelenik a képernyő billentyűzet (virtuális billentyűzet), azzal együtt a jobb alsó sarokban egy billentyűzet ikon.
Mivel az eszközünknek van hardveres billentyűzete, ami az esetek többségében jól használható (pl. számok beírása), ezért célszerű a virtuális billentyűzetet kikapcsolni, és csak olyankor visszakapcsolni, ha olyan karaktert kell beírnunk,
amit nehézkesebb lenne fizikai billentyűzettel. Ha a jobb alsó sarokban lévő billentyűzet ikonra kattintunk, akkor feljön egy ablak, amin ki-, illetve bekapcsolhatjuk a virtuális billentyűzetet.


-----------------------------------------
## Árubeérkezés

A funkció az "Árubeérkezés" menüpont kiválasztásával indítható el. Várjuk meg, amíg betölti az adatokat:
- Raktár: Gyakorlatban csak egy raktárunk van, a "KÖZPONT", mindig ezt fogja mutatni.
- Szállító: Itt jelennek meg azok a szállító üzleti partnerek, akiknek van nyitott szállítói megrendelése. (A KÖZPONT raktárban)  
  "V:" előtaggal megjelennek azok a vevők is, akikre lett rögzítve vevői visszáru tervezet az SAP Business One-ban.
  A folyamat szempontjából ezek a vevők is ugyanúgy működnek, mint a szállítók, hiszen a visszáru tervezet tételei alapján bevételezést kell végrehajtani, akárcsak a szállítói megrendeléseknél.
  A lépések ugyanazok, a különbség annyi, hogy szállító esetén a folyamat végén árubeérkezés fog létrejönni, míg vevő esetén a vevői visszáru.
  Legördülő listából választható ki a partner.
- Dátum: Az üzleti partner kiválasztása után megjelennek azok a dátumok, amelyre ennek a partnernek nyitott szállítói megrendelése (vagy vevői visszáru tervezete) van.
- Középső rész: A partner kiválasztása után itt kerülnek felsorolásra a nyitott szállítói megrendelései, visszáru tervezetei, árubeérkezés tervezetei.

### Árubeérkezés szállítói megrendelés alapján

A listában megjelennek a kiválasztott szállító nyitott megrendelései. Itt rá kell kattintanunk, ki kell jelölnünk azt a sort, amire árubeérkezést akarunk végrehajtani. Utána megnyomjuk a lenti "Árubeérkezés" gombot. (Vagy duplaklikk a sorra.)
Ezután egy új képernyőre jutunk, ahol fent megjelenik a kiválasztott szállítói megrendelés bizonylatszáma. Amennyiben már korábban el lett kezdve erre a megrendelésre egy árubeérkezés tervezet, akkor itt ennek a
tervezetnek a kódját is láthatjuk. (ABS-...)

A képernyő nagyobb területén a megrendeléshez tartozó cikkeket soroljuk fel, mindegyiknél látható, mennyi az igény, és mennyi lett már bevételezve. Közben a fizikailag beérkezett raklapra ragasztunk egy új raklap vonalkódot.
Azonosítjuk a raklapon szereplő cikket, és a listában kijelöljük az adott cikk sorát, majd
- Rálövünk a raklap vonalkódra
- Vagy dupla kattintással is megnyithatjuk

Mindkét esetben megnyílik a raklap készítő ablak, amin már ki van töltve a kiválasztott cikk. A két módszer között az a különbség, hogy az első esetben azonnnal raklap azonosítóval nyílik meg az ablak, a második esetben az
üres marad. De később bármikor beírhatjuk a raklap azonosítót, vagy lelőhetjük a vonalkódját.

A raklap készítése a "Raklap megtekintés, összeállítás" fejezetben van részletesen leírva.

Ha erről az ablakról visszatérünk, mert létrehoztuk az új raklapot, akkor már látnunk kell az összesített mennyiségek között a most hozzáadottat.

Lehetőségünk van még az "Egyéb cikk" nyomógombbal is elindítani egy raklap létrehozást. Ilyenkor viszont tetszőleges cikket kiválaszthatunk, nem csak a szállítói megrendelésen foglaltakat. (Normál jogosultsággal
csak göngyöleget lehet felvenni, különleges jogosultsággal viszont bármelyik cikket kiválaszthatjuk.)

Amíg ebben a funkcióban vagyunk, a program foglalja az kiválasztott megrendelést, és más felhasználó nem tudja megnyitni. Ha kilépünk, az eddigi munkáink nem vesznek el, de a megrendelés felszabadul - később visszatérhetünk rá,
vagy más felhasználó is befejezheti azt.

A "Befejezés" gombbal tudjuk véglegesíteni az árubeérkezést, ezzel "Tervezet" állapotba kerül a beérkezés. Ebben az állapotban már többször nem tudjuk megnyitni, módosítani a rajta lévő raklapok adatait. Ezeket az
árubeérkezéseket az SAP Business One felületén az IFSZ AddOn "Árubeérkezés tervezet" képernyőjén tudjuk véglegesíteni, amivel létrejön egy árubeérkezés a szállítói megrendelésre hivatkozva, azokkal a cikkekkel,
mennyiségekkel és sarzsokkal, amit az adatgyűjtés közben megadtunk.

### Árubeérkezés vevői visszáru tervezet alapján

A visszáru tervezet alapján történő árubeérkezés rögzítésének folyamata megegyezik a szállítói megrendelés alapján történő rögzítéssel. De itt az igényelt cikkek és mennyiségek listája nem egy szállítói megrendelésből,
hanem egy vevői visszáru tervezetből jön.

A folyamat végén az addon "Árubeérkezés tervezet" képernyőjén a véglegesítésre nem egy árubeérkezés jön létre, hanem egy vevői visszáru.

### Árubeérkezés hivatkozás nélküli

Ilyen típusú árubeérkezés létrehozására csak speciális jogosultsággal van lehetőségünk. Ha a szállítót kiválasztva a "Hiv.nélkül" gombra nyomunk, akkor a nulláról tudunk elindítani egy új árubeérkezést.

Ennek a folyamata is megegyezik az előzőekkel, annyi különbséggel, hogy itt az előzmény hiánya miatt nem lesz javasolt cikk a listában. Ezért csak az "Egyéb cikk" nyomógombbal tudunk továbblépni.

Az árubeérkezés véglegesítésekor az SAP Business One-ban szállítói árubeérkezés fog létrejönni előzmény nélkül.


-----------------------------------------
## Raklap megtekintés, összeállítás

### Mezők

- Raklap törlés gomb
- Kilépés gomb
- Raklap azonosító
- Cikk szűrő
- Cikk(ek)
- Lejárat
- Karton darab
- Egység darab
- Egyéb lejáratok listája
- Kartonsúlyok listája (csak nem egalizált termékek esetén, és olyankor kötelező)
- Cimkézettség
- Raklap típusa
- Mentés gomb
- Bontás esetén két fül

### Árubeérkezésből hívás

Ha az árubeérkezésből hívtuk, akkor vagy egy teljesen új raklapot kezdünk, vagy egy ugyanebben az árubeérkezésben korábban már elkezdett raklapot módosíthatunk.
Jellemzően már az árubeérkezés tétel képernyőjén raklap vonalkódot lövünk, ilyenkor azonnal megjelenik a raklap azonosítóban ez a raklap vonalkód. De ha ott nem lőttünk vonalkódot, itt még megtehetjük, illetve
kézzel is beírhatjuk azt. (Célszerűbb a vonalkódolvasót használni.)

Ha olyan raklapazonosítót válaszottunk ki, ami még nem lett használatba véve a rendszerben, akkor ez egy új raklapnak számít, az adatok kitöltése és a "Mentés" gomb megnyomása után jön létre a raklap.
Ha olyan raklapazonosítót választottunk, amit ugyanebben az árubeérkezésben már egyszer elkészítettünk, akkor annak adatait látjuk, tudjuk módosítani, és a "Mentés" gombbal átvezetni a változásokat.
Egyéb raklapazonosítókra itt a program hibát jelez.

### Tárhely cikkeiből megtekintésre

Ha megtekintésre nyitottuk meg a formot, akkor semmi nem módosítható, kivétel a cimkézettség, raklap típus.
Illetve a lejáratokat, karton súlyokat is lehet módosítani, de az összsúly nem változhat, sem a legrövidebb lejárat.

### Bontásra

Ha bontásra hívtuk meg, akkor két fül jelenik meg, az egyiken a kiválasztott (bontandó) raklap, a másikon az új jelenik meg.
Az új raklaphoz raklap azonosítót lehet lőni, a mennyiséget meg lehet adni, mennyi megy át az adott cikkből (automatikusan csökken a másik oldal)
és a lejáratokat, súlyokat lehet módosítgatni.

### Kitárolási javaslatból hívás

...

### Leltárból hívás

Ilyenkor elrejtjük a rendszer szerinti mennyiségeket.

### Lejáratok kezelése

Minden raklaphoz meg kell adni a lejárati időt, ez a képernyő felső részén, a cikknév alatt található. Ide beírható, vagy naptárnézetből kiválasztható a dátum. Beírásnál egyszerűsíthetünk:
- Csak egy kétjegyű szám: ez az aktuális hónap adott napját jelenti. (pl.: "08" az aktuális hónap 8-a)
- Csak egy négyjegyű szám: az aktuális év első két számjegy szerinti hónapjának a második két számjegy szerinti napja. (Pl.: "1231": Az aktuális év december 31-e)
- Csak egy hatjegyű szám: Mint az előbbi, de az első két karakter az évszámot jelenti. (Pl.: "251231": "2025.12.31"-et jelent)

Ha a raklapon több lejárat is található, akkor ide a legrövidebbet írjuk fel. A többit felsorolásszerűen vihetjük fel egyéb lejáratként.
Az egyéb lejáratok a képernyő bal alsó részén találhatóak listaszerűen felsorolva. Újat úgy tudunk felvenni, ha belekattintunk a lista fölött lévő dátum beviteli mezőbe, és beírjuk/kiválasztjuk a lejárati dátumot. Ha beírtuk,
a listába akkor kerül be az új lejárat, ha elhagyjuk a mezőt. A beviteli mezőre visszalépésnél a korábbi érték onnan törlődik, újat lehet beírni.
- Ha rövidebb lejáratot írtunk be, akkor a program kicseréli a fő lejárat mezővel. (Ez csak árubeérkezésnél működik, beérkezett raklapnál már nem módosíthatjuk a fő lejáratot.)
- Ha ugyanazt a dátumot írjuk be ismételten, azzal tudjuk törölni a listából az adott dátumot.

### Raklap törlése

A raklap törlés gombnak csak akkor van hatása, ha még beérkezés alatti raklapról van szó. (Egyszer már berögzítettük az árubeérkezéshez, majd újra felhozzuk ezt a raklapot, de még közben nem véglegesítődött az
árubeérkezés.) Ilyenkor rákérdezés után végérvényesen törli a raklapot a rendszerből, a rajta lévő készlettel, mintha soha nem is történt volna meg ennek felvitele.

Már beérkezett raklap esetén akkor működhet a törlés, ha már nincs rajta semmilyen mennyiség, de mégsem lett kivezetve a raklap. Ilyenkor a törlés csak kivezeti a raklapot.

### Egyedi kartonsúlyok felvitele

Egyedi kartonsúlyokat csak nem egalizált termék esetén lehet felvinni. A listája a jobb alsó sarokban található. A már felvitt összes értéket egy mozdulattal az "X" gommbal lehet törölni.
Három módszerrel lehet felvinni:

#### Kézi bevitel

Ha a kartonsúlyok listája fölötti azonosítóba beírunk egy azonosítót, majd a mellette lévő súly mezőbe beírjuk annak egyedi súlyát, majd azt elhagyjuk, akkor beíródik ez a két érték a listába.
Ha a már felvitt karton azonosítót újra beírjuk, azzal módosítani tudjuk a korábban bevitt hozzá tartozó súlyt.
Ha a már felvitt karton azonosítót újra beírjuk, és a súly mezőbe 0-t írunk, azzal törölni tudjuk a listából.

#### Félautomata bevitel

Ha a karton azonosítót nem adjuk meg, csak a súlyt, elhagyjuk a mezőt, akkor is bekerül a bejegyzés a listába, de egy generált azonosítóval: "001", "002", stb.

#### Vonalkódos bevitel

Ha lelőjük a termék súly vonalkódját, akkor rákérdez a program, hogy beállítsuk-e a vonalkód szerinti bevitelt. Feltételezzük, hogy egy termékhez ugyanolyan formátumú súlykódok érkeznek, ezért a beállítást csak
egyszer kell megtenni, a következő alkalommal már magától viszi be a súlyokat a program a listába. Ha mégis módosítani akarunk rajta, akkor nyomjunk rá a "III" nyomógombra.

##### Súlykód formátum beállítása

Egy dialógus ablak jön fel, ahol a lelőtt vonalkódot látjuk külön kockákban. Négy plusz kocka van: "\[", "\]", "<", ">". Ezeket a plusz kockákat kell a megfelelő helyre helyezni, ahol a
- "\[" jelenti a súly egész részének kezdetét
- "\]" jelenti a súly egészrészének végét
- "<" jelenti a súly tizedesrészének kezdetét
- ">" jelenti a súly tizedesrészének végét.

Ezeket úgy tudjuk áthelyezni, hogy először rákattintunk a jelre (az pirossal kjelölődik), majd átkattintunk arra a számra, ami elé, vagy mögé akarjuk ezt a jelet elhelyezni.


-----------------------------------------
## Tárhely cikkei

A felső blokkban a raktárt + tárhelyet választjuk ki (tárhely vonalkódolvasóval - is).

Az alsó blokkban felsoroljuk a tárhelyen lévő raklapokat és a raklapokon lévő cikkeket.

Legalul nyomógombok:
- Áttárol (A kiválasztott raklapot megjegyzi, és azzal megnyitja az áttárolás formot)
- Bont (A raklap formot nyitja meg bontási módban.)
- Néz (A raklap formot nyitja meg megtekintési módban.)
- Kilép

A raklapot kiválasztani a vonalkód beolvasásával is lehet. Ha így kiválasztottuk, majd másodjára is rálövünk a vonalkódra, akkor a raklap megnézés funkció aktiválódik.

### Betárolás

A "Betárolás" funkció szinte ugyanúgy működik, mint a "Tárhely cikkei", viszont itt csak az LBE tárhely készletét láthatjuk. Kifejezetten az árubeérkezés utáni betárolásra van optimalizálva ez a funkció.
Ha az LBE tárhelyen lévő raklap vonalkódját beolvassuk, akkor azonnal az "Áttárolás" funkcióba kerülünk.

### Áttárolás

Ide már egy kiválasztott raklap után kerülünk, ennek a raklapnak az azonosítója jelenik meg felül.
Alapvetően tárhely lelövéssel kell kiválasztani a céltárhelyet, de be is lehet írni, illetve a képernyő középső részén megjelennek azok a tárhelyek, ahol már található ebből a cikkből valamilyen készlet.


-----------------------------------------
## Cikk tárhelyei - nem kell???

-----------------------------------------
## Bontásra komissiózás

Ebben a funkcióban lehet előkészíteni a kitárolási javaslattal előírt bontásokhoz a készletet. Azokat kell bontani, amit nem teljes egészében kell kiszedni a tárhelyről, mivel kevesebb mennyiségre van szükség.

Itt a bontás első részlépése történik meg: a teljes raklapot kimozgatjuk a jelenlegi fizikai tárhelyükről, és áttesszük a KOM nevű logikai tárhelyre.

### A képernyő elrendezése

Fent egy raktár és egy terem legördülő lista van. A raktár adott, mert csak KOZPONT raktárban dolgozik ez a fejlesztés, azon belül az egyes termeket lehet kiválasztani.
A raktár / terem kiválasztás után az alatta lévő táblázatban megjelennek az előírt kitárolási utasítások, ami nem egész raklapra szól. A táblázat oszlopai:

| Mező | Leírás |
|:-----|:-------|
| Tárhely | Melyik tárhelyről kell kiszedni a terméket |
| Raklap | Melyik raklapról kell kiszedni |
| Vevő | Melyik vevő számára |

### Működés

A táblázatban a kiválasztott kitárolási javaslaton a kiválasztott raktár / teremre előirt raklapokat lehet látni. Csak vonalkódolvasóval tudunk itt komissiózni.
- Először a tárhely vonalkódját kell lelőni. Ekkor az adott sorra áll a program, és élénkzöld szín jelzi, hogy sikeresen kiválasztottuk a tárhelyet.
- Utána a raklapot kell lelőni. Csak akkor lőhetjük a raklapot, ha előtte a tárhelyet is azonosítottuk.

A helyes tárhely / raklap azonosításra feljön egy kérdés, hogy valóban át akarjuk-e mozgatni ezt a raklapot a KOM tárhelyre. OK megnyomására, vagy a raklap azonosító ismételt lelövésére az áttárolás megtörténik, a sor eltűnik a táblázatból.


-----------------------------------------
## Bontás

A "Bontásra komissiózás" form folytatása. Ugyanazokat kell listázni, de már csak azt, amit abban a funkcióban áttettünk a KOM tárhelyre. A folyamat során egy új raklapot nyitunk, amire sorban át fogjuk tenni az egyes termékeket az előkészített raklapokról.

### A képernyő elrendezése

A képernyő felső sorában egy legördülő lista és egy legordülő nyomógomb van:
1. A legördülő listában a kitárolási javaslatokat látjuk, azokat, amin van KOM-ba áttárolt, de még nem komissiózott raklap. Valamelyiket ki kell választanunk.
2. A képernyő jobb oldalán az "Újtip" gombra kattintva ki tudjuk választani, hogy abban az esetben, ha egy teljesen új raklapra kezdünk el komissiózni, az milyen típusú. (EUR raklap, stb.) Ha nem választunk ki egyet sem, akkor EUR raklapot feltételez a program.

A képernyő ez alatt található legnagyobb részén táblázatos formában a KOM tárhelyre előkészített raklapokat látjuk.
| Mező | Leírás |
|:-----|:-------|
| Raklap | Melyik raklapról kell kiszedni |
| Tárhely | Melyik fizikai tárhelyen volt eredetileg. (Már a KOM-on van, csak informatív szerepet játszik ez a mező.) |
| \# | Komissiózandó mennyiség |

A táblázat alatt a kiválasztott kitárolási javaslat megjegyzése, az alatt pedig a kiválasztott tételsoron szereplő cikk száma és neve olvasható.

Legalulra került a terem választó legördülő menü, és a kilépés gomb.

### Működése

Csak vonalkódolvasóval tudunk itt komissiózni.
- Annak a raklapnak a vonalkódját kell lelőni, amire a szedjük a termékeket. Célszerűen ez egy új azonosító lesz, vagy egy korábbi folyamat félbehagyása után a már meglévő félig kész raklapot is lehet folytatni.
  - Ez a raklap az LKI tárhelyre kerül (ha még nem volt ott.)
  - Ha már ott van, akkor arra is szedhetünk, de csak akkor, ha ezt a raklapot nem egy másik vevő számára készítettük elő korábban. Ugyanarra a vevőre mehet akkor is, ha másik kitárolási javaslathoz tartozott.
  - Akár többször is, minden bontás előtt rálőhetünk erre a raklapra, akkor biztosan nem fogunk tévedni.
- Utána kell a táblázatban látható raklap vonalkódját lelőnünk.
  - Ekkor a program kiírja, hogy milyen cikkből mekkora mennyiséget kell átpakolni az előzőekben megnyitott komissiós raklapunkra.
  - Ezt leokézva, vagy a raklap azonosító újbóli lelövésével nyugtázhatjuk a bontást. Innen kezdve a megadott mennyiség már a másik raklapon van.
  - Ha nem egalizált termékről van szó, akkor feljön a raklap bontó képernyő, ott kézzel kell elvégezni a bontást, mert meg kell határozni, hogy mely egyedi csomagok kerülnek át egyikről a másikra.


-----------------------------------------
## Kiszedési javaslat

Ezen a felületen azokat a kitárolásokat tudjuk elvégezni, amiket nem kell bontani.

### A képernyő elrendezése

A felső sorban egy raktár és egy terem legördülő lista van. A raktár adott, mert csak KOZPONT raktárban dolgozik ez a fejlesztés, azon belül az egyes termeket lehet kiválasztani.

A raktár / terem kiválasztás után az alatta lévő táblázatban megjelennek az előírt kitárolási utasítások, amik egész raklapra szólnak. A táblázat oszlopai:

| Mező | Leírás |
|:-----|:-------|
| Dátum | A kitárolási javaslat dátuma |
| Vevő | A vevő neve és címe |
| Megjegyzés | A kitárolási javaslathoz írt megjegyzés - ez is segít beazonosítani. |

Ez az alapértelmezett képernyő elrendezés, viszont ha a lenti legördülő gomb segítégével a szedés módját átállítjuk "Folyamatos szedés"-ről "Cikkre szedés"-re, akkor ez alatt megjelenik egy másik táblázat.
Ez a másik táblázat mindig a fölötte kiválasztott kitárolási javaslat tételeit (cikkeit) mutatja.

| Mező | Leírás |
|:-----|:-------|
| Cikk | Cikk neve |
| Mennyiség | |
| Karton | |

A képernyő legalján található a:
- Kiszed nyomógomb
- Szedés módja nyomógomb ("Cikkre?" felirattal)
- Kilépés gomb

### Működése

- Ki kell választanunk a raktár / termet, ahol dolgozunk.
- Ki kell választani az alatta lévő táblázatból egy kitárolási javaslatot
- Ha cikkre szedés módban vagyunk, akkor alatta egy cikket is válasszunk ki.
- Nyomjunk a "Kiszed" gombra

A kiszed gombbal feljön egy másik képernyő, ahol a kiválasztott kitárolási javaslat még szedendő tételeit fogjuk látni. (Cikkre szedés esetén az adott cikkre leszűrve.)

### Kiszedő képernyő elrendezése

Felső sor: Raktár választó (bár csak KÖZPONT lehetőségünk van), és "Gyűjtő" mező, mellette "Bont" gombbal.
Eggyel alatta a táblázatban éppen kiválasztott sor cikkét látjuk.

Ez alatt a táblázatban a kiszedendő sorok jelennek meg.

| Mező | Leírás |
|:-----|:-------|
| Tárhely | Melyik fizikai tárhelyen van a raklap |
| Raklap | Melyik raklapot kell szedni |
| \# | A raklapon lévő és egyben kiszedendő mennyiség |

A legalul lévő nyomógombbal ki lehet lépni a formból. (Vissza tudunk lépni az előző képernyőre.)

### Kiszedő képernyő működése

Először a tárhelyet kell lelőni, majd a raklapot. Ha mindezt jó sorrendben tesszük, és a megfelelő, összetartozó értékeket lőttük, akkor a rendszer az adott raklapot az LKI tárhelyre mozgatja. A listából eltűnik ez a bejegyzés.


-----------------------------------------
## Kocsira pakolás

Ebben a menüpontban lehet a korábban komissiózott (LKI tárhelyen lévő) raklapokat hozzárendelni egy-egy konkrét rendszámhoz, vagyis egy konkrét kiszállításhoz. Ennek segítségével fogjuk tudni, hogy egy-egy szállítólevélre végeredményben mely cikkek kerültek fel.

### A képernyő felépítése

Fentről lefelé a következő mezők láthatóak a képernyőn:
- Vevő legördülő lista. A menüpontba belépéskor ennek értéklistája feltöltődik azokkal a partnerekkel, akire van olyan kitárolási javaslat, aminek már történt komissiózása. Egész pontosan vevő, vevőcím és szállítási dátumonként jelennek meg ezek a választási lehetőségek.
- Egy szövegdoboz, amiben a legördülő listában kiválasztott vevőhöz (+szállítási dátum +cím) tartozó részletes adatok jelennek meg - ami a kapcsolódó kitárolási javaslatok megjegyzés mezőjébe be lett írva.
- Egymás mellett található a következő két elem:
  - Rendszám választó lista.
  - Az adott rendszámra rálőtt raklapok listája
- Egy szövegdoboz, amiben a lelőtt raklap adatai láthatóak.
- Három nyomógomb:
  - Kilép: Visszalép a kezdőképernyőre.
  - "...": A lelőtt raklap adatait tudjuk megnézni a raklap megtekintő képernyőn.
  - Néz: A rendszám melletti raklap listában kiválasztott bármelyik raklap adatait tudjuk megnézni a raklap megtekintő képernyőn.
  
### Működése

- Megnyitáskor a teljes képernyő üres.
- Válasszuk ki azt az értéket a vevő legördülő listából, akinek a pakolást végre akarjuk hajtani.
- Ekkor frissül az alatta lévő szövegdoboz a kitárolási javaslatok adataival, illetve a rendszám legördülő listát lenyitva megjelennek az adott vevőhoz (+címhez, +naphoz) már korábban hozzárendelt rendszámok. Plusz egy "Új gépkocsi" lehetőség.
- Először meg kell határoznunk az autót, amire pakolunk.
  - Ha korábban ennek az autónak a rendszámát még nem rendeltük hozzá nyitot állapotban lévő pakoláshoz, akkor álljunk rá az "Új gépkocsi" lehetőségre.
    - Itt lőjük le a gépkocsi rendszámának vonalkódját.
    - Ekkor a program meg fogja kérdezni, hogy valóban erre pakolunk-e. Nyomjunk "OK"-t, vagy csak ismételjük meg a gépkocsi vonalkódjának lelövését.
    - Megerősítés után a rendszám legördülő listában megjelenik, és kiválasztásra kerül ez a rendszám.
  - Ha már korábban történt erre pakolás, akkor a listában meg kell jelennie - válasszuk ki.
    - Kiválasztás után a képernyő jobb oldali részén meg kell jelennie a korábban már felpakolt raklapok listájának.
- Az autó meghatározása után lőjük le a raklap azonosítót.
  - Ha nem létezik a raklap, vagy nem az LKI tárhelyen van, vagy nem ehhez a partnerhez tartozik, vagy másik kocsira lett már rápakolva, akkor hibát jelez a program.
  - Ha ezen az autón már fent van ez a raklap, akkor megkérdezi, hogy visszavonjuk-e. "OK"-ra nyomva, vagy a raklap újabb lelövésére lekerül az autóról ez a raklap.
  - Egyébként ez a raklap rápakolható a kocsira, és az alsó szövegdobozban megjelennek a raklap adatai. Ezzel előkészítettük a felpakolást, kijelöltük a felpakolandó raklapot.
- Ha ki lett jelölve a felpakolandó raklap, akkor a rendszám újabb lelövésével történik meg a raklap autóra helyezése.



-----------------------------------------
## Leltár

Listáznia kell a nyitott ifsz addonban definiált leltárakat. De itt is lehet újat indítani a tárhely és szint megadásával.

A leltároz gomb megnyomására leltár módban jutunk a tárhely listára, illetve onnan a raklap karbantartóra. A módosításokat
más oszlopokba jegyezzük le.

-----------------------------------------
## Raklap napló - nem kell ???
