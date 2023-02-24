#  NAV bejövő számla letöltő telepítési útmutató 

Első körben le kell futtatni NAV bizonylatok szkript.txt fájlban lévő
szkripteket az adatbázisban. Ez létrehozza a következő adatbázis
objektumokat:

-   SPC_NAV_BIZONYLATOK tábla, ide kerülnek a NAV-tól letöltött
    bizonylat fej adatok

-   SPC_NAV_BIZONYLAT_TETELEK tábla, ide kerülnek a NAV-tól letöltött
    bizonylat tétel adatok

-   SPC_NAV_BIZONYLATOK_LOG tábla, ide a futás közben keletkezett
    logokat menti majd a program.

-   SPC_SEQ szekvencia, ha még nincs, meg akkor létrehozza

-   SPC_NAV_SEQ szekvencia

-   SPC_NAV_BIZONYLATOK_CHECK_V nézet, ez majd a lekérdezésekhez kell.

NAV_Helit_Szamlaletolto mappában van maga a program. Lényegesebb fájlok:

-   appsettings.json ez tartalmazza a konfigurációs adatokat

-   log.txt ide a program logolása ide történik

-   navkomm.exe ezt a fájlt kell elindítani a program futtatásához

## appsettings.json

A fájl tartalma és leírása

{

\"ConfigSettings\": {

\"serverName\": \"192.168.xx.xx\", a szerver IP címe vagy neve

\"dbName\": \"HELIT_PROD\", az adatbázis neve

\"dbUser\": \"sdkuser\", adatbázis felhasználónév ezt nem kell átírni

\"dbPassword\": \"l6c4sCZkuvBjzVhcBv4pDg==\", adatbázis jelszó, ez is jó
így

\"logPath\": \"log.txt\", a log fájl neve, nem kell módosítani

\"navUrl\": \"https://api.onlineszamla.nav.gov.hu/invoiceService/v3\", a
NAV szolgáltatás elérése nem kell módosítani

\"navLogin\": \"xxxxxxxxxxxx\", a NAV-tól kapott technikai felhasználó
bejelentkezési neve

\"navPassword\": \"xxxxxxxxxxxxxxxxxx\", a NAV-tól kapott technikai
felhasználó jelszava kódolva, leírom később hogyan kell kódolni

\"navXmlSignKey\": \"xxxxxxxxxxxxxxxxxxxxxxxx\", a NAV-tól kapott
technikai felhasználó aláíró kulcsa

\"navExchangeKey\": \"xxxxxxxxxxxxxxxxxxx\", a NAV-tól kapott technikai
felhasználó csere kulcsa

\"navTaxNumber\": \"xxxxxxxx\", az adószámotok első 8 számjegye

\"softwareId\": \"HUxxxxxxxx00000001\", szoftver azonosító kérlek, az
x-ek helyére az adószámotok első 8 számjegyét írjátok be, 18 hosszú
kell, legyen, az nem változhat

\"softwareName\": \"SPC-NAV_számlaletöltő\", szoftvernév, ez így jó

\"softwareOperation\": \"NAV_számlaletöltés\", ez így jó

\"softwareMainVersion\": \"1.0\", ez így jó

\"softwareDevName\": \"SPC\", ez így jó

\"softwareDevContact\": \"xxxxxxxxxxx@helit.hu\", ide egy email
címeteket kell megadni

\"dateFrom\": \"convert(nvarchar(10), GETDATE()-1,121)\", a program
paraméterei, lentebb részletesen leírom

\"dateTo\": \"convert(nvarchar(10), GETDATE()-1,121)\"

}

}

## Technikai felhasználó jelszavának kódolása

Magával a programmal lehet a jelszót bekódolni, parancssorban be kell
lépni a navkomm.exe mappájába, és így kell elindítani a programot
paraméterként megadva a jelszót, és a program eredményként kiírja a
jelszót kódolva. Tehát a parancs:

navkomm.exe /pwd jelszó

## A program paraméterezése

Paraméterként a NAV-hoz beérkezés időpontjára lehet intervallumot
megadni. Ez kétféleképpen lehet, vagy konkrét dátumot kell megadni, vagy
képletet. A program a dateFrom paraméterhez 0 óra 0 percet illeszt
hozzá, a dateTo paraméterhez 23 óra 59 percet, így lehet egy napot is
megadni azonos dátumokkal. Ha konkrét dátumot adunk meg, de a képletnek
is, ilyen formában kell a dátumot megadni ÉÉÉÉ-HH-NN. Ha konkrét dátumot
adunk meg annak így kell kinéznie "'2023-01-01'", a dupla aposztrófok
mellet sima aposztrófok is kellenek ilyenkor, képlet esetén nem.

## A program futtatása

A programot célszerű naponta hajnalban az előző napi időszakra futtatni
ütemezett feladattal, azokkal a konfigurációs dátum paraméterekkel,
melyek a példafájlban is szerepelnek.

## Felhasználói lekérdezések

A NAV bizonylatok felhasznaloi lekerdezes.txt fájl tartalmaz 2
felhasználói lekérdezést, ezeket az adatok áttekintésére lehet
használni.
