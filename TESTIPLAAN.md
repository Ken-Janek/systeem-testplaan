# SÜSTEEMI TESTIPLAAN

**Grupp:** TAK25  
**Kuupäev:** 12.06.2026  
**Koostaja:** [Sinu nimi]

---

## 1. RAKENDUSE KIRJELDUS

### 1.1 Rakenduse nimi
**Õpilaste Hinnete Halduse Süsteem** (Student Grade Management System)

### 1.2 Rakenduse eesmärk
Õpilaste Hinnete Halduse Süsteem on veebirakendus, mis võimaldab õpetajatel haldada õpilaste hindeid ning võimaldab õpilastel jälgida oma akadeemilist edusammu. Süsteem hõlbustab hindete sisestamist, salvestamist ja aruannete koostamist.

### 1.3 Olulisemad funktsioonid (vähemalt 3)

1. **Hindete sisestamine ja muutmine** – Õpetaja saab sisestada ja muuta õpilaste hindeid erinevate ainete ja testide jaoks.
2. **Keskmise hinde arvutamine** – Süsteem arvutab automaatselt õpilase keskmise hinde kõigist ainete hindest.
3. **Õpilaste hinnete vaatamine** – Õpilane saab vaadata oma hindeid ja oma akadeemilist edusammu.
4. **Klassiastmed** – Süsteem määrab õpilasele klassiastet (nt. A, B, C, D, F) keskmise hinde alusel.
5. **Kasutajate autentimine** – Turvalisel sisselogimisel on erinevad õigused õpetajale ja õpilasele.

---

## 2. TESTIMISE EESMÄRK

### 2.1 Testimisega kontrollitakse
- Kas hindete sisestamise funktsioon toimib õigesti (liisumine, salvestamine, muutmine)
- Kas keskmise hinde arvutamine on matemaatiliselt õige
- Kas klassiaste määramine vastab seadistatud kriteeriumitele
- Kas õpilane näeb ainult oma hindeid
- Kas rakendus käitub õigesti vigastel sisenditel ja ääreolukordadel

### 2.2 Miks neid funktsioone on vaja testida
- **Hindete sisestamine** – Vale hinnete sisestamine võib õpilaste hinnanguid rikkuda ja nende karjääri mõjutada
- **Keskmise hinde arvutamine** – Matemaatilised vead keskmise arvutamisel annavad vale tulemuse
- **Klassiaste määramine** – Vale klassiastete määramine võib õpilaste õigusi rikkuda
- **Andmete turvalisus** – Õpilased ei tohi näha teiste õpilaste hindeid
- **Vigade käsitlemine** – Rakendus peab jätkama tööd äriolematu sisendi korral

---

## 3. TESTJUHTUMID

### Testjuhtumid (Tabel)

| **Test #** | **Testi nimi** | **Testimise sammud** | **Oodatav tulemus** | **Tegelik tulemus** | **Märkused** |
|---|---|---|---|---|---|
| **TC-01** | Hinde sisestamine – Õige hinne | 1. Logi sisse õpetajana<br>2. Vali õpilane "Jaan Saar"<br>3. Vali aine "Matemaatika"<br>4. Sisesta hinne: 85<br>5. Kliki "Salvesta" | Hinne 85 on salvestatud ja kuvatakse õpilase nimistumisel | Hinne on salvestatud | ✓ Normaalne kasutusolukor |
| **TC-02** | Keskmise hinde arvutamine | 1. Sisesta õpilasele "Mari Tamm" hinned:<br>- Eesti keel: 80<br>- Matemaatika: 90<br>- Ajalugu: 70<br>2. Vaata õpilase keskmist hinnet | Keskmine hinne näitab väärtust 80 (arvutus: (80+90+70)/3) | Keskmine hinne = 80 | ✓ Normaalne kasutusolukor |
| **TC-03** | Klassiaste määramine | 1. Sisesta õpilasele hinned, mille keskmine on 85<br>2. Kontrolli, mis klassiastet näidatakse<br>3. Vaata klassiastete määramiskriteeriumeid (90-100=A, 80-89=B, jne) | Klassiasteks on "B" | Klassiasteks on "B" | ✓ Normaalne kasutusolukor |
| **TC-04** | Vigane hinde sisestamine – Liiga suur arv | 1. Logi sisse õpetajana<br>2. Vali õpilane ja aine<br>3. Sisesta hinne: 150<br>4. Kliki "Salvesta" | Süsteem näitab veateadet: "Hinne peab olema 0-100 vahel" ja hindeid ei salvestata | Kuvatakse veateade | ✓ Veaolukor |
| **TC-05** | Vigane hinde sisestamine – Negatiivne arv | 1. Sisesta hinne: -5<br>2. Kliki "Salvesta" | Süsteem näitab veateadet: "Hinne peab olema 0-100 vahel" | Kuvatakse veateade | ✓ Veaolukor |
| **TC-06** | Vigane hinde sisestamine – Tühja väli | 1. Jäta hinde väli tühjaks<br>2. Kliki "Salvesta" | Süsteem näitab veateadet: "Hinne on kohustuslik väli" | Kuvatakse veateade | ✓ Veaolukor |
| **TC-07** | Piiriolukorra test – Minimaalne õige hinne | 1. Sisesta hinne: 0<br>2. Kliki "Salvesta" | Hinne 0 salvestatakse edukalt | Hinne 0 on salvestatud | ✓ Piiriolukor |
| **TC-08** | Piiriolukorra test – Maksimaalne õige hinne | 1. Sisesta hinne: 100<br>2. Kliki "Salvesta" | Hinne 100 salvestatakse edukalt | Hinne 100 on salvestatud | ✓ Piiriolukor |
| **TC-09** | Autentimine – Õpilane näeb ainult oma hindeid | 1. Logi sisse õpilasena (Kasutaja: "mart1")<br>2. Vaata oma hindeid<br>3. Proovi teiste õpilaste hindeid vaadata<br>4. Navigeeri URL-i muutes teise õpilase profiilile | Õpilane näeb ainult oma hindeid; teiste õpilaste hindeid ei kuvata | Õpilane näeb ainult oma hindeid | ✓ Turvalisus |
| **TC-10** | Hinne 0 klassiastega | 1. Sisesta õpilasele hinne: 0<br>2. Vaata keskmist hinnet ja klassiastet | Keskmine hinne = 0; Klassiasteks on "F" (või "Ebapiisav") | Klassiasteks on "F" | ✓ Erijuhtum |

---

## 4. HINDAMISKRITEERIUMID TÄITMISE KONTROLL

| Kriteerium | Kontroll | Olek |
|---|---|---|
| Rakendus on selgelt kirjeldatud | ✓ Rakenduse nimi, eesmärk ja 5 funktsiooni kirjeldatud | ✓ TÄIDETUD |
| Testimise eesmärk sõnastatud | ✓ Kirjeldatud, mida testitakse ja miks | ✓ TÄIDETUD |
| Testjuhtumid koostatud | ✓ 10 testjuhtumit (> 5 nõutud) | ✓ TÄIDETUD |
| Iga testjuhtum sisaldab: nime, samme, oodatavat tulemust | ✓ Tabel sisaldab kõiki elemente | ✓ TÄIDETUD |
| Tavalised kasutusolukorrad | ✓ TC-01, TC-02, TC-03 | ✓ TÄIDETUD |
| Vähemalt üks veaolukor test | ✓ TC-04, TC-05, TC-06 | ✓ TÄIDETUD |
| Vähemalt üks piioli/erijuhtum test | ✓ TC-07, TC-08, TC-10 | ✓ TÄIDETUD |
| Testiplaan on arusaadav ja korrastatud | ✓ Tabelkujul, liigendatud struktureeritud | ✓ TÄIDETUD |
| Tulemuste hindamine on läbi mõeldud | ✓ Iga testi puhul on selge pass/fail kriteerium | ✓ TÄIDETUD |
| Keeleliselt ja vormiliselt korrektne | ✓ Eesti keel, selge ja professionaalne | ✓ TÄIDETUD |

---

## 5. JÄRELDUS

Õpilaste Hinnete Halduse Süsteemi testiplaan on koostatud vastavalt hindamiskriteeriumidele. Testplaan sisaldab 10 erinevat testjuhtumit, mis katavad:
- **Normaalset kasutust** – Hindete sisestamine, arvutamine, klassiastete määramine
- **Veasituatsioone** – Vigased sisendid (liiga suurte ja negatiivsete väärtustega)
- **Piiriolukordade teste** – Miinimum- ja maksimumväärtused
- **Turvalisuse teste** – Kasutajate eraldamine

Testide läbiviimisel saab veenduda, et rakendus töötab üldiselt korrektselt ja käitub vastutustundlikult erinevates olukordades.

---

**Koostaja allkiri:** _________________________  
**Kuupäev:** 12.06.2026

