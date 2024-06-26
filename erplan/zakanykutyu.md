# Zákány komissió fejlesztés

## Táblák

### IFSZ_ALTMENU_SESSION

A kütyüs fejlesztésen belül ez az alappillére annak, hogy általános menüt tudjunk kezelni. Az általános menünél gyakorlatilag a menüpontba belépve minden lépés tárolt eljárásokkal történik, a képernyőn megjelenítést is tárolt eljárás vezérli.
Ahhoz, hogy a párhuzamosan futó folyamatok (két felhasználó is ugyanakkor lép be ugyanabba a menüpontba) el legyenek különítve egymástól, mindenki kap egy sessionid-t, ami ebből a táblából jön. Egy-egy bejelentkezésnek van itt egy-egy sora.
A menüpontba belépéskor a program kér egy új sort ebből a táblából, annak lesz egy id-ja, és később a menüpontból kilépésig ugyanezt a sessionid-t használja minden lépésnél. Innen tudja a program, hogy ez a session milyen státuszban van.

Bizonyos idő után automatikusan törlődnek innen a sorok. Egy egy napig folyamat közben letett kütyün nem lehet ugyanonnan folytatni a folyamatot, olyankor kilépteti a felhasználót.

| Oszlop | Leírás |
|:-------|:-------|
| ID | Egyedi kulcs automatikusan osztva, ez a sessionid |
| MENU | Melyik menüpontban vagyunk. Jelenleg kettő van: "KOMISSIO", "VEGELLENORZES" |
| USERID | A felhasználó azonosítója |
| KLIENSAZON | A backend által adott kliensazonosító, jelenleg nincs használva |
| TELEPHELY | A telephely |
| STATUSZ | A menüponton belül éppen melyik állapotban vagyunk |
| VISSZA_STATUSZ | Belső felhasználásra van, nem lineáris lépések során a vissza gomb hova térjen vissza |
| CREATED | Mikor indult ez a session (amikor belépett a felhasználó a menüpontba |
| LAST_UPDATED | Minden eseménynél ez frissül. Célja, hogy az 1 napja nem változott sessionöket törölhessük |

### IFSZ_ALTMENU_SESSION_VARS

Az IFSZ_ALTMENU_SESSION-höz tartozik, saját változókat lehet benne eltárolni, ami csakis az adott session-höz tartozik. Így a következő esemény során fel tudjuk használni ezt az értéket. Ezt a tárolt eljárásokban a
- IFSZ_SET_ALTMENU_SESSIONVAR_P eljárással lehet beállítani
- Az IFSZ_GET_ALTMENU_SESSION_STR_F, IFSZ_GET_ALTMENU_SESSION_NUM_F, IFSZ_GET_ALTMENU_SESSION_DAT_F függvényekkel lehet visszaszedni (típustól függ, hogy melyiket használjuk.)

| Oszlop | Leírás |
|:-------|:-------|
| ASN_ID | IFSZ_ALTMENU_SESSION.ID - sessionid |
| KOD | A változó neve - tetszőleges |
| ERTEK_STR | A változó értéke - amennyiben sztring |
| ERTEK_NUM | A változó értéke - szám |
| ERTEK_DAT | A változó értéke - dátum |

### IFSZ_SZEDOKOCSIK

A komissiózás során használt szedőkocsik vannak itt. Előre fel kell venni a szedőkocsikat, program automatikusan nem hoz létre újat. A kódja kezdődjön "SZK"-val.

| Oszlop | Leírás |
|:-------|:-------|
| ID | |
| AZONOSITO | SZK... |
| RKP_ID | Ha null, akkor nincs tárhelyen, mozgatható. Egyébként a csomagoló tárhelyre mutat, ahová betolták |
| USERID | Melyik felhasználó számára van lefoglalva. Null: senkinek |

### IFSZ_SZEDOHELYEK

A komissiózás során ebbe az egységbe történik a szedés. SZH-val kezdődik a kódja. A szedőhely vonalkód bekérésekor ha olyan SZH kódot adnak meg, ami még nem szerepelt ebben a táblában, akkor a program létrehozza azt.

| Oszlop | Leírás |
|:-------|:-------|
| ID | |
| AZONOSITO | SZH... |
| RKP_ID | A tárhely, ahova be lett téve. Ha szedőkocsin van, és a szedőkocsi került a tárhelyre, akkor ez null maradhat, de technikailag a szedőhely már tárhelyen van - csak közvetett módon |
| SZKI_ID | A szedőkocsi, amin ez rajta van. Lehetséges raklaposan szedni, ilyenkor a szedőhely nem kerül szedőkocsira |
| USERID | Raklapos szedésnél ez mondja meg, hogy mely felhasználónál van folyamatban ez a szedés |
| ORDR_DOCENTRY | Egy szedőhely szigorúan egy rendeléshez kapcsolódhat |
| STATUSZ | "N - Normál", "K - Kivezetve" A számlázáskor kerül kivezetésre |

### IFSZ_SZHLY_TETELEK

A szedőhely tartalmát mutatja.

| Oszlop | Leírás |
|:-------|:-------|
| ID | |
| SZHLY_ID | Melyik szedőhely |
| ITEMCODE | Cikkszám |
| SYSNUMBER | sarzs lenne, de nincs használva |
| MENNYISEG | Mennyiség |
| ORDR_DOCENTRY | Ugyanaz, ami a fejben van |
| LINENUM | A rendelés melyik tételére szedtük |
| SUBORDER | A foglalási tábla melyik altételére |
| RKP_ID_FROM | A tárhelyről leszedéskor az ifsz-es nyilvántartásban tényleg lekerül a tárhelyes készletről a kiszedett termék. (SBO-ban még nem) Itt utalunk arra, hogy honnan szedtük le, hogy az sbo-s áttároláskor a megfelelő helyről szedjük le.
| STATUSZ | "0": normál, "1": Ellenőrizve, "2": Kiszállítva |
| ELLENORZOTT_MENNYISEG | Ellenőrzött mennyiség |
| OINV_DOCENTRY | A létrehozott számla |

### IFSZ_SZEDES_RENDELESEI

A komissiózó felhasználó mely rendeléseket választotta ki komissiózásra. Ezeket más nem választhatja ki. Ha szedőkocsira szed, akkor az "SZKI_ID"-hoz rendeljük a vevői rendeléseket, amit szedni akar. Raklapos szedésnél az SZKI_ID nincs töltve, helyette a USERID van használva.

| Oszlop | Leírás |
|:-------|:-------|
| ID | |
| SZKI_ID | Szedőkocsi |
| USERID | Szedő felhasználó |
| ORDR_DOCENTRY | Rendelés |
| FOLYAMATBAN | "I/N" |

### IFSZ_SZEDES_JAVASLATOK

Ezek a rendelés tételek állapotba lépéskor ("RENDTETELEK") kalkulálódnak újra. A program ad egy javaslatot a szedésre. Másoknak ugyanezt a részét a készletnek már nem fogja felajánlani.

| Oszlop | Leírás |
|:-------|:-------|
| SZKI_ID | Szedőkocsi. Raklapos esetben -1 kerül bele |
| USERID | Melyik felhasználó. Raklapos esetben fontos |
| DOCENTRY | Rendelés |
| LINENUM | Tétel sorszám |
| SUBORDER | A foglalási tábla szerinti sor |
| RPC_ID | Melyik készletet javasolja a program - IFSZ_TH_RAKLAP_CIKKEI |
| MENNYISEG | Mekkora mennyiséget kell onnan szedni |

### IFSZ_KOM_ATTAROLAS_LOG_FEJ, IFSZ_KOM_ATTAROLAS_LOG_TETEL

A csomagolóhelyre történő "betoláskor" van szerepe ezeknek a táblának. Egy bejegyzést hoz létre a program, amiben benne van, hogy milyen szedőkocsit/szedőhelyet teszünk be a csomagoló területre. Az áttárolás bizonylat ez alapján fog létrejönni.

| IFSZ_KOM_ATTAROLAS_LOG_FEJ | Leírás |
|:---------------------------|:-------|
| ID | |
| FOLYAMATBAN | "0": Most lett bejegyezve, "1": Az ifsz-es tárhelyes nyilvántartásban át lett téve a készlet a csomagolóhelyre, és a szedőkocsi/szedőhely is, "2" Az SBO-s áttárolás is elkészült |
| DI_AZON | Az áttárolás docentry-je |

| IFSZ_KOM_ATTAROLAS_LOG_TETEL | Leírás |
|:-----------------------------|:-------|
| ID | |
| FEJ_ID | A fejre hivatkozik |
| SZKI_ID | Szedőkocsi |
| USERID | Felhasználó |
| SZHLY_ID | Szedőhely, amit "betolunk". Szedőkocsis esetben is felsoroljuk az azzal betolt szedőhelyeket. |
| ORDR_DOCENTRY | Melyik rendelésre |

## Tárolt eljárások

### IFSZ_CE_ALTMENU_INIT_P

Az általános menübe (jelenleg 5-ös és 8-as menüpont) belépéskor hívódik meg.
Feladata, hogy létrehozzon egy új bejegyzést az IFSZ_ALTMENU_SESSION táblában, és így osszon egy sessionid-t.
Ugyanakkor a visszatérési értékében definiálja azokat az adatokat is, ami az adott menüponton belül az egyes lépések során a gridek beállításához szükségesek. Tehát hány oszlopa lesz, ezek milyen fejléccel, milyen szélességben, milyen formázással hogyan lesznek elrendezve.

### IFSZ_CE_ALTMENU_PROCESS_P

Az általános menü lelke. A menüpontba belépés initje után, illetve később minden esemény kiváltódásakor meghívódik. Paraméterként a sessionid-t kapja, az esemény azonosítóját és a paramétert. Ez alapján dönti el a program, hogy mit kell tennie, milyen státuszba kell váltania, esetleg milyen egyéb adatbázis műveletet kell végrehajtania.

Esemény lehet:
- GombNyomas (technikailag csak az alsó sorban pluszban feltehető max. 2 vezérlő gombot kezeli)
- menu (ez is gombnyomás, csak a nagy, a képernyő közepén lévő gombokat kapja el)
- ErtekBeiras (Az input mezőbe beírt valamit)
- SorKivalaszt (A gridből kiválasztott egy sort)
- VezerloBillentyu ("vissza" gomb, esetleg emptyenter lehet)

A paraméter az eseménytől függhet:
- GombNyomas: "b_vez1", "b_vez2" lehet - melyik gombot nyomta meg.
- menu: "1", "2", stb. - melyik gombot nyomta meg.
- ErtekBeiras: Ami bekerült az input mezőbe
- SorKivalaszt: A kiválasztott sor. Ez azt jelenti, hogy az előző lépésben egy gridet mutattunk, ennek kellett, hogy legyen egy "PK" oszlopa. Ennek az értékét kapjuk itt meg.
- VezerloBillentyu: "back": Vissza gomb, "emptyenter": A beviteli mezőben csak egy entert nyomott.

Az eljárásnak a végén vissza kell adnia a képernyő megjelenítési adatait. Ez valójában ki lett szervezve az átláthatóság kedvéért az IFSZ_CE_ALTMENU_SCREEN_P eljárásba, ez utolsó lépésként meghívja azt.

### IFSZ_CE_ALTMENU_SCREEN_P

Visszaadja a megjelenítési adatokat. Részletesebben magában a tárolt eljárás kommentjében lehet tájékozódni.

### IFSZ_CE_ALTMENU_GRID_P

Az IFSZ_CE_ALTMENU_SCREEN_P megmondja, hogy kell-e grid-et megjelenítenünk, illetve a grid azonosítóját is megmondja. Ha van ilyen, akkor a program meghívja az IFSZ_CE_ALTMENU_GRID_P eljárást, ami státusztól függően visszaad egy eredményhalmazt, amit grid formában fog megjeleníteni a program.

Bármilyen oszlopnév szerepelhet benne, de fix oszlopok:
- PK: Ez egyedileg kell, hogy azonosítson egy sort. Kiválasztása után az IFSZ_CE_ALTMENU_PROCESS_P ezt az értéket fogja megkapni.
- ORD: A rendezési sorrend. Mindig ennek az oszlopnak az abc sorrendjében jelennek meg a képernyőn az adatok. (Nem feltétlenül egy order by-ban megadott sorrendben.)
- BETUSZURES: Nem kötelező benne lennie. De ha benne van, akkor a kütyü egy betű beírásakor azonnal szűkíti a listát azokra a sorokra, ami BETUSZURES oszlopában szerepel a beírt érték.

### IFSZ_SET_ALTMENU_SESSIONVAR_P, IFSZ_GET_ALTMENU_SESSION_STR_F, IFSZ_GET_ALTMENU_SESSION_NUM_F, IFSZ_GET_ALTMENU_SESSION_DAT_F

Ezeket használja a program a session változók beállításához, és lekérdezéséhez.

### IFSZ_GET_CE_SZAM_F

Segédfüggvény, a kütyübe beírt értéket értelmezi számként.

### IFSZ_CE_KOM_IGENYEK_TF

Visszaadja, hogy milyen igények vannak az adott szedőkocsira / userre.

### IFSZ_CE_KOM_JAVASLAT_FELTOLT_P

Ezt hívja meg a program a RENDTETELEK állapotba kerüléskor, feltölti az IFSZ_SZEDES_JAVASLATOK táblát.

## Folyamat

### Komissiózás (KOMISSIO) menüpont

| Státusz | Leírás |
|:--------|:-------|
| INIT | Csak technikai állapot, azonnal átvált KOM_FORRAS-ba |
| KOM_FORRAS | Itt lehet választani a forrásokból, a KOM_CEL állapotba kerül utána |
| KOM_CEL | Itt a  szállítási mód/portál variációkat lehet választani. Utána a SZEDŐKOCSI állapotba kerül, raklapos forrás esetén azonnal a RENDLISTA-ba |
| SZEDŐKOCSI | Be lehet vinni, vagy választani a szedőkocsit. A RENDLISTA állapotba kerül utána |
| RENDLISTA | A kiválasztott célnak megfelelő rendeléseket lehet választani. Kiválasztás után marad ebben a státuszban, de ha az első "Tovább"-ot választotta, akkor átkerül a RENDTETELEK-be. Itt bármikor szedőkocsit lelőve, vagy a "Betol" gombot megnyomva a BETOL_MODSZER állapotba kerül. Raklapos esetben (nem kell egyben/egyesével-t választani) azonnal a BETOL_SZHLISTA-ba |
| RENDTETELEK | A kiválasztott rendelés tételeit mutatja. Ha kiválasztotta, a VONALKODELL állapotba jutunk. Itt is elindíthatjuk a betolást. |
| VONALKODELL | Ha a megfelelő vonalkódot lövi le, akkor továbblép a KESZLETLISTA állapotba. És itt is elindíthatjuk a betoltás funkciót. |
| KESZLETLISTA | A kiválasztott cikk hol található meg, elöl van a javasolt. Kiválasztás után a MENNYISEG állapotba jutunk. És itt is elindíthatjuk a betoltás funkciót. |
| MENNYISEG | Be kell írni a mennyiséget, utána a SZEDŐHELY állapotba jutunk. És itt is elindíthatjuk a betoltás funkciót. |
| SZEDŐHELY | A szedőhelyre teszi a mennyiséget. Visszajutunk a RENDTETELEK állapotba. És itt is elindíthatjuk a betoltás funkciót. |
| BETOL_MODSZER | Ki kell választani, hogy egyben, vagy egyesével toljuk be a szedőkocsit. Egyben: BETOL állapotba jutunk, Egyesével: BETOL_SZHLISTA |
| BETOL_SZHLISTA | Listázza a szedőkocsin lévő, vagy raklapos esetben a felhasználónál lévő szedőhelyeket. Utána a BETOL állapotba jutunk |
| BETOL | Itt látjuk a választható csomagoló tárhelyeket. A kiválasztott szedőhelyet/szedőhelyeket/szedőkocsit az itt megadott tárhelyre tesszük. Ifsz nyilvántartásban is, és sbo-s áttárolás is létrejön. Ha sikeres, akkor visszatérünk a KOM_FORRAS állapotba |

### Végellenőrzés (VEGELLENORZES) menüpont

| Státusz | Leírás |
|:--------|:-------|
| INIT | Csak technikai állapot, azonnal átvált VEGELLENORZES-be |
| VEGELLENORZES | A rendeléseket listázzuk, választhat egyet, a VEGELL_TET állapotba jutunk |
| VEGELL_TET | A rendelés tételeit listázzuk, kiválasztva a MENNYISEG állapotba jutunk. Itt tudjuk megnyomni a "Számláz" gombot is, ami sikeres számla létrehozás után visszavisza a VEGELLENORZES állapotba |
| MENNYISEG | A beírt mennyiséget bejegyzi, mint ellenőrzött mennyiseg |

