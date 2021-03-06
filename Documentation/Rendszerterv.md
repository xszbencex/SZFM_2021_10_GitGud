# Rendszerterv

***1. A rendszer célja***<br>
A rendszer célja, hogy a válaszadók egy jól átlátható, könnyen értelmezhető, űrlapot tölthessenek ki, ahol a kitöltés gyors és hatékony minden korosztály számára. A felhasználói élmény növeléséhez fontos, hogy a kérdések és válaszok egyértelműen legyenek megfogalmazva, kerülve a többszörösen összetett mondatokat, bonyolult kifejezéseket. Továbbá elengedhetetlen, hogy minden kérdésblokk egymástól jól látható módon, elkülönítve jelenjen meg. Többféle válaszadási mód is elérhető lesz a kitöltés során: legördülő menüből való kiválasztás, eldöntendő kérdésekre igen/nem válaszlehetősek kiválasztása, megjegyzés mezőbe további gondolatok írása. Az űrlap nem csak számítógépen, hanem okostelefonon vagy tableten is elérhető lesz mindenki részére a legelterjedtebb webböngészőkön keresztül. A kitöltők a sikeres kitöltés után (minden kötelező kérdésre válaszolva) egy köszönetnyilvánító visszajelzést kapnak, illetve láthatják a szervezők elérhetőségeit is.

***2. Projektterv***<br>
**Projekt munkatársak és felelőségek:**

Backend munkálatok: 
- Pete Balázs
- Szabó Bence
- Szimeonov Viktória
- Tóth Csenge Beatrix
- Tóth Zoltán

Feladatuk a funkciók létrehozása és megvalósítása.

| Funkció / Story | Feladat / Task | Prioritás | Becslés | Aktuális becslés | Eltelt idő | Hátralévő idő |
|-----------------|----------------|-----------|---------|------------------|------------|---------------|
| Követelmény specifikáció | | 0 | 12 | 12 | 12 | 0 |
| Funkcionális specifikáció | | 0 | 12 | 12 | 12 | 0 |
| Rendszerterv | | 0 | 16 | 16 | 16 | 0 |
| Fejlesztés | HTML | 1 | 12 | 12 | 12 | 0 |
| | CSS | 1 | 12 | 12 | 12 | 0 |
| |JavaScript | 1 | 12 | 12 | 12 | 0 |
| | JSON | 1 | 12 | 12 | 12 | 0 |
| Tesztelés | | 1 | 16 | 16 | 10 | 6 |
| Értékelés | | ? | ? | ? | ? | ? | 

***3. Üzleti folyamatok modellje***<br>

<img src="images/üzl_foly_mod_beta.png" data-canonical-src="images/üzl_foly_mod_beta.png" width="768" height="576" />

***4. Követelmények***<br>
Követelmények, funkciók, melyek a megfelelő működéshez elengedhetetlenek.
- Funkcionális követelmények:
  - Kérdések, és az azokhoz tartozó válaszlehetőségek átlátható megjelenítése.
  - Eldöntendő kérdések esetében 2 választási lehetőség közül csakis egy kiválasztása (igen/nem).
  - Választó kérdések esetében egy vagy több válaszlehetőség kiválasztása legördülő menüből.
  - Egyes választó kérdések esetében egyéb gomb megjelenítése, melyre kattintva saját válaszlehetőség begépelése biztosított.
  - Kötelező jelleggel megjelölt kérdések (piros csillag a kérdőjel után közvetlenül) kihagyása esetén figyelmeztető szöveg megjelenítése.
  - Az utolsó kérdést követően szövegdoboz elhelyezése, amelybe kérdések, megjegyzések, véleményezés írására van lehetőség.
  - Androidon és webes környezeten való működés.
- Nem funkcionális követelmények:
  - Válaszlehetőség kiválasztása esetén gyors reagálás. A rendszer jelezze a kitöltő felé, hogy feldolgozta a kérést.
  - A rendszer minimális válaszidőn belül feldolgozza az adatokat.
  - Biztonságos működés.
  - Könnyű karbantarthatóság.
  - Működőképesség, használhatóság.
  - Adatok megbízhatósága és rendelkezésre állása.
- Törvényi előírások, szabványok:
  - GDPR-nak, ÁSZF-nek való megfelelés.
  - Szükség esetén Cookie szabályzat feltüntése a weboldalon.
  - Checkbox jóváhagyása nélkül az űrlapon feltüntetett válaszok elküldése nem engedélyezett.


***5. Funkcionális terv***<br>
**<ins>Rendszer szereplők:<ins>**
- Admin
- Kérdőív kitöltő személy

**<ins>Rendszerhasználati esetek és lefutásaik:<ins>**<br>
ADMIN:
- Beléphet bármilyen szereplőként teljes hozzáférése van a rendszerhez
- A felhasználói adatokat látják, változtathatják
- Felhasználói adatok módosítása
- Tesztek létrehozása, törlése, módosítása

FELHASZNÁLÓ:
- képes a kérdőív minden kérdésére válaszolni.


***6. Fizikai környezet***<br>
  
- Az űrlap Android és web platformra, hordozható eszközökre (okostelefonok, táblagépek) készül.
- Az összes elterjedt webböngészőn (Firefox, Chrome, Edge, Opera) megfelelően működik.
- Nincsenek megvásárolt komponenseink.
- Fejlesztői eszközök:
  - Visual Studio Code
  - Bootstrap
  - GIMP
  - Trello

***7. Architektúrális terv***<br>

- A webalkalmazás keretrendszer nélkül készül, natív javascript, html és css segítségével, így az alkamzásnak nincsen semmilyen függősége és a telepítéssel sem kell bajlódni.
- A kérdéseket és válaszokat JSON állományban tároljuk és az programunk ezt dolgozza fel javascript segítségével.
- A JSON állomány szerkezete a következő:
<pre><code>{
     "questions": [
      {
        "id": "1",
        "question": "Kérdés szövege",
        "type": "Kérdés típusa",   // "options" vagy "text" vagy "decidable" vagy "logical"
        "options": ["Lehetőség 1", "Lehetőség 2", ...]    // "options" típus esetén
      },
      {
        "id": "2",
        "question": "Kérdés szövege",
        "type": "Kérdés típusa",   // "options" vagy "text" vagy "decidable" vagy "logical"
        "options": ["Lehetőség 1", "Lehetőség 2", ...]    // "options" típus esetén
      }
   ]
}</code></pre>

***8. Adatbázis terv***<br>
![Adatmodell](images/adatmodell.png)
  
***8. Implementációs terv***<br>

A Webes felület főként HTML, CSS, és Javascript nyelven fog készülni.
Ezeket a technológiákat amennyire csak lehet külön fájlokba írva készítjük, és
úgy fogjuk egymáshoz csatolni a jobb átláthatóság, könnyebb változtathatóság,
és könnyebb bővítés érdekében. Képes lesz feldolgozni a JSON állományt, és a benne 
tárolt adatok alapján a kérdéseket megfelelően megjeleníteni a felületen.
  
***9. Tesztterv***<br>
  
   A tesztelések célja a rendszer és komponensei funkcionalitásának
teljes vizsgálata, ellenőrzése, a rendszer által megvalósított üzleti
szolgáltatások verifikálása.<br>
  
**Tesztelési eljárások**
 
<ins>Unit teszt:<ins>
  
Ahol csak lehetséges, szükséges már a fejlesztési idő alatt is tesztelni, hogy a
metódusok megfelelően működnek-e.
Ezért a metódusok megfelelő működésének biztosítására mindegyikhez írni
kell Unit teszteket, a minél nagyobb kódlefedettséget szem előtt tartva. A
metódusok akkor vannak kész, ha a tesztesetek hiba nélkül lefutnak az egyes
metódusokon.
  
<ins>Alfa teszt:<ins>
  
  A teszt elsődleges célja: az eddig meglévő funkcióknak a különböző
böngészőkkel, és androidokkal való kompatibilitásának tesztelése. A tesztet a
fejlesztők végzik.
  Az eljárás sikeres, ha különböző böngészőkben és különböző androidokon is
megfelelően működnek a különböző funkciók.
  A teszt időtartama egy hét.
  
<ins>Tesztelendő funkciók<ins>
  
<b>Backend Service<b>
  
- Képesnek kell lennie csatlakozni webes, és androidos klienshez is.
- Képesnek kell lennie egy időben kiszolgálni több klienst is.
- Képesnek kell lennie minden felületen elérhető funkciók biztosítására.
  



***10. Telepítési terv***<br>
**Webes alkalmazás:**
    A szoftver webes felületéhez csak egy ajánlott böngésző telepítése szükséges (Google Chrome, Firefox, Opera, Safari), külön szoftver nem kell hozzá. A weboldalra közvetlenül az internetről kapcsolódnak rá a kliensek.


***11. Karbantartási terv***<br>
A weboldal folyamatos üzemeltetése és karbantartása, mely magába foglalja a programhibák elhárítását, a belső igények változása miatti módosításokat, valamint a környezeti feltételek változása miatt megfogalmazott program-, illetve állomány módosítási igényeket.

**Karbantartás:**
- A felhasználók által felfedezett hibák javítása.
- A weboldal naprakészen tartása és finomhangolása.
-  Olyan problémák elhárítása, amelyek még nem tűnnek fontosnak, de később komoly problémákat okozhatnak.

***12. Képernyőtervek***<br>

![Képernyő tervezete](images/kepernyoterv1.png)<br>
![Képernyő tervezete](images/kepernyoterv2.png)
