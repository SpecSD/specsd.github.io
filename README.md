# Specific Software Development

## FAQ

### Telepítés előfeltételek

#### Böngészős változat

Ez a kliens oldaláról semmilyen plusz telepítést nem igényel, böngészőben fut. Böngészőként Edge, vagy Chrome használata javasolt.

Amihez csatlakozik, az egy IIS szerver lesz, ahol van frontendünk, meg backendünk. A [.net6 letöltés](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) oldaláról a következők kellenek:
- A bal oldali teljes sdk-ra nincs szükség, de lehet, hogy célszerű feltenni mindent.
- Egyébként a jobb oldali runtime-ok közül a .Net runtime 6...-ot
- Szükség lesz az ASP.NET Core Runtime 6...-ra
- Ha a backend DI API műveleteket is végrehajt (pl. bizonylatok generálása), és az SAP kliens 32bites, akkor a fentiekből a 32bites változatot (is) telepíteni kell.
- Az IIS-hez telepíteni kell az [url-rewrite modult](https://www.iis.net/downloads/microsoft/url-rewrite)
- Ha az IIS-ben elkészített site megnyitásakor 500 Server Error-t jelez, akkor még az [aspnetcore hosting bundle](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)-t kell telepíteni.

#### Addon (winform)

A kliensre fel kell tenni a [.net6 letöltés](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) oldaláról:
- Talán a bal oldali teljes sdk-ra nincs szükség, ha lehet, csak a runtime-ot tegyük fel.
- Egyébként a jobb oldali runtime-ok közül a .Net runtime 6...-ot, annak az x86 változatát, v10 SAP esetén a 64 bitest!
- ASP.NET Core Runtime 6... x86/64
- .NET Desktop Runtime 6.... x86/64
- Edgewebview: https://developer.microsoft.com/en-US/microsoft-edge/webview2/

#### Android

Ez a tapasztalatok alapján egyéb telepítést nem igényel, az apk, amit adunk, az elég.

#### Windows (különálló, nem addon)

Ilyet még nem generáltunk ki (nem feltétlenül van rá szükség, a böngészős változat ugyanúgy használható), de ha szükség lesz rá, akkor valószínűleg ugyanazt fogja igényelni, mint az addon alatt leírtak. Itt viszont - mivel ez közvetlenül SBO SDK-hoz nem csatlakozik, ezért lehet a 64 bites változat.

### Telepítés helye

#### Böngészős változat

Itt IIS-en belül két végpontra (site-ra) van szükség, az egyik a backendnek, a másik a frontendnek. Célszerűen ez a két végpont ne legyen publikusan elérhető, csak belső hálózaton belülről.

Maga az IIS szerver futhat az SAP adatbázis szerveren is, a tapasztalatok alapján nem szokott teljesítmény problémákat okozni az SAP működésében. De különálló szerverre is telepíthető, amennyiben a rendszergazda fontosnak tartja ennek elkülönítését.

A különálló esetben ennek a hardvernek a következő követelményeknek kell megfelelnie:
- Legalább az általános, Microsoft által javasolt konfiguráció IIS esetén.
- Amennyiben a backend DI API műveleteket is végrehajt (pl. bizonylatok generálása), akkor ez a szerver is egy SAP Business One kliens legyen.
- Az SQL szerver magas sávszélességgel elérhető legyen.

A backend és frontend telepítési mérete változó lehet, hozzávetőlegesen végpontonként 2-300 MB helyigényről van szó.

A működés során szükség lehet az egyes funkciókban feltöltött fájlok tárolására. (Pl. szkennelt számlaképek tárolása) Ezt a tárolást a backend végzi, a beállításokban megadott útvonalra. Ez természetesen bármilyen útvonal lehet, akár lokális is, de célszerű egy külön fájlszerver útvonalát beállítani.
Ahhoz pedig, hogy ennek jogosultságai korlátai ne legyenek, a backend alkalmazáskészletének futását egy olyan felhasználóra kell állítani, akinek erre az útvonalra írási joga van.

#### Addon (winform)

Az AddOn-t minden esetben regisztráljuk az SAP Business One-ba, ott a rendszergazdának lehetősége van beállítani, hogy melyik felhasználónál milyen módon induljon el.  
Amikor a felhasználó egy olyan kliensen lép be az SAP-ba, ahol még nincs, vagy nem a legfrissebb változat van telepítve, akkor megjelenik egy telepítő ablak, aminek segítségével az adott kliensre települni fog az AddOn. Alapértelmezetten az SAP által adott útvonalra, de ez tetszőlegesen megváltoztatható. Fontos, hogy az adott felhasználónak legyen írási joga a kiválasztott mappához, egyébként az addon nem fog települni.
Az AddOn-hoz szükséges telepítési fájlok kb. 1-200 MB-ot foglalnak el.

Az AddOnként történő futtatáshoz is szükség van a backend-re, ahhoz csatlakozik a program.

#### Android

Az androidos alkalmazáshoz apk-t adunk, ezért a telepítéshez be kell állítani a külső forrásból történő telepítések engedélyezését. Az apk hozzávetőlegesen 50MB-ot foglal el. Ez is csatlakozik a backendhez.