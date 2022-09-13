# Specific Software Development

## FAQ

### Telepítés előfeltételek
<details>
<summary>Kinyit</summary>

#### Böngészős változat

Ez a kliens oldaláról elvileg semmit nem igényel, böngészőben fut.

Amihez csatlakozik, az egy IIS szerver lesz, ahol van frontendünk, meg backendünk. A [.net6 letöltés](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) oldaláról a következők kellenek:
- Talán a bal oldali teljes sdk-ra nincs szükség, de lehet, hogy célszerű feltenni mindent.
- Egyébként a jobb oldali runtime-ok közül a .Net runtime 6...-ot
- Valószínűleg szükség lesz az ASP.NET Core Runtime 6...-ra
- Ha di api van a backenden, akkor az 32bites lesz, ezért valószínűleg a 32bites változatot (is) telepíteni kell.

#### Addon (winform)

A kliensre fel kell tenni a [.net6 letöltés](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) oldaláról:
- Talán a bal oldali teljes sdk-ra nincs szükség, ha lehet, csak a runtime-ot tegyük fel.
- Egyébként a jobb oldali runtime-ok közül a .Net runtime 6...-ot, annak az x86 változatát!
- ASP.NET Core Runtime 6... x86
- .NET Desktop Runtime 6.... x86
- Edgewebview: https://developer.microsoft.com/en-US/microsoft-edge/webview2/

#### Android

Ez a tapasztalatok alapján egyéb telepítést nem igényel, az apk, amit adunk, az elég.

#### Windows (különálló, nem addon)

Ilyet még nem generáltunk ki (nem feltétlenül van rá szükség, a böngészős változat ugyanúgy használható), de ha szükség lesz rá, akkor valószínűleg ugyanazt fogja igényelni, mint az addon alatt leírtak. Itt viszont - mivel ez közvetlenül SBO SDK-hoz nem csatlakozik, ezért lehet a 64 bites változat.

</details>
