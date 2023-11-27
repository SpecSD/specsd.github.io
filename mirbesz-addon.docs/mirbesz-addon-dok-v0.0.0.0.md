# Részletes cikk információ nyilvántartó

A fejlesztés célja, hogy olyan tulajdonságokat is nyilvántartsunk a rendszerben lévő cikkekről, amik az SAP Business One-ban nem léteznek. A részletes cikk innformációs addonban a  cikktulajdonságok dinamikusan bővíthetőek, jól lekérdezhetőek. SAP B1 mező esetén a cikkhez tartozó értékek a SAP-ból frissül és oda is mentjük vissza a módosításokat. 

Egy külön ["formon"](#reszletes-cikk-cikktul) tetszőleges tulajdonságokat rögzíthetünk. Amit itt felrögzítettünk, azokat a tulajdonságokat látjuk a ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon, és az egyes cikkekhez ezen tulajdonságainak kell értéket adnunk.  A cikktulajdonságokat csoportokba tudjuk sorolni, az egyes csoportok külön fülön jelennek meg a formon.

## Cikk tulajdonságok form <a name="reszletes-cikk-cikktul"></a>

Itt tudjuk karbantartani, hogy a részletes cikk információ formon milyen tulajdonságok jelenjenek meg, és ezek kezelése hogyan történjen.

A form egy blokkból áll, ahol táblázatos formában az egyes cikk tulajdonságokat lehet felvinni.

| Mező         | Leírás                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kód          | Egy egyértelmű kódot adjunk a cikktulajdonságnak, amivel hivatkozni tudunk rá. Kötelező és egyedi.                                                                                                                                                                                                                                                                                           |
| Sorrend      | Egy számot adhatunk meg.                                                                                                                                                                                                                                                                                                                                                                     |
| Címke        | A ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon ez lesz a címkéje az adott oszlopnak.                                                                                                                                                                                                                                                                                      |
| Érv.?        | Érvényes? - jelölőnégyzet. Csak az érvényesek jelennek meg a ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon.                                                                                                                                                                                                                                                                |
| Külső oszlop | Az értéke az eredeti rendszerből jön. Értéklistából választható                                                                                                                                                                                                                                                                                                                              |
| Köt.?        | Kötelező? - jelölőnégyzet.                                                                                                                                                                                                                                                                                                                                                                   |
| Szélesség    | A mező megjelenített szélessége.  A ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon minden sort 12 egyenlő részre osztottunk meg. Attól függ, hogy ebben a  mezőbe milyen értéket írunk, hogy hány mező kerül egy sorba. Ha a szélesség mezőbe 12-t írunk, akkor egy sorba egy mező fog megjelenni. Amennyiben 3-at, akkor akár 4 db 3 egység széles mező is meg tud jelenni egy sorban. |
| Adattípus    | A tulajdonság adattípusa: Alfanumerikus, numerikus, dátum, dátum+idő. Értéklistából választható                                                                                                                                                                                                                                                                                              |
| Értéklista   | Az értéklista, domain, nézet oszlopok alapján tudunk választási lehetőségeket adjunk egy mezőben a felhasználónak. Ez egy igen/nem-es oszlop. Ha ez "Nem"-re van állítva, akkor legördülő listában jelennek meg a lehetséges értékek. Ha igen-re, akkor sima textbox, és azon *tabbal választhatunk értéklistából értéket.                                                                   |
| Megjegyzés   | A tulajdonsághoz tetszőleges megjegyzés rögzíthető. A ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon a mező címkéjére húzva a kurzort, megjelenik a megjegyzésbe írt szöveg.                                                                                                                                                                                                |
| Tul.csop. ID | Az adott tulajdonságot melyik tulajdonságcsoportba soroljuk. A ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon minden tulajdonságcsoport külön fülön jelenik meg.                                                                                                                                                                                                            |
| Domain       | Az értéklista, domain, nézet oszlopok alapján tudunk választási lehetőségeket adjunk egy mezőben a felhasználónak. Ha ki van töltve, akkor egy domain nevet értünk alatta. Ilyenkor a cikk információs form legördülő listát jelenít meg az adott domain SPC_DOMAINS-ben felsorolt értékeivel.                                                                                               |
| Módosítható  |                                                                                                                                                                                                                                                                                                                                                                                              |
| Nézet        | Az értéklista, domain, nézet oszlopok alapján tudunk választási lehetőségeket adjunk egy mezőben a felhasználónak. A domaineken túl is kell lehetőséget adni arra, hogy lehetőségek közül lehessen választani. (Pl. partner, gyártó lista) Erre szolgálna a "Nézet" mező.                                                                                                                    |
| Alapérték    |                                                                                                                                                                                                                                                                                                                                                                                              |

### Szabályok, ellenőrzések

- A "Kód"-nak egyedinek kell lennie, kétszer ugyanaz nem vehető fel.
- A "Sorrend" értékek ismétlődhetnek, de nem célszerű így rögzíteni, mert az azonos sorszámmal bíró tulajdonságok közötti megjelenési sorrend nem meghatározott.
- Ha egy tulajdonság érvényességét megszüntetjük, attól még nem tűnnek el a korábban az egyes cikkekhez felvitt értékek, de a ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon már nem lesznek láthatóak, és egyéb fejlesztések sem dolgozhatnak ezekkel az adatokkal.
- Ha egy érvénytelenített tulajdonságot újra érvényesítünk, akkor azonnal látni fogjuk a korábban nem törölt tulajdonság értékeket a ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon.
- Ha a tulajdonságot kötelezőre állítjuk, akkor a program ellenőrzi, hogy minden cikk esetén - amihez már rögzítettünk bármilyen tulajdonságot - van érték adva ennek a tulajdonságnak
  - Emiatt új tulajdonságot csak akkor állíthatunk kötelezővé, ha még semmilyen cikkhez sem rendeltünk tulajdonság értéket.
  - Ha már legalább egy cikkhez van tulajdonság rendelve, akkor először nem kötelezőként tudjuk létrehozni, utána minden cikknél adunk neki valami értéket, és utólag állítjuk kötelezőre.
- "Értéklistá"-snak csak akkor állíthatjuk be a tulajdonságot, ha az adattípusa alfanumerikus.
- A következő esetekben a program leellenőrzi, hogy bármelyik cikkhez van-e már rendelve ehhez a tulajdonsághoz érték. Ha van, akkor hibát dob:
  - Az adattípus módosul
  - A "Külső oszlop" üres volt, és kitöltjük
- Ha az "Értéklista"-t módosítjuk, akkor is ellenőrzi a program, hogy nincs e olyan cikk tulajdonság érték, ami nem esik bele az értéklista lehetséges értékeibe. Ha van, akkor hibát jelez.

## Cikk tulajdonság csoportok form<a name="reszletes-cikk-tulcsopform"></a>

Ezen a formon tudjuk felvenni a tulajdonságcsoportokat, amelyekre a cikk tulajdonságnál kell hivatkozni. Minden ciktulajdonság csoport külön fülön jenelik meg a a ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon. 

| Mező       | Leírás                                                                                                                  |
| ---------- | ----------------------------------------------------------------------------------------------------------------------- |
| Kód        | Egy egyértelmű kódot adjunk a cikktulajdonság csoportonak, amivel hivatkozni tudunk rá. Kötelező és egyedi.             |
| Megnevezés | A tulajdonság csoport neve                                                                                              |
| Címke      | A ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon ez lesz a címkéje az adott fülnek az adott oszlopnak. |
| Megjegyzés | Tetszőleges megjegyzés                                                                                                  |

## Részletes cikk információ form <a name="reszletes-cikk-reszlform"></a>

Itt tudjuk feltölteni, és megtekinteni az egy-egy cikkhez rendelt tulajdonság értékeket. Minden cikkről látjuk a cikkszámát, és nevét (ezeket itt nem módosíthatjuk), valamit azokat a tulajdonságokat, amik a ["Cikk tulajdonságok"](#reszletes-cikk-cikktul) formon felvettünk - azok közül az érvényeseket.

Ugyanazon a képernyőn tudunk meglévő tulajdonságértékek alapján keresni, illetve cikkekhez tulajdonság értékeket rögzíteni. Balról az első gomb (egy nyíl) segítségével tudunk váltogatni 2 nézet között, amelyből az első az a kereső nézet, a második pedig a módosító nézet.

Ezek alapján a képernyő tulajdonképpen három blokkból áll:

- Legfelül a szűűrési feltételeknél megjelennek a cikktulajdonságok. Amikor a cikktulajdonságok szűrésként vannak a képernyőn, a mező háttere halványkék.

- Középen láthatóak a cikkek

- Alul pedig a cikkekhez rögzített cikktulajdonság értékek.

A három blokk közül dinamikusan mindig 2 jelenik meg a képernyőn. 

### Keresés cikktulajdonságok alapján

A form indításakor legfelül megjelennek a cikktulajdonságok, mint szűrési feltételek. Az alatta lévő blokkban láthatóak a szűrési feltételeknek megfelelő cikkek.

A cikktulajdonság mezőkben tudjuk megadni, hogy milyen tulajdonság értékek alapján akarunk keresni. Egyszerre több tulajdonság alapján is tud keresni a program 'vagy' feltétellel.

A legfelső blokk az egy gombsort tartalmaz:

A 'Keres' gombot megnyomva lefutattja a program a keresést. És a lenti blokkban megjelennek azok a cikkek, amelyeket a szűrés alapján megtalált a program.

A 'Kereső törlése' nyomógombbal tudjuk kiüríteni a szűrési feltételeket.

Az 'Összes cikk' nyomógombra felhozza a program az összes cikket az alsó blokkban. 

A 'Pontos egyezés' checkboxot bepipálva van lehetőségünk a szűrési feltételeknél csak a pontosan egyező cikkekre keresni. Pl.: Cikkcsoport szűrő mezőben az "eh" keresésre nem hozza fel azokat a cikkeket, ahol a cikkcsoport EH/SERTÉS, csak akkor, ha a szűrő mezőben "eh/sertés"-t írunk. A checkbox kivételének következtében, ha a szűrőmezőkbe írt értékek egy részlete is megtalálható egy adott cikknél, akkor azt a cikket fel fogja hozni. (Pl.: Az előző esetet nézve, az "eh" keresésre felhozza azokat a cikkeket, ahol EH/SERTÉS a cikkcsoport.)

A gombsor alatt látható egy szűrőblokk, amely a cikk tulajdonságok formon felvett tulajdonságokból áll, ezek különböző csoportokra vannak osztva, amelyeket külön füleken jelenítünk meg
A szűrőblokk alatt található táblázatos részben a Cikk részletes adatai jelennek meg.

### Cikkinformációk rögzítése a cikkekhez

A legfelső blokkban össze tudjuk csukni a fel-le nyíllal a szűrési feltételeket. Ebben az esetben a funkció gombok is változnak, illetve eltűnnek a lenti szűrő mezők.

Ilyenkor a felső blokkban a cikkek jelennek meg , a cikk kód és a cikk név látható az oszlopokban - ezek az adatok itt nem módosíthatóak. 

Az alsó blokkban pedig a cikkekhez rögzített cikk tulajdonságok és az adott cikkhez rendelt értékek láthatóak.

Tehát a felső gombsorban a nyílra kattintva a módosító nézetre válthatunk, ahol megváltoznak a gombsorban lévő gombok funkciói:

Az 'Aktualizálás' nyomógombbal segítségével a módosító nézetben a tulajdonságokon tett változtatások menthetőek el, aminek a sikerességéről a felhasználót is informáljuk

Az 'Új cikk információk' nyomógombbal tudjuk az adott cikkhez hozzárendelni a cikk tulajdonság mezőket. Ez azt is jelenti, hogy a felső blokkban megjelenik az összes cikk, viszont lesznek olyan cikkek, ahol az alsó blokkban nem látszik semmi. Amennyiben megnyomjuk az 'Új cikk információk' nyomógombot, az alsó blokkan megjelennek a cikk tulajdonságok és meg tudjuk adni az értékeket.

Az 'Összes cikk' az előző nézethez hasonlóan egy úgymond "Frissítés" gombbal ér fel.

A középső kék sávra kattintva tudunk megjelenítési módot váltani:

- A felső blokkban listaszerűen jelennek meg a cikkek és adott sorra állva tudjuk megnézni, módosítani az egyes tulajdonság értékeket. Ebben az esetben az alsó blokk kevesebb helyet foglal el a képernyőn.

- A felső blokk összecsukásakor, csak a kiválasztott cikkkódja és neve jelenik meg és az alsó blokkban tudjuk megnézni, módosítani az egyes tulajdonság értékeket. Ebben az esetben az alsó blokknak több hely jut, így akár több tulajdonság is látható egyszerre csúszka nélkül.

A módosítható tulajdonságok mind a megadott szabályok szerint tölthetőek:

- Adattípus: alfanumerikus
  - Amennyiben van definiálva "Értéklista/Domain/Nézet", akkor az adott listához tartozó értékeket láthatjuk itt. "*" beírásával értéklistában jönnek fel a választható értékek, illetve a "*"-ot "bármi behelyettesíthető ide" módon is értelmezhetjük. Pl.: `s*`: Az összes olyat fel fogja hozni az értéklistában, aminek a kódja, vagy neve s-sel kezdődik.
    Ha `*` nélkül a pontos kódot, vagy nevet beírjuk, akkor az adott érték elnevezése bekerül ebbe a mezőbe. Ha csak egy részletét írjuk be, és ez a részlet több értékre is ráillik, akkor feljön az értéklista az illeszkedő értékekkel. Ha csak egy értékre illik rá, akkor értéklista nélkül kiválasztásra kerül ez az egyértelmű érték.
  - Ha nincs értéklista, akkor tetszőleges értéket beírhatunk. 
- Adattípus: numerikus
  - Egy tetszőleges számot írhatunk be ide. 
- Adattípus: dátum, dátum+idő
  - Amit beírunk, azt dátumként értelmezi a program.
  - Dátum típus esetén csak a napot adjuk meg, dátum+időnél időpontot is.

### Tömeges cikkinformáció betöltés Excel-ből

A a ["Részletes cikk információ"](#reszletes-cikk-reszlform) formon lehetőség van cikktulajdonságok tömeges betöltésére. A betöltendő Excel fájl egyes oszlopai legyenek a cikktulajdonságkódok.

Excel-ből való cikk információk importálása esetén egy "Excel betöltés" nevezetű gombra kattintva tudunk tallózni egy Excel típusú fájlt, amit ha kiválasztunk és a megfelelő formázással rendelkezik ("cikkszám" oszlop nagyon fontos!), akkor elkezdi beimportálni a benne lévő adatokat.

Az Excel fált vagy ki tudjuk tallózni, vagy pedig rá is tudjuk dobni az Excel betöltéshez használt régióra.

### Excel export

A a ["Részletes cikk információ"](#reszletes-cikk-reszlform) formról történő Excel-be való cikk információk exportálása egy "Excel export" nevezetű gombbal történik, amely elmenti a formon megjelenő cikkeket a hozzájuk tartozó cikk információkkal együtt. Abban az esetben, ha nem történt semmilyen szűrés, akkor az összes cikket, az összes cikk információjával együtt exportálja, viszont ha leszűrtük bizonyos számú cikkre, akkor csak azok a cikkek kerülnek exportálásra. Amint elkészült az exportálás, azt követően megjelenik a jobb felső sarokban a Letöltések között a kész Excel fájl.

 

### Mellékletek csatolása

Szükség lehet a cikkhez többféle típusú fájl csatolására, pl. termék fotó, specifikációs pdf fájl stb. Ehhez bevezetünk egy  Fájl típusú tulajdonságot, amelynél lehetővé tesszük, hogy ezekben a mezőkben ki tudjon választani egy fájlt. Mentéskor pedig a fájlt feltölti a program egy paraméterben megadott útvonalra. A fájlt meg lehet nyitni a form felületéről is.

# EPR bevallás kezelés

-----------------------------

## Bevezetés

 2023. július 1-jétől életbe lépett a 80/2023. (III. 14.) Korm. rendelet a kiterjesztett gyártói felelősségi rendszer (EPR - Extended Producer Responsibility) működésének részletes szabályairól.

E rendelet hatálya az 1. mellékletben meghatározott, az 1. melléklet 2. pontja szerinti, nyolc számjegyből álló azonosító számmal, a körforgásos kóddal (a továbbiakban: KF kód) azonosított, a hulladékgazdálkodási intézményi résztevékenység körébe tartozó kiterjesztett gyártói felelősségi rendszer hatálya alá tartozó termékekre (a továbbiakban: körforgásos termék), a körforgásos termékek hulladékára és az ezekkel kapcsolatos, e rendelet szerinti tevékenységekre terjed ki.

A körforgásos termékeket 8 számjegyű KF kódokkal azonosítja. A KF kód felépítése:

1. Az 1 és 2. karakter: Termékáram és az abból képződött hulladékot jelölő kód
2. A 3 és 4. karaktere: Anyagáram kód
3. Az 5.  és 6. karaktere: Csoport kód
4. A 7.  karaktere: Termék esetén kötelezettséget, hulladék esetén hulladékkezelést jelölő kód
5. A 8. karaktere: Származást jelölő kód

Az elfogadott törvénymódosítás az EPR rendszer bevezetése mellett néhány anyagáram esetében megtartja a termékdíj fizetési kötelezettséget is. A rendeletben meghatározott termékdíj összegéből azonban le lehet  vonni az EPR díj összegét. Ha az így kialakult szám 0 vagy negatív  előjelű, akkor ténylegesen nem keletkezik termékdíjfizetési  kötelezettség. A termékdíjat változatlanul a vámtarifaszám 
alapján kell bevallani, az EPR díjat pedig a 8 jegyű KF kód alapján.

Az EPR bevallást negyedévente kell teljesítéseni a MOHU erre megadott felületén.

A bevallás elkészítése előtt tisztázni kell:

- Az adott cég milyen folyamat és milyen cikkek  alapján kötelezett a bevallásra a körforgásos termékek anyagáramánál.

- Az 'első belföldi forgalombahozatal' tekintetében a beszerzési illetve értékesítési forgalom alapján teljesítjük-e a bevallást. (Egyáltalán tudjuk-e az értékesítési oldalon pontosan megmondani, hogy mely termékek a külföldi beszerzésűek)

- Az adott cég milyen egyéb folyamatok, bizonylatok alapján érintett az EPR bevallásban, pl.: göngyölegek, saját felhasználás, gyártás stb.

Ebben a dokumentumban az értékesítési/ vagy beszerzési számla forgalom alapján történő EPR bevallásának támogatását írjuk le. A funkció alkalmas akár beszerzési, akár értékesítési oldal alapján elkészíteni az adott negyedéves EPR bevalláshoz szükséges riportokat.

Az adott cég egyéb folyamatait miatti EPR összegek nem részei a fejlesztésnek. (pl. saját felhasználás, gönygölegek stb.)

## Előfeltételek, beállítások

### Cikktörzs jelölés

A bevallásban érintett cikkekhez hozzá kell rendelni a KF kódot. Erre a 'Részletes cikkinformációs form' - on van lehetőség. 

Ezen a formon tudunk a cikkekhez olyan információkat nyilvántartani, amelyre az EPR rendszerben (pl.: SAP Business One) nem léteznek külön mezők. A részletes cikk innformációs addonban a cikktulajdonságok dinamikusan bővíthetőek, jól lekérdezhetőek. SAP Business One mező esetén a cikkhez tartozó értékek a SAP-ból frissül és oda is mentjük vissza a módosításokat. (Részletes használati leírás a modul dokumentációjában)

A Részletes cikkinformációknál az 'EPR' tulajdonságcsoport került felvételre. Ehhez a tulajdonságcsoporthoz hozzá lettek rendelve a cégnél előforduló KF kódok, mint cikktulajdonságok. Ezáltal a cikkekhez külön fülön megjelennek az EPR-re kapcsolatos mezők (KF kódok)

Az EPR bevallásban érintett cikkekhez beállításra kerültek az adott KF kódhozz tartozó mezőben az adott cikkr 1 kg-jára vonatkozó csomagoló anyag gramm súlyok. 

A cikkek beállítása történhet manuálisan, vagy tömeges betöltéssel Excel fájlból.

### EPR csomagolási díjak form

Ezen a formon kell felvinni a jogszabály szerinti EPR csomagolási díjakat, és azok beállításait. Ennek a formnak az alsó blokkjában rendeljük hozzá egyrészt a KF kódokat, másrészt pedig időszaki hozzárendeléssel a csomagolási díjak értékét.

![](../media/EPR_01.jpg)


#### Felső blokk - Díjkategóriák

| Mező       | Leírás                                                                     |
|:---------- |:-------------------------------------------------------------------------- |
| Díjkód     | A díjkategória kódja                                                       |
| Megnevezés | A díjkategória megnevezése                                                 |
| Típus      | A díjkategória típusa: Lehetséges értékei: EPR díjkategória, CSK kategória |
| Megjegyzés | Tetszőleges megjegyzés                                                     |

Itt lehet karbantartani a jogszabály által előírt díjkódokat, kategóriákat. A kétféle típussal tudjuk egyrészt az EPR bevalláshoz tartozó díjakat, másrészt pedig a környezetvédelmi termékdíj bevalláshoz szükséges CSK kódonkénti díjakat megadni.

A blokk tetején lévő 'Új díjkategória' nyomógombbal tudunk új sort felvenni a díjkategóriák közé. A 'Díjkategória törlése' nyomógombbal pedig kitöröni már létező sort.

Az alsó blokk két részre van osztva.

### Alsó bal blokk -Díj értékek

Ide lehet felvinni a fenti blokkban kiválasztott díjkódhoz tartozó "gyártó által fizetendő kiterjesztett gyártói felelősségi díjat".  Időszakot megadva tudjuk a díj értékét rögzíteni. 

Azért van lehetőség kezdő és záró dátumot megadni, hogy ha idővel változnak a díjak, akkor is visszakereshetőek, és kalkulálhatóak legyenek a korábbi időszakra vonatkozó összegek is.

| Mező           | Leírás   |
|:-------------- |:-------- |
| Kezdő dátum    | Kötelező |
| Záró dátum     |          |
| Összeg (Ft/kg) |          |

Induláskor a kezdő dátumnak adjuk meg az érvénybe lépés időpontját (2023.07.01), és a záró dátum maradjon üresen. Ezzel jelezzük, hogy jelen állapot szerint ez az összeg a jövőben sem fog változni.
Végül adjuk meg a jogszabály szerinti díj összegét.

Ha később változik az összeg, akkor ezen a soron állítsuk be a záró dátumot az utolsó napra, amikor a régi összeg még érvényes. Vegyük fel egy új sort az új összeggel, ahol a kezdő dátum az új összeg érvénybe lépésének dátuma lesz.

Amennyiben a már felvett díjhoz tartozó sort törölni szeretnénk a 'Díj törlése' gombbal tudjuk megtenni.

#### Ellenőrzések

Aktualizálás előtt a rendszer ellenőrzi, hogy az adott díjkódhoz berögzített összegek dátumai nincsenek-e ellentmondásban:

- Átfedés nem lehet az időszakok között. (Pl. ha van egy sorunk, ami 2023.07.01 - 2025.12.31-ig tart, akkor a másik sorunk kezdődátuma nem lehet e két dátum közötti érték)
- Hézag sem maradhat időszakok között. (Pl. ha az egyik sor záró dátuma 2025.12.31, akkor a következő sornak 2026.01.01-gyel kell kezdődnie.)

### Alsó jobb blokk - KF kódok

| Mező              | Leírás                                 |
|:----------------- |:-------------------------------------- |
| Tulajdonság kód   | Cikk tulajdonság értéklistából         |
| Tulajdonság címke | A kiválasztott tulajdonság címkéje     |
| Megjegyzés        | A kiválasztott tulajdonság megjegyzése |

Itt adjuk meg a felső blokkban kiválasztott díjkódokhoz tartozó KF kódokat. KF kódnak nevezzük, valójában ez egy cikk tulajdonságot jelent. Értéklistából kiválasztható a cikk tulajdonságok törzsből.
Tehát a díj kódhoz cikk tulajdonságot rendelünk. Emiatt előfordulhat, hogy a mi értelmezésünkben itt olyan tulajdonságok is megjelenhetnek, ami nem KF kód, ezért a rögzítő felhasználó felelőssége, hogy megfelelő adatokat töltsön itt fel.

'Új KF kód hozzáadása' nyomógombbal tudunk új tulajdonságot hozzárendelni, törölni pedig a 'KF kód törlése' nyomógombbal lehet.

#### Ellenőrzések

A program ellenőrzi, hogy az újonnan felvitt (vagy módosított) cikk tulajdonság még korábban más soron nem lett felvéve, ugyanolyan típushnál más díjkódhoz sem. 

Ugyanaz a KF kódot megadhatjuk egy EPR Díjkategóriához és egy CSK kategóriához is.

## EPR beállítások használata

- A díj kategóriákat felrögzíti a felhasználó
- Ehhez beállítja a díj összegeket, és kapcsolódó cikk tulajdonságokat. (KF kódokat)
- A cikk információk formon minden érintett tulajdonsághoz (KF kódhoz) meg kell adni, mennyit tartalmaz az adott termék csomagolása ebből az anyagtípusból.
- Az adatszolgáltatási időszakban külön lekérdezésekkel ki tudjuk mutatni a csomagolóanyag súlyát és a kapcsolódó EPR díj értékét is. 
- Mivel nemcsak EPR díjkategóriát, hanem CSK kategóriát is fel tudunk venni, ezért a környezetvédelmi termékdíj értékét is ki tudjuk mutatni hasonló elvek szerint, csak CSK kódonként.

## Lekérdezések

#### Beszerzési lekérdezések

<u><b><strong>1. KF lekérdezések</strong></b></u>

**EPR lekérdezés KF súlyok:** bizonylatonként tételesen mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti EPR súlyokat.

**EPR lekérdezés KF összegek:** bizonylatonként tételesen mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti az EPR díjösszeget.

**EPR lekérdezés KF súlyok cikkre csoportosítva:** cikkenkénti összesítésben mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti EPR súlyokat

**EPR lekérdezés KF összegek cikkre csoportosítva:** cikkenkénti összesítésben mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti EPR díj összegeket.

**EPR lekérdezés KF mindenösszesítve:** cikkenként összesítve mutatja az EPR súlyt, és az EPR díjösszeget.

<u><b><strong>2. CSK lekérdezések</strong></b></u>

**EPR lekérdezés CSK súlyok:** bizonylatonként tételesen mutatja az értékesítés mennyiségét, súlyát,CSK kódonkénti súlyokat.

**EPR lekérdezés CSK összegek:** bizonylatonként tételesen mutatja az értékesítés mennyiségét, súlyát, CSK kódonkénti a környezetvédelmi termékdíj összegét.

### Értékesítési lekérdezések

<u><b>1. KF lekérdezések</b></u>  

**EPR lekérdezés értékesítés KF súlyok**: bizonylatonként tételesen mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti EPR súlyokat. 

**EPR lekérdezés értékesítés KF összegek:** bizonylatonként tételesen mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti az EPR díjösszeget.

**EPR lekérdezés értékesítés KF súlyok cikkenként:** cikkenkénti összesítésben mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti EPR súlyokat

**EPR lekérdezés értékesítés KF összegek cikkenként:** cikkenkénti összesítésben mutatja az értékesítés mennyiségét, súlyát, KF kódonkénti EPR díj összegeket.

**EPR lekérdezés értékesítés KF súlyonként cikkenkét mindösszesen:**
 cikkenként összesítve mutatja az EPR súlyt, és az EPR díjösszeget.

**EPR lekérdezés értékesítés KF bevallás:** KF kódonként mutatja az
 EPR súlyokat (ezt kell a bevalláskor megadni)

**EPR - Ft/Kg díj:** cikkenként mutatja az 1 kg-ra eső EPR díj értékét

<u><b>2. CSK lekérdezések</b></u>  

**EPR lekérdezés értékesítés CSK súlyok:** bizonylatonként tételesen  mutatja az értékesítés mennyiségét, súlyát,CSK kódonkénti súlyokat.

**EPR lekérdezés értékesítés CSK  összegek:** bizonylatonként  tételesen mutatja az értékesítés mennyiségét, súlyát, CSK kódonkénti a környezetvédelmi termékdíj összegét.
