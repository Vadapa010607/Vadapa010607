# 📋 PPA Ajánlatgenerátor

## 📋 Projekt Célja
Automatikus vállalati PPA ajánlat generálása 60 másodpercen belül.

**Workflow:** Vállalat adatok → Kalkulátor → Case Study → Email ajánlat → Küldés

---

## 🔄 Teljes Workflow

```
1. INPUT: Vállalat neve + Régió
                    ↓
2. ADATOK LEKÉRÉS: LinkedIn/web keresés
   - Éves fogyasztás
   - Iparág
   - Elérhetőség
                    ↓
3. KALKULÁTOR FUTTATÁS
   (PPA Kalkulátor modul meghívása)
                    ↓
4. CASE STUDY ADAPTÁLÁS
   - Hankook-szerű analógia
   - Régió-specifikus adatok
   - CO₂ megtakarítások
                    ↓
5. EMAIL AJÁNLAT GENERÁLÁS
   - Professionális template
   - Vállalat specifikus adatok
   - CTA (Call-to-Action)
                    ↓
6. KÜLDÉS + NYOMON KÖVETÉS
   - Email elküldés
   - Follow-up scheduling
   - Conversion tracking
```

---

## 📝 Input Adatok

| Mező | Forrás | Kötelező |
|------|--------|----------|
| Vállalat neve | User input | ✅ |
| Régió | User input | ✅ |
| Éves fogyasztás (MWh) | LinkedIn/web | ⚠️ opcionális |
| PPA futamidő preferencia | User input | ✅ |

---

## 📧 Output Email Template

```
Subject: [Vállalat neve] - Napelem PPA Ajánlat

---

Tisztelt [Kapcsolattartó],

Elemzésünk alapján az Ön vállalata **[éves fogyasztás] MWh** 
energiát fogyaszt évente [régió]-ban.

Egy napelem + tárolós PPA megoldással:

📊 AJÁNLAT PARAMÉTEREI:
├─ Napelem teljesítmény: [XX kWp]
├─ Energiatárolás: [XX kWh]
├─ Évi termelés: [XXX MWh]
└─ Fedezettség: [XX%] az energiafogyasztásának

💰 GAZDASÁGOSSÁGI ADATOK:
├─ Ár: [XX Ft/kWh]
├─ Évi megtakarítás: [X Ft]
├─ ROI: [X%] (10 év alatt)
└─ Break-even: [X év]

🌱 FENNTARTHATÓSÁG:
├─ CO₂ csökkentés: [X tonna/év]
└─ Szén semlegességhez hozzájárulás

📚 REFERENCIA CASE:
Hankook Tire + GoldenPeaks Capital
→ 30 MWp napelem, 20% energiafogyasztás fedezés

Szeretnénk részletesebben megbeszélni? Foglaljon időpontot:
[Calendly link / Egyéb appointment link]

Üdvözettel,
[Aláírás]
```

---

## 🔗 Integrációk

### LinkedIn API (Ügyfél keresés)
- Cégadatok lekérése
- Fogyasztási profil becsülése
- Elérhetőség

### Google Sheets (Kalkulátor)
- PPA Kalkulátor futtatása
- Adatok tárolása
- Históriás tracking

### Email Bot
- Template rendering
- Персонализáció
- Küldés + nyomon követés

### n8n Workflow
- Teljes folyamat automatizálása
- Trigger-ok (új lead, manual)
- Error handling

---

## 🛠️ Technológia

- **Workflow:** n8n
- **AI:** Claude API (email generálás, analízis)
- **Adatok:** Google Sheets API
- **LinkedIn:** LinkedIn API (ha engedélyezve)
- **Email:** Gmail API / SMTP

---

## 📅 Fázisok

### Phase 1: MVP (1-2 hét)
- [ ] Manuális input form
- [ ] PPA Kalkulátor integráció
- [ ] Email template motor
- [ ] Basic n8n workflow

### Phase 2: AI Integrálás (1 hét)
- [ ] Claude API integráció
- [ ] Automatikus LinkedIn keresés
- [ ] Intelligens adatok becslése
- [ ] Dynamic email generálás

### Phase 3: Optimálás (1 hét)
- [ ] A/B tesztelés
- [ ] Conversion rate elemzés
- [ ] Template refinement
- [ ] CRM integráció

---

## 📊 KPI Trackingolás

| Metrika | Target | Notes |
|---------|--------|-------|
| Generálás idő | <60 sec | Végcél |
| Email nyitás | >40% | Industry avg ~30% |
| Click-through | >15% | CTA követés |
| Conversion | >5% | PPA deal |

---

## 🚀 Status

**Jelenlegi:** Design fázis ✅
**Függőség:** PPA Kalkulátor MVP-je (01_PPA-Kalkulátor)
**Következő:** Workflow tervezés

---

## 📝 Megjegyzések

- A LinkedIn API-hez üzleti jóváhagyás szükséges
- Etikus keresési módszerek alkalmazása ajánlott
- GDPR compliance az email marketinghez
- Follow-up automation felépítése szükséges a konverzióhoz

---

## 👤 Felelős

Vad Imre (projekt vezető)

**Utolsó frissítés:** 2026-08-15
