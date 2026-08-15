# 🔍 LinkedIn Adathalászat & Kontakt Gyűjtés

## 📋 Projekt Célja
Automatikus nyilvános ügyfél- és céges adatok lekérése (email, telefon, kontakt) LinkedIn-ről és egyéb forrásbólöl, az automatikus kapcsolatfelvételhez.

**Végcél:** PPA ajánlatgenerátor számára: előfeldolgozott, érvényes kontakt adatok.

---

## 🎯 Források

### 1. LinkedIn (PRIORITÁS)
- [ ] LinkedIn profil adatok kinyerése
- [ ] LinkedIn keresés automatizálása (szűrők: iparág, méret, régió)
- [ ] Elérhetőség lekérés (email/telefon LinkedIn-ből)
- [ ] LinkedIn API integráció (ha lehetséges)
- [ ] LinkedIn scraping (etikus módszer)

### 2. Egyéb Források (Multiplex)
- [ ] Google keresés automatizálása
- [ ] Céges weboldal adatok kinyerése
- [ ] Fórumok (Stack Overflow, GitHub, stb.)
- [ ] Nyilvános adatbázisok
- [ ] Yellow Pages-szerű források
- [ ] Üzleti nyilvántartások

---

## 🔎 Keresési Stratégia

### LinkedIn Keresés Kritériumai
```
Iparág: Energia, Termelés, Gyártás
Méret: 50+ alkalmazott
Régió: Magyarország
Pozíció: CEO, COO, Energy Manager, Procurement
```

### Céges Weboldal Adatok
- About / Elérhetőség oldal
- Csapat / Team szekció
- Blog / Hírek (email signup)

### Nyilvános Adatbázisok
- Cégbíróság (hu)
- KSH (Központi Statisztikai Hivatal)
- OPIK (Országos Pályázati és Projektadatbázis)

---

## 📊 Adatgyűjtés Logika

### 1. Cégek Keresése
```python
# Input: Keresési kritériumok
# Output: Cég lista (1-100 egyezés)

1. LinkedIn search API / Web scraping
2. Weboldal azonosítása
3. Alapadatok gyűjtése
```

### 2. Elérhetőség Keresés
```python
# Input: Cég neve
# Output: Elérhetőség lista

1. Google keresés: "[Cég neve] contact" / "email" / "phone"
2. Weboldal parse-olása
3. LinkedIn profil parse-olása
4. Hunter.io / RocketReach API (opcionális)
```

### 3. Validálás
```python
# Input: Email/Telefon
# Output: Valid/Invalid státusz

1. Email formátum validálás
2. Email verifikáció (send test)
3. Telefon formátum & országkód ellenőrzés
4. Duplikátum eltávolítása
```

---

## 💾 Adatmodell

### CSV Struktúra
```
ceg_id,ceg_neve,iparlog,alkalmazottak,webolda,email,telefon,linkedin_url,verzelt_at,validas
001,XYZ Kft,Energia,150,xyz.hu,contact@xyz.hu,+36123456789,linkedin.com/company/xyz,2026-08-15,valid
```

### Adatok Tárolása
- **CSV:** Local backup
- **Google Sheets:** Cloud szinkro
- **Database:** Opcionális (később)

---

## 🛠️ Technológia

### Python Libraryik
- `selenium` - Web scraping
- `beautifulsoup4` - HTML parse
- `requests` - API hívásoK
- `linkedin-api` vagy `pylinkedin` (nem official)

### API-k
- LinkedIn API (hivatalos - üzleti jóváhagyás szükséges)
- Hunter.io (email finder)
- Google Custom Search API

### n8n Workflows
- Napi LinkedIn keresés
- Email verifikáció
- Duplikátum keresés
- Auto-update Google Sheets

---

## 📋 Implementálási Fázisok

### Phase 1: MVP (2 hét)
- [ ] Google keresés automatizálása
- [ ] Weboldal scraping (contact info)
- [ ] Alapadatok gyűjtés
- [ ] CSV export
- [ ] Manual LinkedIn data

### Phase 2: LinkedIn Integráció (1-2 hét)
- [ ] LinkedIn API research
- [ ] LinkedIn profil lekérés
- [ ] Elérhetőség extrakciók
- [ ] Etikus keresési módszerek

### Phase 3: Validálás & Tisztítás (1 hét)
- [ ] Email validálás
- [ ] Telefon validálás
- [ ] Duplikátum eltávolítás
- [ ] Aktualitás frissítése

### Phase 4: Automatizálás (1 hét)
- [ ] n8n napi keresés workflow
- [ ] Google Sheets szinkro
- [ ] Error handling
- [ ] Alerting

---

## ⚖️ Etikai & Jogi Keretei

### GDPR Compliance
- ✅ Nyilvános adatok gyűjtése OK
- ✅ Céges elérhetőségek OK
- ⚠️ Személyi adatok GDPR kezelés szükséges
- ❌ Scraping tiltott webhelyek (LinkedIn terms)

### LinkedIn Terms of Service
- ❌ Nem engedélyezett: Unauthorized automation
- ⚠️ Szürketermület: Etikus scraping
- ✅ Alternatíva: Hivatalos LinkedIn API (Business jóváhagyás)

### Ajánlott Megközelítés
1. **Hivatalos API** - Ha LinkedIn jóváhagyás érhető el
2. **Web Scraping** - Etikus módszerek, rate limiting
3. **Email Finder szervizek** - Hunter.io, RocketReach
4. **Nyilvános adatbázisok** - Cégbíróság, Yellow Pages

---

## 📊 Kimeneti Metrikák

| Metrika | Target |
|---------|--------|
| Napi gyűjtött kontakt | 50+ |
| Érvényes email % | >70% |
| Érvényes telefon % | >60% |
| Feldolgozási idő/kontakt | <5 sec |

---

## 🚀 Status

**Jelenlegi:** Design & Research fázis ✅
**Blocker:** LinkedIn API jóváhagyás (üzleti döntés)
**Következő:** Prototype web scraping (non-LinkedIn)

---

## 📝 Kockázatok

1. **LinkedIn politika** - Scraping ban kockázata
2. **Adatvédelem** - GDPR és egyéb szabályozások
3. **Adat minőség** - Elavult vagy hamis adatok
4. **Etika** - Spam-szerű megközelítés elkerülése

**Megoldás:** Fókusz az etikus módszerekre + nyilvános API-kra

---

## 👤 Felelős

Vad Imre (projekt vezető)

**Utolsó frissítés:** 2026-08-15
