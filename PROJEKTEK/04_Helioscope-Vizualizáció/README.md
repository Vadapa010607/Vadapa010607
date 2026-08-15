# 🎨 HelioScope Integráció - Napelem Projekt Vizualizáció

## 📋 Projekt Célja
Napelem projektek automatikus vizualizálása SVG-ben + interaktív HTML, drónfotó vagy Google Earth képek alapján.

**Végcél:** Vizuális ajánlat az ügyféleknek email-ben, PDF-ben vagy online.

---

## 🎯 Workflow

```
1. INPUT: Drónfoto vagy Google Earth kép + GPS
                    ↓
2. PARAMÉTEREK MEGADÁSA
   - GPS koordináták
   - Napelem teljesítmény (kW)
   - Tárolo kapacitás (kWh)
   - Elrendezés (sorok, oszlopok)
   - Becsült ár
                    ↓
3. CLAUDE SVG RAJZ (Automatikus)
   - Terület észrevétele
   - Panel elrendezés kalkukálása
   - SVG rajz generálása
                    ↓
4. INTERAKTÍV HTML VIZUALIZÁCIÓ
   - 3D nézet (threejs vagy hasonló)
   - Info sávok (termelés, költség, CO2)
   - Zoom & Pan funkciók
                    ↓
5. EXPORT & KÜLDÉS
   - PDF generálás
   - HTML email
   - Online link
                    ↓
6. ÜGYFÉL EMAIL
   - Vizuális ajánlat
   - Kattintható elemek
   - CTA gombos
```

---

## 📥 Input Paraméterek

### Képi Adat
| Parameter | Forrás | Formátum |
|-----------|--------|----------|
| Épület fotó | Drón vagy Google Earth | JPG/PNG |
| GPS координátes | Geolocation | LAT/LON |
| Térkép vetület | Google Maps API | Raster |

### Projekt Paraméterek
| Paraméter | Típus | Példa |
|-----------|-------|-------|
| Napelem teljesítmény | kW | 30 |
| Tárolo kapacitás | kWh | 50 |
| Panel méret | m² | 75 |
| Elrendezés | sorok×oszlopok | 5×3 |
| Becsült ár | Ft | 8,500,000 |
| ROI idő | év | 10 |

---

## 🎨 SVG Rajz Generálása

### Claude AI Prompt
```
"Generálj egy SVG napelem-elrendezést a következő paraméterek alapján:
- Épület terület: [GoogleMaps képből extrahálva]
- Tetőcserép terület: [m²]
- Napelem: [30 kW = 75 m²]
- Panel: 400W, 1.6×1.0m
- Elrendezés: 5 sor × 3 oszlop
- Orientáció: 180° (Dél)
- Dőlés: 35°
- Terület: Zöld = szabad, Piros = árnyék, Kék = panel

Output: Professzionális SVG, léptékhelyes"
```

### SVG Output Elemek
```xml
<svg width="800" height="600">
  <!-- Épület alaprajz -->
  <polygon points="..." fill="#e0e0e0" stroke="black"/>
  
  <!-- Árnyék zóna -->
  <polygon points="..." fill="#ff6b6b" opacity="0.5"/>
  
  <!-- Napelem panel -->
  <g id="panel-row-1">
    <rect x="50" y="50" width="160" height="100" fill="#4a90e2" stroke="black"/>
    <text x="80" y="105">400W</text>
  </g>
  
  <!-- Tájolás jelzés -->
  <text x="700" y="50" font-size="24">↓ DÉL</text>
  
  <!-- Léptékcikk -->
  <line x1="50" y1="550" x2="250" y2="550" stroke="black"/>
  <text x="130" y="575">10 méter</text>
</svg>
```

---

## 🌐 HTML Interaktív Vizualizáció

### Keretrendszer
- **Frontend:** Vue.js / React
- **3D Render:** Three.js (opcionális)
- **Responsív:** Bootstrap / Tailwind CSS

### Info Panel Tartalom
```html
<div class="info-panel">
  <h2>Napelem Projekt Overview</h2>
  
  <div class="metrics">
    📊 Teljesítmény: 30 kW
    ⏰ Évi termelés: 36 MWh
    💰 Becsült ár: 8,5 M Ft
    📈 ROI: 8% / 10 év
    🌱 CO₂ spórolás: 10 tonna/év
  </div>
  
  <div class="cta">
    <button class="btn-primary">PDF Letöltés</button>
    <button class="btn-secondary">Kapcsolatfelvétel</button>
  </div>
</div>
```

---

## 📧 Email Integráció

### HTML Email Template
```html
<body style="font-family: Arial, sans-serif; background: #f5f5f5;">
  <div style="max-width: 600px; margin: 0 auto; background: white;">
    
    <h1>Napelem PPA Ajánlat - [Cégnév]</h1>
    
    <!-- Beágyazott SVG vagy képként -->
    <img src="cid:solar-diagram" alt="Napelem elrendezés" width="100%">
    
    <!-- Info panel -->
    <div style="padding: 20px; background: #f9f9f9;">
      <p><strong>30 kW</strong> napelem + 50 kWh tárolo</p>
      <p>Évi termelés: <strong>36 MWh</strong></p>
      <p>Ár: <strong>8,5 M Ft</strong></p>
    </div>
    
    <!-- CTA -->
    <a href="https://offering.example.com/quote/ABC123" 
       style="display: inline-block; padding: 15px 30px; 
              background: #4a90e2; color: white; 
              text-decoration: none; border-radius: 5px;">
      Megtekintés & Aláírás
    </a>
  </div>
</body>
```

---

## 🛠️ Technológia Stack

| Komponens | Technológia |
|-----------|------------|
| Képelemzés | Claude Vision API |
| SVG generálás | Claude API + SVG.js |
| GPS/Térkép | Google Maps API |
| 3D render (opt.) | Three.js |
| Frontend | Vue.js + Tailwind CSS |
| Email | n8n + SendGrid |
| PDF export | PDFKit (Node.js) |
| Hosting | Vercel / Firebase |

---

## 📋 Implementálási Fázisok

### Phase 1: MVP (1-2 hét)
- [ ] Static SVG generálás (manuális paraméterek)
- [ ] HTML template
- [ ] Email integráció
- [ ] Tesztelés 3-5 projekttel

### Phase 2: Claude AI Integráció (1 hét)
- [ ] Claude Vision API integrálása
- [ ] Automatikus terület-felismerés
- [ ] SVG auto-generálás
- [ ] Intelligens panel elrendezés

### Phase 3: Interaktivitás (1 hét)
- [ ] Vue.js frontend
- [ ] 3D nézet (opcionális)
- [ ] Dinamikus paraméter módosítás
- [ ] Online link megosztás

### Phase 4: Produktionizálás (1 hét)
- [ ] Performance optimálás
- [ ] Mobile responsivitás
- [ ] PDF export
- [ ] Analytics tracking

---

## 📊 Kimeneti Formátumok

### 1. **PDF Ajánlat**
   - Nyomtatható
   - Digitális aláírás lehetőség
   - Email melléklet

### 2. **HTML Email**
   - Interaktív elemek
   - Kattintható CTA
   - Beágyazott képek

### 3. **Online Link**
   - Módosítható paraméterek
   - Megosztható linkek
   - Analytics tracking

### 4. **SVG Exportálás**
   - CAD-ba importálható
   - Mérnöki rajzokhoz
   - Helyszín felméréshez

---

## 🚀 Integráció az Adathalászattal

```
Google keresés + Drón/Map → Paraméterek → SVG → Email Ajánlat → Ügyfél
        ↓
   Cégadatok (LinkedIn)
        ↓
   PPA Kalkulátor
        ↓
   Vizualizáció
        ↓
   Automatikus email
```

---

## 🎬 Felhasználási Eset

**Forgatókönyv:**
1. Ügyfél: XYZ Kft (gyártó cég, Debrecen)
2. Google keresés: "XYZ Kft napelem"
3. LinkedIn: Termelés 50 MWh/év
4. Drón fénykép: 250 m² tetőterület
5. Kalkulátor: 30 kW napelem + 50 kWh tárolo → 8,5 M Ft
6. Vizualizáció: SVG + HTML generálás
7. Email: Ajánlat küldés CEO-nak
8. Follow-up: CRM tracking

---

## 🚀 Status

**Jelenlegi:** Koncepció ✅
**Prototype:** Design fázis
**Következő:** Mock-up HTML elkészítése

---

## 📝 Megjegyzések

- Google Maps API jóváhagyás szükséges
- Claude Vision API költségei figyelembevétele
- PDF export library kiválasztása
- Email template tesztelése több kliensben

---

## 👤 Felelős

Vad Imre (projekt vezető)

**Utolsó frissítés:** 2026-08-15
