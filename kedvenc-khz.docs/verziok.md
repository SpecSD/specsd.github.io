Éles verzió: [v1.0.12.9](#v1.0.12.9p)

Teszt verzió: [v1.0.13.6](#v1.0.13.6)

- v1.0.13.6<a name="v1.0.13.6">
  - Egyedi ár hibaüzenet javítás
- v1.0.13.5<a name="v1.0.13.5">
  - UK egyedi ár javítás
    - "Nem található megegyező ársor" hibaüzenet
	- 0 ár tiltása
- v1.0.13.4<a name="v1.0.13.4">
  - Cikk tulajdonságok form továbbfejleszése - excel betöltés
- v1.0.13.3
  - Egyedi ár UK jóváhagyó form
    - automatizmusok kezelése
- v1.0.13.2<a name="v1.0.13.2">
  - Cikk részletek form (Telesales mappa) {jegy: 22}
    - Cikk tulajdonságok form
	- Cikk tulajdonság csoportok form
	- Cikk információk form
  - Vevői rendelés form továbbfejlesztése (Telesales mappa)
  - Üzletkötői feladatok formon "/" jelet tartalmazó mező esetén előforduló hiba javítása {jegy: 72}
  - Sofőr kontaktok form {jegy: 75} (KKH fejlesztések menüpont)
- v1.0.13.1<a name="v1.0.13.1">
  - Ár jóváhagyás funkció lockolásos probléma megoldása
  - (v1.0.12.10-ben is:) Árazás: kezdődátum megegyezhet a záró dátummal
- v1.0.13.0<a name="v1.0.13.0t">
  - Hívólista form
    - Időnként előforduló lefagyásos hibaüzenetek megszüntetése
	- Már táblázat nézetben is láthatóak a korábbi napokhoz tartozó sorok, de módosítnai hozzáadni nem lehet
    - Kanban nézet frissul (megjelennek az új kártyák), ha sablonból betöltünk új sorokat
	- Kanban nézetben is lehet hozzáadni
	- Dátum mező egyszerűsített beírás működik (Pl. "0701" -> "2023.07.01")
  - Napi hívólista form
    - Hibaüzenetet kapunk, ha úgy akarunk hívást indítani hogy nincs kijelölve sor a partner listában (nincs kék színnel kiemelve)
    - Az eredmény oszlopra ha rávisszük az egeret tooltip megjeleníti a teljes üzenetet (akkor is ha az üzenet kifér)
    - A partner táblázatbeli ikon telefon ábra helyett dokumentumot ábrázol, jelezve, hogy itt nem fog történni valódi tárcsázás
    - Az "eredmény mezőt nem hagyhatja üresen" felirat hibájának javítása
    - Státusz megjelenítésének javítása
	- Kanban nézetben dátumváltásra előforduló lefagyás javítása
  - Új vevői rendelés form: A form kinézete, adatok beírása, kiválasztása tesztelhető - egyelőre még nem menti el adatbázisba
  - Szállítólevél nyomtatás
    - A formon ki lehet választani egy "Árukísérő nyomtató"-t is. Azoknak a vevőknek, akiknek ez be van állítva (U_SZLEV_NYOMT fho.mező), nem a másik nyomtatóra lesz elküldve a karakteres nyomtatású szállítólevél, hanem az "Árukísérő nyomtató"-ban kiválasztott nyomtatóra lesz elküldve egy grafikus formátumú árukísérő.
- v1.0.12.10
  - Árazás: kezdődátum megegyezhet a záró dátummal
- v1.0.12.9<a name="v1.0.12.9p">
  - Ár módosítások form
    - Szabad szavas keresés
	- Új ár beszúrása az ospp táblába
    - Új ár beszúrásánál a u_3x és u_arlistas oszlopok 'Y' illetve 'I'-re állítása
    - Érvénytelen partnerek és cikkek kihagyása
- v1.0.12.8<a name="v1.0.12.8p">
  - Üzletkötői rendelések: Meglévő rendelésre ráforgatásnál is tölti (módosítja) az U_FELHASZNALO felhasználói mezőt
  - Iktatás
    - Ha már korábban berögzített külső bizonylatszámot rögzít a felhasználó, felugró ablakban figyelmeztet
    - A tételekben a bizonylatok értéklista tartalmazza a devizás összeget és a pénznemet
  - Raktári leosztás form
    - kommissiozásra szűrés javítása.
    - Mennyiség mező szélességének a módosítása a jobban láthatóság érdekében
    - Kijelölt fej nélküli aktualizálás esetén hibára futott
  - Napi zárás: Gyorsabb betöltés
  - Napi zárás visszanyitás: Induláskor azonnal lekérdezi a mai napi adatokat.
  - Kihozatali csoportok form
  - Szállítólevél generálás formok
- [v1.0.12.7](kedvenc-khz-dok.v1.0.12.7.md) - éles<a name="v1.0.12.7p"></a>
  - Ügyvédi felszólítás:
    - Az elengedett státuszú felszólítást vissza lehet vonni.
    - Elengedéskor és visszavonáskor is kér okot, amit a megjegyzés oszlopba mentünk.
- [v1.0.12.6](kedvenc-khz-dok.v1.0.12.6.md) - éles<a name="v1.0.12.6p"></a>
  - Az ügyvédi felszólítás csatolt pdf-re rákerül maga az iktatószám.
  - Elengedéskor be kell írni egy okot, ami a megjegyzés mezőbe kerül. A megjegyzés mező megjelenik mindkét ügyvédi felszólítás formon.
  - Rendezetlen oszlop felkerül a formokra. (Érvényesítés után követhető, hogy még mennyi a tartozás.)
  - Excel lista generálás az ügyvédi felszólítás listából
  - Generált ügyvédi felszólítási díj számlán a fizetési feltétel a partner alapértelmezett fizetési feltétele, és a lejárat is ez alapján számolódik.
  - Az ügyvédi felszólítások formról indított frissítés során is újrakalkulálja a már korábban érvényesített felszólítások rendezettségi adatait.
  - Hibajavítás: Amint rendezetlen státuszba került a felszólítás, olyankor egy újat generált.
  - Kinnlevőség számoló algoritmus javítása (nem vette észre, hogy már volt 2. szintű felszólítás, amikor adminisztrációs számla is a képbe került.)
- v1.0.12.5 - éles<a name="v1.0.12.5p"></a>
  - Ügyvédi felszólitások lista menüpontban listázzuk az ügyvédi felszólításokat
  - Ügyvédi felszólítás form
    - Érvényesítés előtt kiválasztható, hogy generálunk-e számlát az ügyvédi felszólítási díjról.
	- Induláskor kiírt hibaüzenet javítása
	- Érvényesítés utáni után-követés: Rendezett, rendezetlen ügyvédi felszólítások
	- Átnavigálhatunk az ügyédi felszólítás listára (partner nevére kattintással)
  - SAP B1 kliens: Üzleti partnerek felületről jobbklikkel előhívható az "Ügyvédi felszólítások lista"
- v1.0.12.4 - éles<a name="v1.0.12.4p"></a>
  - Egyedi ár modul:
    - Engedélyezéssel kapcsolatos szabályok javítása
  - Üzletkötői rendelések beforgatása hibajavítás
- v1.0.12.3 - teszt<a name="v1.0.12.3"></a>
  - A riportok menüpont visszakerül a példa riportokkal, plusz két új: DataBar, és Dinamikus riportok
  - Az ügyvédi felszólítás érvényesítéskor most már pdf nyomtatási képet is készítése
  - Hívólista form:
    - dátum kiválasztáskori hiba javítása
	- kanban nézetben a felhasználók rendezése egy külső bug miatt egyelőre le van tiltva - így most nincs szabályozva, hogy a felhasználók milyen sorrendben jelennek meg.
  - Ár engedélyezés form hibára futott, ha nem volt vezetője a bejelentkezett felhasználónak
- [v1.0.12.2](kedvenc-khz-dok.v1.0.12.2.md) - teszt<a name="v1.0.12.2"></a>
  - Menüpontok átalakítása, csoportosítása
  - Új funkció: Rendelés leosztás form
  - Új funkció: Raktári leosztás formok
    - Gyöngyös szállítólevél rendelés
	- Bp. szállítólevél rendelés
	- Kecskemét szállítólevél rendelés
	- Kimérős leosztás
  - Új funkció: Különszedős beállítása form
  - Egyedi ár fejlesztés:
    - Cikk értéklista hozza azokat a cikkeket is, amire már volt egyedi ára a partnernek, de lejárt
    - Ha a partner kiválasztásnál megnyomjuk a mégse gombot a felugró ablakon, akkor nem kapunk hibát.
    - Form kinézetének javítása
    - Alapértelmezetten már a sorok holnapi dátum értékkel jönnek létre; hibajelzést adunk, ha a dátumtól mező értéke nagyobb mint a mai nap.
    - Engedélyezésre átadás üzenetküldése hibára futott korábban
  - Napi zárás "feldolgozás" gombja végrehajtja a rendelés zárását
  - Telesales hívólista látványos naptár nézetben (Kanban nézet) is meg tudja mutatni a teendőket.
  - Adminisztratív funkciók:
    - Ütemezési szintek, csoportok, email beállítások, címzettek hozzárendelése
	- Szerepek, jogosultságkezelés
	- Naptár karbantartó
- v1.0.12.1 - teszt<a name="v1.0.12.1"></a>
  - Egyedi ár menüpont:
    - Beszerzési ár már nem látható
    - Cikk értéklista nem hozza az olyan cikkeket, amikre jelenleg már van valamilyen egyedi ára a partnernek.
    - Minimál ár alatti ár esetén felmerült hibaüzenet javítása.
- [v1.0.12.0 - teszt](kedvenc-khz-dok.v1.0.12.0.md)<a name="v1.0.12.0"></a>
  - A NAV-tól betöltött bejövő számlákra készült egy megtekintő felület.
  - Az üzletkötői rendelések beforgatása a bizonylatfej felhasználói mezőjébe írja a tényleges felhasználó kódját. (U_FELHASZNALO. Technikailag a manager által jön létre a bizonylat, ezért nem lehetett tudni, ki hozta létre valójában.)
  - Az Email iktatások felületen most már megjelenítjük az "Aktuális összeg" mezőben fizetési felszólítás esetén az aznap lejáró összeget. (Ami eltérhet a teljes tartozás összegétől, mert korábbi tartozásai is lehetnek a partnernek.)
  - Az üzletkötői rendelések beforgatása formon a törlés gomb középre, olyan helyre került, ahol kisebb eséllyel lehet véletlenül megnyomni.
  - Telesales fejlesztés
    - Hívólista (hívólista összeállítása, sablonok betöltése)
	- Napi hívólista (Telefonhívás, tevékenység indítás a megadott hívólista alapján)
- v1.0.11.1 - teszt
  - Már módosítás nélkül is tudunk sorokat az "ár módosítások" táblába beszúrni.
  - Ügyvédi felszólitás menüpont - kinnlevőség IV-es ütem
    - Nyomtatási kép készítése, adminisztrációs díj számla generálása még hiányzik.
  - Az üzleti partnerek módosítása felületen egy progressbar mutatja a folyamat állapotát - nem fut időtúllépés hibára.
- [v1.0.6.8 - éles](kedvenc-khz-dok.v1.0.6.8.md)<a name="v1.0.6.8"></a>
  - Az üzleti partnerek módosítása form egyben lockolta a teljes folyamatot, ami több percig is tarthatott. Ez alatt más nem tudott SPCKhz-ből bizonylatot generálni. (Pl. iktatás)
  Most lépésenként lockol, ezért párhuzamosan, egymás mellett működni tudnak, nem kell megvárnia az összes partner módosítást, két partner módosítása között is megtörténhet egy iktatás.
  - 676/2020 megjegyzés módosítása a szállítólevélen az új kérésnek megfelelően (2023.02.02-i levél)
  - Az üzletkötői beforgatás olyankor nem találta meg a vevő korábbi SAP-s rendelését, ha egy menetben lett feldolgozva a vevő két külön rendelése.
- v1.0.6.7 - éles
  - Üzletkötői rendelések hibajavítás: többet nem lehetett kijelölni
  - AddOn csatlakozáskor ne az exe nevét (MasterDetailWinform) írja ki, hanem valóban az addon nevét: "SPCKhz AddOn".
- v1.0.6.6 - éles
  - Email iktatások felület jelenítse meg a végösszeget is.
  - Email iktatások link letöltés böngészőtől függ, hogy működik-e. Az "Insecure request" engedélyezését bekapcsoljuk, hogy nagyobb eséllyel engedje a böngésző a letöltést.
  - Minimár ár kalkuláció továbbfejlesztése: feltöltés - módosítás - véglegesítés.
  - Iktatásban a számkör kiválasztása a könyvelési dátumtól függ, sorrend átalakítása. Egyéb bugfix.
  - Iktatás szűrési feltételek fejlesztése - alapból kevesebb sor jelenjen meg.
  - Tr.notification módosítás: Számla nyomtatási kép készpénzt mutasson a sofőr modulból generált készpénzes számlák esetén is.
  - Üzletkötői rendelések: Depó alapján is lehet szűrni.
  - Üzletkötői rendelések bugfix: A szűrő legördülő listát ne lehessen kiüríteni, mert hibához vezet.
  - Napi zárás visszanyitás: nincs még ugyan használva, de ez már törli is a szállítólevél tervezeteket.
- v1.0.6.5 - éles
  - Szállítólevélen a 676/2020 szöveg módosítása.
- v1.0.6.4 - éles
  - Iktatás instabilitási problémák javítása
- v1.0.6.3 - éles
  - Iktatás: A táblázaton lévő szűrők használata esetén rossz sorra pozicionált, vagy hibára is futhatott.
- v1.0.6.2 - éles
  - A backend átalakítva a sofőr modulhoz hasonlóan. SAP DI API-hoz kapcsolódás módszere változott.
  - Iktatás: Célhely legördülő hibás értéket tartalmazott
- v1.0.6.1 - éles
  - Szállítólevélen a 676/2020 szöveg módosítása - nyilatkozzuk helyett tájékoztatjuk.
- v1.0.0.6 - éles
  - Nyomtatók karbantartása form
  - 676/2020-as fejlesztés
  - Az Üzletkötői feladatok fejlesztés az SPC_UK_FELADAT_SLPCODES táblát tölti.
- v1.0.0.5 - éles
  - Backend elérése az eddigi GET módszer helyett POST módszerrel történik.
  - Iktatás javítások. (Értéklisták)
  - Chat és üzenetek ablak bekerül a menübe
- v1.0.0.4 - éles
  - Kezdeti verzió, funkciók:
    - Változó minárak egyedi árai
    - Iktatás
    - Cikk információk
    - Minimál ár kalkuláció
    - ÜK értékesítési feladatok
    - Forcast betöltése
    - Szállítólevél nyomtatás
    - Napi zárás
    - Új ük rendelések beforgatás
    - Email iktatás
    - Üzleti partnerek módosítása
    - Rendelés visszanyitása
    - Domain-ek kezelése

- v1.0.12.4 - teszt<a name="v1.0.12.4t"></a>
  - Egyedi ár modul:
    - Engedélyezéssel kapcsolatos szabályok javítása
  - Üzletkötői rendelések beforgatása hibajavítás
- v1.0.12.3 - teszt<a name="v1.0.12.3"></a>
  - A riportok menüpont visszakerül a példa riportokkal, plusz két új: DataBar, és Dinamikus riportok
  - Az ügyvédi felszólítás érvényesítéskor most már pdf nyomtatási képet is készítése
  - Hívólista form:
    - dátum kiválasztáskori hiba javítása
	- kanban nézetben a felhasználók rendezése egy külső bug miatt egyelőre le van tiltva - így most nincs szabályozva, hogy a felhasználók milyen sorrendben jelennek meg.
  - Ár engedélyezés form hibára futott, ha nem volt vezetője a bejelentkezett felhasználónak
- [v1.0.12.2](kedvenc-khz-dok.v1.0.12.2.md) - teszt<a name="v1.0.12.2"></a>
  - Menüpontok átalakítása, csoportosítása
  - Új funkció: Rendelés leosztás form
  - Új funkció: Raktári leosztás formok
    - Gyöngyös szállítólevél rendelés
	- Bp. szállítólevél rendelés
	- Kecskemét szállítólevél rendelés
	- Kimérős leosztás
  - Új funkció: Különszedős beállítása form
  - Egyedi ár fejlesztés:
    - Cikk értéklista hozza azokat a cikkeket is, amire már volt egyedi ára a partnernek, de lejárt
    - Ha a partner kiválasztásnál megnyomjuk a mégse gombot a felugró ablakon, akkor nem kapunk hibát.
    - Form kinézetének javítása
    - Alapértelmezetten már a sorok holnapi dátum értékkel jönnek létre; hibajelzést adunk, ha a dátumtól mező értéke nagyobb mint a mai nap.
    - Engedélyezésre átadás üzenetküldése hibára futott korábban
  - Napi zárás "feldolgozás" gombja végrehajtja a rendelés zárását
  - Telesales hívólista látványos naptár nézetben (Kanban nézet) is meg tudja mutatni a teendőket.
  - Adminisztratív funkciók:
    - Ütemezési szintek, csoportok, email beállítások, címzettek hozzárendelése
	- Szerepek, jogosultságkezelés
	- Naptár karbantartó
- v1.0.12.1 - teszt<a name="v1.0.12.1"></a>
  - Egyedi ár menüpont:
    - Beszerzési ár már nem látható
    - Cikk értéklista nem hozza az olyan cikkeket, amikre jelenleg már van valamilyen egyedi ára a partnernek.
    - Minimál ár alatti ár esetén felmerült hibaüzenet javítása.
- [v1.0.12.0 - teszt](kedvenc-khz-dok.v1.0.12.0.md)<a name="v1.0.12.0"></a>
  - A NAV-tól betöltött bejövő számlákra készült egy megtekintő felület.
  - Az üzletkötői rendelések beforgatása a bizonylatfej felhasználói mezőjébe írja a tényleges felhasználó kódját. (U_FELHASZNALO. Technikailag a manager által jön létre a bizonylat, ezért nem lehetett tudni, ki hozta létre valójában.)
  - Az Email iktatások felületen most már megjelenítjük az "Aktuális összeg" mezőben fizetési felszólítás esetén az aznap lejáró összeget. (Ami eltérhet a teljes tartozás összegétől, mert korábbi tartozásai is lehetnek a partnernek.)
  - Az üzletkötői rendelések beforgatása formon a törlés gomb középre, olyan helyre került, ahol kisebb eséllyel lehet véletlenül megnyomni.
  - Telesales fejlesztés
    - Hívólista (hívólista összeállítása, sablonok betöltése)
	- Napi hívólista (Telefonhívás, tevékenység indítás a megadott hívólista alapján)
- v1.0.11.1 - teszt
  - Már módosítás nélkül is tudunk sorokat az "ár módosítások" táblába beszúrni.
  - Ügyvédi felszólitás menüpont - kinnlevőség IV-es ütem
    - Nyomtatási kép készítése, adminisztrációs díj számla generálása még hiányzik.
  - Az üzleti partnerek módosítása felületen egy progressbar mutatja a folyamat állapotát - nem fut időtúllépés hibára.
  - Az üzletkötői beforgatás olyankor nem találta meg a vevő korábbi SAP-s rendelését, ha egy menetben lett feldolgozva a vevő két külön rendelése. (1.0.6.8-ban történt változtatás)
- v1.0.11.0 - teszt
  - Minden, amit a v1.0.6.6-os verzió is tartalmaz, plusz:
  - Szám billentyűzet jöjjön fel az egységárnál androidon
  - Tranzakciókezelés átalakítva (korábbi megoldás problémás lehet bizonyos helyzetekben)
- v1.0.8.0 - teszt
  - Androidra alakítás
  - Ugyanaz a programkód bázis, de kettéválasztva: lehet olyan változata, ami csak az árazásos menüpontokat tartalmazza
- v1.0.7.0 - teszt
  - A v1.0.0.6-os verziót és azon kívül a következőket tartalmazza:
  - Árazás fejlesztés
  - Ár engedélyezés
  - Frissített keretrendszer
  - Üzenet, chat

## Telepítési végpontok

| Végpont | Leírás |
|:--------|:-------|
| Éles backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\khz_eles_backend IIS: http://192.168.20.162:4102 Db: JEGSBO2/KHAZ_PROD |
| Éles frontend | Útvonal: \\\\192.168.20.162\\c$\\spc\\khz_eles_frontend IIS: https://192.168.20.162:7172 |
| Éles AddOn | Útvonal: \\\\192.168.20.162\\c$\\spc\\spc_addon_khz Addon neve: spc_addon_khz |
| Éles android apk | [Letölthető](../kedvenc.md) |
| Éles egyedi ár modul apk | [Letölthető](../kedvenc.md) |
| Teszt backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\khz_teszt_backend IIS: http://192.168.20.162:4009 Db: JEGSBO2/TESZT_KHAZ_UJ |
| Teszt frontend | Útvonal: \\\\192.168.20.162\\c$\\spc\\khz_teszt_frontend IIS: https://192.168.20.162:7079 |
| Teszt AddOn | Útvonal: \\\\192.168.20.162\\c$\\spc\\spc_addon_khz_teszt Addon neve: TESZTspc_addon_khz |
| Teszt android apk | [Letölthető](../kedvenc.md) |
| Teszt egyedi ár modul apk | [Letölthető](../kedvenc.md) |
| Árazáshoz éles backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\kedvencar_eles_backend IIS: http://192.168.20.162:4103 Db: JEGSBO2/KHAZ_PROD (Mivel élesben lehet csak tesztelni, viszont az éles backendet nem lehet jelenleg felülvágni) |
| KedvencInformatika backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\kinf_khz_backend IIS: http://192.168.20.162:4105 Db: JEGSBO2/KEDVENC_INFORMATIKA |
| KedvencInformatika frontend | Útvonal: \\\\192.168.20.162\\c$\\spc\\kinf_khz_frontend IIS: https://192.168.20.162:7175 |
| Nokoro backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\nokoro_khz_backend IIS: http://192.168.20.162:4106 Db: JEGSBO2/NOKORO |
| Nokoro frontend | Útvonal: \\\\192.168.20.162\\c$\\spc\\nokoro_khz_frontend IIS: https://192.168.20.162:7176 |
  
## Telepítési napló

| Verzió | Végpont | Telepítve |
|:-------|:--------|:----------|
| 1.0.13.6 | Éles egyedi ár modul apk | 2023.10.16 |
| 1.0.13.6 | Árazáshoz éles backend | 2023.10.16 |
| 1.0.13.5 | Árazáshoz éles backend | 2023.10.06 |
| 1.0.13.4 | Teszt backend  | 2023.10.05 |
| 1.0.13.4 | Teszt frontend | 2023.10.05 |
| 1.0.13.3 | Éles egyedi ár modul apk  | 2023.10.03 |
| 1.0.13.3 | Árazáshoz éles backend | 2023.10.03 |
| 1.0.13.2 | Teszt backend  | 2023.09.23 |
| 1.0.13.2 | Teszt frontend | 2023.09.23 |
| 1.0.13.1 | Éles egyedi ár modul apk  | 2023.09.22 |
| 1.0.13.1 | Árazáshoz éles backend | 2023.09.22 |
| 1.0.12.10 | Árazáshoz éles backend | 2023.09.18 |
| 1.0.13.0 | Nokoro backend  | 2023.09.06 |
| 1.0.13.0 | Nokoro frontend | 2023.09.06 |
| 1.0.13.0 | KedvencInformatika backend  | 2023.09.06 |
| 1.0.13.0 | KedvencInformatika frontend | 2023.09.06 |
| 1.0.13.0 | Teszt backend  | 2023.09.06 |
| 1.0.13.0 | Teszt frontend | 2023.09.06 |
| 1.0.12.9 | Éles egyedi ár modul apk  | 2023.09.05 |
| 1.0.12.9 | Árazáshoz éles backend | 2023.09.05 |
| 1.0.12.9 | Éles backend  | 2023.09.05 |
| 1.0.12.9 | Éles frontend | 2023.09.05 |
| 1.0.12.8 | Éles backend  | 2023.09.03 |
| 1.0.12.8 | Éles frontend | 2023.09.03 |
| 1.0.12.7 | Éles backend  | 2023.08.18 |
| 1.0.12.7 | Éles frontend | 2023.08.18 |
| 1.0.12.6 | Éles backend  | 2023.07.25 |
| 1.0.12.6 | Éles frontend | 2023.07.25 |
| 1.0.12.6 | Teszt backend  | 2023.07.25 |
| 1.0.12.6 | Teszt frontend | 2023.07.25 |
| 1.0.12.5 | Éles backend  | 2023.07.03 |
| 1.0.12.5 | Éles frontend | 2023.07.03 |
| 1.0.12.5 | Teszt backend  | 2023.07.03 |
| 1.0.12.5 | Teszt frontend | 2023.07.03 |
| 1.0.12.4 | Éles backend  | 2023.06.06 |
| 1.0.12.4 | Éles frontend | 2023.06.06 |
| 1.0.12.4 | Éles AddOn    | 2023.06.06 |
| 1.0.12.4 | Éles egyedi ár modul apk  | 2023.05.31 |
| 1.0.12.4 | Teszt egyedi ár modul apk | 2023.05.31 |
| 1.0.12.4 | Árazáshoz éles backend    | 2023.05.31 |
| 1.0.12.4 | Teszt frontend            | 2023.05.31 |
| 1.0.12.4 | Teszt backend             | 2023.05.31 |
| 1.0.12.3 | Teszt frontend | 2023.05.17 |
| 1.0.12.3 | Teszt backend  | 2023.05.17 |
| 1.0.12.2 | Éles egyedi ár modul apk  | 2023.05.09 |
| 1.0.12.2 | Teszt egyedi ár modul apk | 2023.05.09 |
| 1.0.12.2 | Árazáshoz éles backend | 2023.05.09 |
| 1.0.12.2 | Teszt frontend | 2023.05.09 |
| 1.0.12.2 | Teszt backend  | 2023.05.09 |
| 1.0.12.1 | Éles egyedi ár modul apk | 2023.05.04 |
| 1.0.12.1 | Teszt egyedi ár modul apk | 2023.05.04 |
| 1.0.12.1 | Teszt AddOn | 2023.05.02 |
| 1.0.12.1 | Árazáshoz éles backend (teszt addonnal való használathoz) | 2023.05.02 |
| 1.0.12.1 | Teszt frontend | 2023.03.29 |
| 1.0.12.1 | Teszt backend  | 2023.03.29 |
| 1.0.12.0 | Teszt frontend | 2023.03.07 |
| 1.0.12.0 | Teszt backend  | 2023.03.07 |
| 1.0.11.1 | Éles egyedi ár modul apk | 2023.02.27 |
| 1.0.11.1 | Teszt egyedi ár modul apk | 2023.02.27 |
| 1.0.11.1 | Teszt frontend | 2023.02.27 |
| 1.0.11.1 | Teszt backend | 2023.02.27 |
| 1.0.11.1 | Árazáshoz éles backend | 2023.02.27 |
| 1.0.6.8  | Éles backend | 2023.02.16 |
| 1.0.6.8  | Éles frontend | 2023.02.16 |
| 1.0.11.0 | Teszt frontend | 2023.02.06 |
| 1.0.11.0 | Teszt backend | 2023.02.06 |
| 1.0.11.0 | Árazáshoz éles backend | 2023.02.06 |
| 1.0.6.7  | Éles AddOn | 2023.01.23 |
| 1.0.6.6  | Éles backend | 2023.01.09 |
| 1.0.6.6  | Éles frontend | 2023.01.09 |
| 1.0.6.6  | Éles AddOn | 2023.01.09 |
| 1.0.6.5  | Éles backend | 2022.12.05 |
| 1.0.8.0  | Teszt frontend | 2022.11.22 |
| 1.0.8.0  | Teszt backend | 2022.11.22 |
| 1.0.8.0  | Árazáshoz éles backend | 2022.11.22 |
| 1.0.6.4  | Éles AddOn | 2022.11.16 |
| 1.0.6.3  | Éles AddOn | 2022.11.15 |
| 1.0.7.0  | Teszt frontend | 2022.11.15 |
| 1.0.7.0  | Teszt backend | 2022.11.15 |
| 1.0.6.2  | Éles backend | 2022.11.14 |
| 1.0.6.1  | Éles backend | 2022.11.07 |
| 1.0.0.6  | Éles frontend | 2022.10.29 |
| 1.0.0.6  | Éles backend | 2022.10.29 |
| 1.0.0.6  | Teszt frontend | 2022.10.24 |
| 1.0.0.6  | Teszt backend  | 2022.10.24 |
| 1.0.0.5  | Éles AddOn     | 2022.10.24 |
| 1.0.0.5  | Éles frontend  | 2022.10.24 |
| 1.0.0.5  | Éles backend   | 2022.10.24 |
| 1.0.0.5  | Teszt frontend | 2022.10.24 |
| 1.0.0.5  | Teszt backend  | 2022.10.24 |
| 1.0.0.5  | Éles AddOn     | 2022.10.24 |
| 1.0.0.5  | Éles AddOn     | 2022.10.24 |
| 1.0.0.4  | Éles frontend  | 2022.09.26 |
| 1.0.0.4  | Éles backend   | 2022.09.26 |
| 1.0.0.4  | Éles AddOn     | 2022.09.26 |
