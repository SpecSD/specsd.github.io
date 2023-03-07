Éles verzió: [v1.0.6.8](#v1.0.6.8)

Teszt verzió: [v1.0.12.0](#v1.0.12.0)

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
| Teszt AddOn | - |
| Teszt android apk | [Letölthető](../kedvenc.md) |
| Teszt egyedi ár modul apk | [Letölthető](../kedvenc.md) |
| Árazáshoz éles backend | Útvonal: \\\\192.168.20.162\\c$\\spc\\kedvencar_eles_backend IIS: http://192.168.20.162:4103 Db: JEGSBO2/KHAZ_PROD (Mivel élesben lehet csak tesztelni, viszont az éles backendet nem lehet jelenleg felülvágni) |
  
## Telepítési napló

| Verzió | Végpont | Telepítve |
|:-------|:--------|:----------|
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
