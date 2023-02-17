<script type="text/javascript" src="js/jquery.min.js"></script>
<script type="text/javascript" src="js/qrcode.js"></script>

# SPCKhz / SPCEgyediAr fejlesztés

[Verziók](kedvenc-khz.docs/verziok.md)

## SPCKhz addon

v1.0.6.7: A 10.0.0.30-as szerveren a C:\spc\spc_addon_khz mappában található.

## SpcKhz androidos változatai

<a href="download/com.spc.khz.apk" download>SPCKhz v1.0.0.5 (JEGSBO2/KHAZ_PROD)</a>
<div id="qrcodekhz" style="width:100px; height:100px; margin:25px;"></div>

<br/><br/>

<a href="download/com.spc.khzteszt.apk" download>SPCKhzTeszt v1.0.0.7 (JEGSBO2/TESZT_KHAZ_UJ)</a>
<div id="qrcodekhzteszt" style="width:100px; height:100px; margin:25px;"></div>

<br/><br/>
  
### Kedvenc Egyedi ár modul (KHZ-ből készült, csak ármodulos menüpontokkal)

<a href="download/com.spc.khzkedvencar.apk" download>SPCKedvencAr v1.0.0.11 (JEGSBO2/KHAZ_PROD)</a>
<div id="qrcodekedvencar" style="width:100px; height:100px; margin:25px;"></div>

<br/><br/>
  
<a href="download/com.spc.khzkedvencarteszt.apk" download>SPCKedvencArTeszt v1.0.0.11 (JEGSBO2/TESZT_KHAZ_UJ)</a>
<div id="qrcodekedvencarteszt" style="width:100px; height:100px; margin:25px;"></div>

<br/><br/>
  
# Kedvenc Sofőr modul

[Verziók](kedvenc-sofor.docs/verziok.md)

## Android letöltés

<a href="download/com.spc.sofor.apk" download>SPCSofor v1.0.9.0 (JEGSBO2/KHAZ_PROD)</a>
<div id="qrcodesofor" style="width:100px; height:100px; margin:25px;"></div>

<br/><br/>
  
<a href="download/com.spc.soforteszt.apk" download>SPCSoforTeszt v1.0.9.0 (JEGSBO2/TESZT_KHAZ_UJ)</a>
<div id="qrcodesoforteszt" style="width:100px; height:100px; margin:25px;"></div>

<script type="text/javascript">
var qrcodekhz = new QRCode(document.getElementById("qrcodekhz"), {
    text   : "https://humigeri.github.io/download/com.spc.khzv5.apk",
	width  : 100,
	height : 100
});
var qrcodekhzteszt = new QRCode(document.getElementById("qrcodekhzteszt"), {
    text   : "https://humigeri.github.io/download/com.spc.khztesztv7.apk",
	width  : 100,
	height : 100
});
var qrcodesofor = new QRCode(document.getElementById("qrcodesofor"), {
    text   : "https://humigeri.github.io/download/com.spc.soforv9.apk",
	width  : 100,
	height : 100
});
var qrcodesoforteszt = new QRCode(document.getElementById("qrcodesoforteszt"), {
    text   : "https://humigeri.github.io/download/com.spc.sofortesztv9.apk",
	width  : 100,
	height : 100
});
var qrcodekedvencar = new QRCode(document.getElementById("qrcodekedvencar"), {
    text   : "https://humigeri.github.io/download/com.spc.khzkedvencarv11.apk",
	width  : 100,
	height : 100
});
var qrcodekedvencarteszt = new QRCode(document.getElementById("qrcodekedvencarteszt"), {
    text   : "https://humigeri.github.io/download/com.spc.khzkedvencartesztv11.apk",
	width  : 100,
	height : 100
});

</script>