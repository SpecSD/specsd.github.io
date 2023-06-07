# Sofőr modul - SPCSofor

A fejlesztés célja, hogy az SAP Business One-ban előkészített, és túra jelleggel végrehajtott árukiszállítások adminisztrálását, elszámolását felgyorsítsa, megkönnyítse.

Bár az SPCSofor modul multiplatformos fejlesztés, egy böngészőben is elérhető (amennyiben ez a végpont be van állítva), és használható, de jellemzően az androidos alkalmazásként telepített formáját használjuk.
Az alkalmazást egy android tabletre telepítjük, ezt a tabletet a sofőr magával viszi, és itt ellenőrzi, és ide rögzíti be a vevő számára ténylegesen átadott áru mennyiségét, szavatossági idejét, és egyéb jellemzőit. Az alkalmazás online kapcsolatban van az SAP Business One adatbázisával, és friss adatokat mutat, valamint véglegesítéskor azonnal el is készíti a szükséges bizonylatokat.

Az androidos táblagéphez kapcsolható Brother PJ762 típusú bluetooth-os hőnyomtató, amit az alkalmazás közvetlenül tud használni, és ide nyomtatja a szállítólevél, számla bizonylatokat.

---------------------------------------------------------
## Telepítés

Android táblagépre történő telepítése a megfelelő apk telepítő csomag letöltésével, és annak futtatásával történik. A sikeres telepítés után az alkalmazások között megtaláljuk a programot.

Két változata van:
- SPCSofor
- SPCSoforTeszt

Az első az éles verzió, a másodikat akkor használjuk, ha egy új változtatást, módosítást első körben le akarunk tesztelni.

Az apk letöltéséhez megadjuk a letöltési útvonalat, amit a táblagépen egy böngészőbe lehet beírni. Illetve a weboldalon, ahonnan ez letölthető, ott egy qr kód is rendelkezésre áll, ezért megnyithatjuk egy pc-n, és a táblagéppel csak le kell fényképeznünk a qr kódot a letöltéshez.


---------------------------------------------------------
## Bejelentkezés - főképernyő

A program indítása után a bejelentkező ablak fogad, ahol három adatot kell megadnunk:
- Szállítási nap: Ide írjuk be, vagy válasszuk ki a szállítási napot. (Beírva a dátumot egyszerüsíthetünk, pl.: `0101` január 1-et jelent.
- Túrakód: Ide írjuk be a túra kódját.
- Jelszó: Ide egyelőre nem kell írnunk semmit, de a későbbiekben valamilyen titkos jelszót lehet majd kötni az egyes túrákhoz.

Alul a "Login" gombra kattintva tudunk belépni a főképernyőre. Ha olyan szállítási nap/túrakódot adtunk meg, ami létezik a rendszerben, akkor továbbenged, egyébként nem.

### Főképernyő

Sikeres bejelentkezés után a főképernyőre jutunk. Ennek a felső sávja minden pillanatban a következő elemeket tartalmazza:
- Hamburgermenü ikon: Erre kattintva jön fel, vagy tűnik el a bal oldali oldalmenü, ahol az egyes menüpontok láthatóak.
- Cím: Ez tartalmazza a program nevét, verziószámát, az éppen aktuális képernyő nevét, valamint a túra napját / kódját.
- Másik túra választása: Ezzel a jobb oldalon lévő ikonnal tudunk kilépni az adott túrából, és visszalépünk a bejelentkező ablakra.

### Oldalmenü

Itt vannak felsorolva az alkalmazás menüpontjai:
- Kezdőlap: Induláskor is ide jutunk, itt láthatjuk a túra összefoglaló adatait.
- Nyitott szállítólevelek: Erre kattintva tudjuk megnézni a rendszerben lévő, az adott túrához tartozó nyitott bizonylatokat.
- Lezárt szállítólevelek: Erre kattintva a túra már bezárt bizonylatait láthatjuk.

### Kezdőlap

A kezdőlapon a túra adatait láthatjuk, valamit táblázatos formában az összegszerű összesítő adatokat:

|   | Nyitott | Zárt |
|---|---------|------|
| Átutalásos | Összesítve a még nyitott kiszállítások, amik átutalásos fizetési módúak | A már lezárt átutalásos kiszállítások |
| Készpénzes  | Összesítve a még nyitott kiszállítások, amik készpénzesek | A már lezárt készpénzes kiszállítások |
| Bankkártyás | Összesítve a még nyitott kiszállítások, amik bankkártyával lettek fizetve | A már lezárt bankkártyás kiszállítások |

Ez a képernyő használható arra, hogy folyamatában lehessen látni a még nyitott összegeket, illetve a túra befejezésekor a sofőrrel történő elszámoláshoz szolgáltatnak információt.

Az összegek mindig a bizonylat pénznemében jelennek meg. Ha egy túrán belül vegyesen szerepelnek különböző pénznemű kiszállítások, akkor minden érintett pénznemre külön jelennek meg a fenti információk. Vagyis ha egy túrában forintos és eurós szállításaink is vannak, akkor 3 sor helyett 6 sort fogunk látni.




---------------------------------------------------------
## Nyitott és zárt bizonylatok

Ezeken a képernyőkön a kiszállítási bizonylatok jelennek meg listaszerűen, a kiszállítás sorrendjében (boltsorrend) felsorolva. Itt nem módosíthatunk semmit, viszont bármelyik sorra rákkatintva megnyílik az adott bizonylat részletező ablaka, ahol az azzal kapcsolatos műveleteket elvégezhetjük.

A nyitott menüpont mindig az aktuális, SAP Business One-ban nyitott szállítóleveleket mutatja.

A Lezárt menüpont mindig az aktuális, SAP Business One-ban a **sofőr modul segítségével** lezárt szállítóleveleket mutatja. Emiatt ha valamelyik szállítólevelet az SAP Business One-ban zárják le, az egyik nézetben sem fog látszódni.


---------------------------------------------------------
## Bizonylatok módosítása

### A képernyő felépítése

#### Felső gombsor

- Vissza (<=) gomb: Ezzel vissza tudunk lépni a bizonylatokat listázó képernyőre.
- Aktualizál: A bizonylaton végzett módosításainkat menteni tudjuk, de ez még nem hat vissza az SAP Business One bizonylataira. Viszont ha kilépünk, visszalépünk, akkor az utoljára mentett állapotot fogjuk látni.
- Új cikk: Ennek a gombnak a megnyomásával új cikket vehetünk fel a bizonylatra.
- Véglegesít: Ezzel tudjuk véglegesíteni a módosításainkat. Amennyiben szállítólevelet, visszárut, vagy számlát kell létrehozni, az létrejön az SAP Business One-ban. A bizonylat lezárásra kerül, innen kezdve nem módosítható. Egy pdf nyomtatási kép generálódik, amit ki lehet nyomtatni, vagy el lehet küldeni emailben az ügyfélnek. Amennyiben "PÉNZÜGY" tárgyalópartner email cím van beállítva az adott partnernek, akkor erre az email címre a program elküldi a pdf-et.
- Száll.levél/számla nyomtatási kép: Ez a gomb csak véglegesítés után látszik. Erre nyomva megtekinthetjük a generált pdf-et.
- Nyomtatás: Ez a gomb csak véglegesítés után látszik. Ez a bluetooth-on csatolt nyomtatóra elküldi a pdf-et.
- Email küld: Ez a gomb csak véglegesítés után látszik. Ezzel a partner megadott email címére elküldjük a pdf-et. (Ez automatikusan is megtörténik, de itt akár utólag újra el lehet küldeni.)

#### Bizonylat fej

Az adott kiszállításnak a fej adatait látjuk itt.

| Mező | Leírás |
|------|--------|
| Bizonylatszám | A kiszállítás SAP-beli bizonylatszáma |
| Partnernév | |
| Cím | |
| Szállítási dátum | |
| Fizetési mód | Átutalásos - készpénzes - bankkártyás. Ebben a blokkban ez az egyetlen módosítható mező. De csak addig, amíg nincs lezárva a bizonylat |
| Bruttó, nettó, áfa | Mindig a bizonylat pénznemében értendőek az értékek. |

#### Bizonylat tétel

Az adott kiszállítás tétel adatait látjuk.

| Mező | Leírás |
|------|--------|
| Cikkszám | Nem módosítható, viszont új sort lehet felvenni az "Új cikk" nyomógombbal |
| Cikknév | Nem módosítható |
| Mennyiség | A rendszer szerinti kiszállított mennyiség az adott tételsoron. Amennyiben a ténylegesen átvett mennyiség ettől eltér, akkor itt meg lehet módosítani. Módosítás esetén azonban a sor végén lévő hibakódot mindenképpen meg kell adni. |
| Egységár | A rendszerből jön, nem módosítható |
| Nettó, bruttó, áfa | A tételsor számolt adatai |
| Szavidő | A szavatossági időt kell megadni. A program előhűtött termékek esetén megköveteli ennek megadását, egyéb esetben is javasolja, hogy töltsük. |
| Megjegyzés | Tetszőleges tétel szintű megjegyzést adhatunk |
| Hibakód | Értéklistából választható. Ezzel tudjuk jelezni, hogy mi miatt változott a mennyiség az eredetihez képest |

#### Működés

Az ezen a formon végrehajtott változtatásink az "Aktualizál" gombbal kerülnek az adatbázisba mentésre. Ezeket a változásokat kifejezetten csak a sofőr modul kezeli, egészen addig átmenetinek tekinthető, amíg a véglegesítés meg nem történik.

A "Véglegesít" gombra nyomva záródik be a bizonylat. Egyúttal a módosított mennyiségek, egyéb információk is bekerülnek az SAP Business One-ba. A partnertől függ, hogy szállítólevél, visszáru, és/vagy számla készül a bizonylatból.


