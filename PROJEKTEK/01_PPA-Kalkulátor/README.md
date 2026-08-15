# 🧮 PPA Kalkulátor

## 📋 Projekt Célja
Valós idejű PPA (Power Purchase Agreement) gazdaságossági analízis generálása magyar piacra optimalizálva.

**Végeredmény:** 60 másodperc alatt teljes PPA gazdaságossági analízis.

---

## 🎯 Input Paraméterek

| Paraméter | Típus | Példa |
|-----------|-------|-------|
| Napelem teljesítmény | kW | 30 |
| Energiatárolás | kWh | 50 |
| Régió | Dropdown | Budapest/Miskolc/Debrecen/Szeged |
| Éves fogyasztás | MWh | 250 |
| PPA futamidő | év | 10 |

---

## 📊 Output Kalkuláció

```
✅ Évi termelés: XXX MWh
✅ Ár: XX Ft/kWh
✅ ROI: X% (10 év alatt)
✅ CO₂ spórolás: X tonna/év
✅ Break-even: X év
```

---

## 📈 Számítási Logika

### 1. Napsugárzás Adatok (Régió alapján)
- **Forrás:** PPA DATA HUB / solar-irradiance-by-region.csv
- Budapest: ~1100 kWh/m²/év
- Miskolc: ~1050 kWh/m²/év
- Debrecen: ~1120 kWh/m²/év
- Szeged: ~1130 kWh/m²/év

### 2. Energiatermelés Előrejelzés
```
Évi termelés (MWh) = Napelem teljesítmény (kW) × Régió irradiance (kWh/m²/év) / 1000
```

### 3. Energiatárolás Optimálás
- Tárolo kapacitás → napi/heti ciklus optimálás
- Hatékonyság: ~90% (round-trip)
- Leépülés: ~2-3% évente

### 4. Ár Számítás
- **Spot ár:** Magyarország grid árak
- **PPA prémium:** Futamidő szerint (+5-15%)
- **Végső ár:** Spot + Prémium = Ft/kWh

### 5. ROI Kalkuláció
```
ROI (%) = (Termelés érték - Beruházási költség) / Beruházási költség × 100
```

### 6. CO₂ Csökkentés
```
CO₂ spórolás = Évi termelés (MWh) × 0,3 tonna/MWh (magyar grid átlag)
```

---

## 🛠️ Technológia Stack

- **Számítások:** Python 3.9+
- **Adatok:** Google Sheets API / CSV
- **Automatizálás:** n8n workflow
- **Frontend:** Google Forms vagy egyszerű web form

---

## 📅 Fázisok

### Phase 1: MVP (1 hét)
- [ ] Python kalkulátor modul
- [ ] Input paraméter validálás
- [ ] CSV adatok integrálása
- [ ] Basic output template

### Phase 2: Integrálás (1 hét)
- [ ] n8n workflow
- [ ] Google Sheets összekötés
- [ ] Web form frontend
- [ ] Email output küldés

### Phase 3: Produkció (1 hét)
- [ ] Performance tesztelés
- [ ] Pontosság validálás (referencia PPAs ellen)
- [ ] UI refinement
- [ ] Live deployment

---

## 📚 Referencia Case

**Hankook Tire + GoldenPeaks Capital**
- 430 GWh / 10 év
- 30 MWp napelem
- **20% energiafogyasztás fedezés**
- 10,000 tonna CO₂/év spórolás
- Ár: ~20-22 Ft/kWh

---

## 📍 Adatforrások

- **Napsugárzás:** PPA DATA HUB / 01_SOLAR-PARAMETERS
- **Battéria spec:** PPA DATA HUB / 02_STORAGE-PARAMETERS
- **Árak:** PPA DATA HUB / 03_PRICING-DATA
- **Referencia deals:** PPA DATA HUB / 04_REFERENCE-CASES

---

## 🚀 Status

**Jelenlegi:** Design fázis ✅
**Következő:** Kódolás elindítása

**Megjegyzés:** Alapadatok szükségesek az OneDrive PPA DATA HUB-ból

---

## 👤 Felelős

Vad Imre (projekt vezető)

**Utolsó frissítés:** 2026-08-15
