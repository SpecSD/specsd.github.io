# IFSZ_AddOn_Kerhaz

- 9.2.0.9
  - Könyvel A gomb használatba vétele
    1. A Banki fizetés hívásakor a Könyvelési dátumba beírja a kivonat értéknapját
    2. KONYVEL_A_KI és KONYVEL_A_BE paraméterekben be lehet állítani a számköröket az automatikus könyveléshez, ha ezek be vannak
       állítva akkor a Kimenő fizetések Bejövő fizetések formon is erre állítja be a program a számkört.
       A paraméterek formátuma <EEEE>GY vagy <EE>GY lehet például. Az <EEEE> az évszámra, az <EE> az évszám utolsó két számjegyére
       cseréli le, és veszi még a beírt karaktereket, így kapjuk meg a számkört.
    3. A véletlen folytán le nem zárt de feldolgozott kivonatokat lezárja.
    4. A Banki tranzakciók alján a Követel és Tartozik értékeinek megcserélése
    5. Egyszerűsített banki utalás form gyorsítása
- 9.2.0.8
  - Új pénztár modul
- 9.2.0.7
  - A szállítólevél generálásba is beletesszük, hogy vigye át a tervezetből a megjegyzést
- 9.2.0.6
  - IFSZ-től kapott verzió

## Telepítési végpontok

| Végpont | Leírás |
|:--------|:-------|
| IFSZ_AddOn_Kerhaz | AddOnként regisztrálva, \\192.168.20.37\c$\Ifsz_AddOn\IFSZ_AddOn_Kedvenc_UJ\IFSZ_AddOn_Kedvenc_UJ.exe |
| TESZT_IFSZ_AddOn_Kerhaz | AddOnként regisztrálva, \\192.168.20.37\c$\Ifsz_AddOn\IFSZ_AddOn_Kedvenc_UJ\TESZT_IFSZ_AddOn_Kedvenc_UJ.exe |
  
## Telepítési napló

| Verzió | Végpont | Telepítve |
|:-------|:--------|:----------|
| 9.2.0.9 | TESZT_IFSZ_AddOn_Kerhaz | 2023.02.27 |
| 9.2.0.8 | IFSZ_AddOn_Kerhaz | 2023.01.24 |
| 9.2.0.8 | TESZT_IFSZ_AddOn_Kerhaz | 2023.01.05 |
| 9.2.0.7 | IFSZ_AddOn_Kerhaz | 2022.11.22 |