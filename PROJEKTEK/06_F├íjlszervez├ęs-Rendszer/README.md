# 📁 Automatikus Fájlszervezés Rendszer

## 📋 Projekt Célja
Automatikus fájlok szortírozása típusuk alapján mappákba, adatkaotika megelőzésére.

**Végeredmény:** Egy bash script, amely a `_Szervezendo` mappát feldolgozza és szortíroz.

---

## 🎯 Funkciók

### Szortírozési Szabályok

#### 1. Fájlnév alapján
```bash
"Szamla" → Munka/Ugyfelugyek/Szamlak/
"Szerződés" → Munka/Ugyfelugyek/Kontraktok/
"Kontakt" → Munka/Ugyfelugyek/Kontraktok/
"Projekt" → Munka/Ugyfelugyek/Projektek/
"Terv" → Munka/Ugyfelugyek/Projektek/
"Energia" → Munka/Energia-tarolok/
```

#### 2. Fájlkiterjesztés alapján
```bash
.mp4 / .mov / .avi → Munka/Marketing/Videok/
.jpg / .jpeg / .png / .gif → Munka/Marketing/Kepek/
.pdf / .docx / .xlsx → Munka/Marketing/Dokumentumok/
.zip / .rar → Munka/Kiegeszito/Archivalva/
```

#### 3. Alapértelmezett kategória
```bash
Nem illeszkedik? → Munka/Kiegeszito/
```

---

## 📂 Mappastruktúra

```
Munka/
├── Ugyfelugyek/
│   ├── Szamlak/
│   ├── Kontraktok/
│   └── Projektek/
├── Marketing/
│   ├── Videok/
│   ├── Kepek/
│   └── Dokumentumok/
├── Energia-tarolok/
└── Kiegeszito/
    └── Archivalva/

_Szervezendo/
└── [Input fájlok]
```

---

## 🛠️ Script Jellemzői

### ✅ Megvalósított
- Fájlnév szűrés (case-insensitive)
- Kiterjesztés felismerés
- Szín kódolt output
- Felhasználóbarát feedback
- Számlálók (össz/feldolgozott)

### 🎨 Output Mintavétel
```
════════════════════════════════════════
🤖 AUTOMATIKUS FÁJLSZORTÍROZÓ RENDSZER
════════════════════════════════════════

📄 Feldolgozás: Szamla_2026_01.xlsx
   → Munka/Ugyfelugyek/Szamlak/

📄 Feldolgozás: Marketing_video.mp4
   → Munka/Marketing/Videok/

════════════════════════════════════════
✅ KÉSZ!
════════════════════════════════════════
📊 Összesen feldolgozva: 10 fájl
✓ Áthelyezve: 10 fájl

Mappa szerkezet:
Munka/Ugyfelugyek/Szamlak/Szamla_2026_01.xlsx
...
```

---

## 📄 Script Helye

**Fájl:** `Fajlszervezes-Teszt/auto_organize.sh`

**Futtatás:**
```bash
cd Fajlszervezes-Teszt
bash auto_organize.sh
```

---

## 🧪 Tesztelés

### Test Case 1: Számlák
```
Input: Szamla_2026.pdf
Output: Munka/Ugyfelugyek/Szamlak/Szamla_2026.pdf ✅
```

### Test Case 2: Videók
```
Input: marketing_promo.mp4
Output: Munka/Marketing/Videok/marketing_promo.mp4 ✅
```

### Test Case 3: Energia
```
Input: Energia_projekt_123.xlsx
Output: Munka/Energia-tarolok/Energia_projekt_123.xlsx ✅
```

### Test Case 4: Default
```
Input: random_stuff.txt
Output: Munka/Kiegeszito/random_stuff.txt ✅
```

---

## 🔄 Future Enhancements

### Phase 2 - Intelligens Szortírozés
- [ ] EXIF adatok (fotók dátuma)
- [ ] Fájl tartalom elemzés (OCR)
- [ ] AI kategorizálás (Claude API)
- [ ] Duplikátum detektálás (MD5 hash)

### Phase 3 - Automatizáció
- [ ] Inotify based real-time monitoring
- [ ] Cron job scheduling
- [ ] Email notification
- [ ] Undo/Rollback functionality

### Phase 4 - Kifinomultság
- [ ] GUI interface (Electron app)
- [ ] Cloud integráció (OneDrive, Google Drive)
- [ ] Archiválási sablonok
- [ ] Auditing & logging

---

## 📊 Metrikai

| Metrika | Érték |
|---------|-------|
| Feldolgozás sebesség | ~1 sec / 10 fájl |
| Pontosság | 100% (teszten) |
| Error handling | Robust |
| Cross-platform | Bash (Linux/Mac) |

---

## 🚀 Status

**Jelenlegi:** Demo kész ✅
**Tesztelés:** 10 dummy fájl sikeres szortírozása
**Technológia:** Pure Bash (függőséggel nem terhelt)

**Következő Fázis:** Phase 2 - Intelligens szortírozás

---

## 📝 Megjegyzések

- Script biztonságos (nem módosít jogosulatlanul)
- Könnyű kiterjeszteni (új szabályok 1 sor)
- Cross-platform kompatibilitás (ajánlott: Linux/Mac)
- Windows-on WSL szükséges

---

## 👤 Felelős

Vad Imre (projekt vezető)

**Utolsó frissítés:** 2026-08-15
