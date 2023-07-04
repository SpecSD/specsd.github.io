# SPCSofor verziók

- v1.0.12.0
  - A számolt értékek újraszámolódnak véglegesítés előtt - azért, mert néha a felvitel során ezek eltérést tudnak mutatni.
- [v1.0.11.0](kedvenc-sofor-dok.v1.0.11.0.md) - teszt
  - Forinttól eltérő pénznemek kezelése
- [v1.0.10.0](kedvenc-sofor-dok.v1.0.10.0.md) - teszt
  - Adatbázis kapcsolati hiba miatt ritkán előfordul, hogy a bizonylat fejet letölti, de a tételeit nem. Ezentúl ha ilyen történik, a következő megnyitásnál újra megpróbálja letölteni a tételeket.
  - Véglegesítéskor automatikusan kiküldi a pdf-et emailben - amennyiben be van állítva a vevő email címe.
  - A bizonylat megtekintőből a "<-" gomb mindig a nyitott bizonylatok listájára lépett vissza. Most ha a zárt listából érkeztünk, akkor oda is lép vissza.
  - A  nyomógombok új, szebb kinézetet kaptak.
  - A "Véglegesít" nyomógomb csak részben inaktiválódik, ha már megtörtént a bizonylat véglegesítése. Az alap kék szín helyett sötétszürke hátteret kap. Ha erre duplán kattintunk, akkor a nyomtatási kép generálása újra megtörténik.
    Erre azért volt szükség, mert időnként az elkészült bizonylat üres, tartalom nélkül készül el. Ha ilyet tapasztalunk, a duplaklikkeléssel újra tudjuk generáltatni a nyomtatási képet - második alkalommal már minden bizonnyal jó eredményt kapunk.
- v1.0.9.2 - éles
  - A feldolgozva státuszt nem lehet módosítani a képernyőről történő aktualizálással. (Ha esetleg képernyőn maradna megnyitva egy korábbi állapot.)
  - Párhuzamos folyamatok kezelésének fejlesztése, ne akadhassanak össze egymással.
- v1.0.9.1 - éles
  - Ha átutalásost készpénzesre módosítana, ne engedje.
  - email bcc-be: ;kedvencuk@gmail.com is
  - Tranzakciókezelés, összeakadásos probléma javítása, további logolás
- v1.0.9.0 - éles
  - Brother nyomtató elérése közvetlenül, arra nyomtatás
  - Számla, szállítólevél megtekintése az android alapértelmezett programjával
- v1.0.0.8 - éles
  - A "Nyomtatási kép" nyomógomb felirata már utal a típusra: szállítólevél / számla
  - Csökkentés esetén kötelező a hibakód töltése
  - Nyomtatva, példányszám beírása az SAP-s számlába, hogy a sofőr modulból történő nyomtatás esetén is lehessen látni, hogy már nyomtatva lett a számla.
  - email bcc
  - A SAP DI API-hoz kapcsolódás módszere változott.
  - Emailküldés lokális smtp szerver használatával és html tartalommal
  - A crystal nyomtatás egy különálló szolgáltatás segítségével készül el. (Sebesség kérdés miatt - gyorsabb, mint a parancssori.)
- v1.0.0.7.1 - éles
  - Számkörök beállítása depónak megfelelően
- v1.0.0.7 - éles
  - Új cikk hozzáadás hiba javítása. (Rossz mértékegység)
- v1.0.0.6 - éles
  - Logolunk minél több dolgot
  - SAP DI API kapcsolat tuningolása.
  - Emailben is lehet küldeni a pdf-et.
  - EH szavidő mégis kötelező
  - Crystal nyomtatás az 1.0.0.2-es verziószámú spccry parancssori programmal.
- v1.0.0.5 - éles
  - Mértékegység megjelenítése
  - Belső szekvencia módosítása
- v1.0.0.4 - éles
  - Szavidő hiányra figyelmeztetés
  - Homokóra (spinner) fejlesztések
- v1.0.0.3 - éles
  - Az esetleges szállítólevél, visszáru, számla nem egy tranzakcióban jön létre, hanem mindegyik külön. Ha megszakadna, akkor is tudja, hogy következő alkalommal, ha rányomnak a gombra, honnan folytassa, és melyiket hagyja ki.
  - 54-es partner tulajdonság: a számla ettől függ, hogy számlás-e
  - A számlán a megjegyzés mezőbe kézzel belekerül, hogy forrása szállítólevél...
  - Nem kötelező a szavidő
  - Készpénzes, bankkártyás esetben a fizetés elkészítése. Előtte a számlán más fizetési feltételt használunk, és utólag visszaállítjuk. (SAP ellenőrzés kikerülése miatt.)
  - Sor tördelése szavak mentén: mindhárom form gridjeiben
  - A sofdocm-ben a felső részt is kicsit összébb hoztam, így két sorban elfér.
  - A tételek ugyanúgy rendeződnek, ahogy a nyomtatáson is.
  - Új cikk hozzáadása a sorrend végére kerül.
- v1.0.0.2 - éles
  - Első jól használható éles változat.

## Telepítési végpontok

| Végpont | Leírás |
|:--------|:-------|
| Éles backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\khz_eles_sofor_backend IIS: http://192.168.20.162:4104 v1.0.12.0 előtt: http://192.168.20.162:4100 Db: JEGSBO2/KHAZ_PROD |
| Éles android apk | [Letölthető](../kedvenc.md) |
| Teszt backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\khz_teszt2_sofor_backend IIS: http://192.168.20.162:4101 Db: JEGSBO2/TESZT_KHAZ_UJ |
| Teszt android apk | [Letölthető](../kedvenc.md) |
  
## Telepítési napló

| Verzió | Végpont | Telepítve |
|:-------|:--------|:----------|
| 1.0.12.0 | Éles android apk | 2023.07.04 |
| 1.0.12.0 | Éles backend     | 2023.07.04 |
| 1.0.11.0 | Teszt android apk | 2023.06.07 |
| 1.0.11.0 | Teszt backend     | 2023.06.07 |
| 1.0.10.0 | Teszt android apk | 2023.05.26 |
| 1.0.10.0 | Teszt backend | 2023.05.26 |
| 1.0.9.2  | Éles backend | 2022.11.21 |
| 1.0.9.1  | Éles backend | 2022.11.04 |
| 1.0.9.1  | Teszt backend | 2022.11.04 |
| 1.0.9.0  | Éles backend | 2022.10.20 |
| 1.0.9.0  | Teszt backend | 2022.10.20 |
| 1.0.9.0  | Éles android apk | 2022.10.20 |
| 1.0.8.0  | Éles backend | 2022.10.14 |
| 1.0.8.0  | Éles android apk | 2022.10.14 |
| 1.0.7.1  | Éles backend | 2022.10.12 |
| 1.0.7.1  | Teszt backend | 2022.10.12 |
| 1.0.0.7  | Éles android apk | 2022.10.07 |
| 1.0.0.7  | Éles backend | 2022.10.04 |
| 1.0.0.7  | Teszt backend | 2022.10.04 |
| 1.0.0.6  | Éles android apk | 2022.10.02 |
| 1.0.0.5  | Éles android apk | 2022.09.26 |
| 1.0.0.4  | Éles android apk | 2022.09.20 |
| 1.0.0.3  | Éles backend | 2022.09.15 |
| 1.0.0.3  | Teszt backend | 2022.09.15 |
| 1.0.0.3  | Éles android apk | 2022.09.15 |
| 1.0.0.2  | Éles backend | 2022.09.14 |
| 1.0.0.2  | Teszt backend | 2022.09.14 |
| 1.0.0.2  | Éles android apk | 2022.09.14 |
