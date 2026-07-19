# Diagnosis: Landing page inventory vs current product

**Scope:** Read-only inventory of the live landing source. No code changes. Assembly engine / recipes not touched.

**Source of truth for this report:** `index.html` (root), plus `assets/` and media URLs referenced by that file. Checked 2026-07-19.

---

## 1. Location and section order

| Item | Fact |
|------|------|
| **File** | `/index.html` (static single-page HTML) |
| **Route** | Site root `/` (Vercel static deploy; `vercel.json` is `{}`) |
| **Stack** | Hardcoded HTML/CSS/JS in one file — no CMS, no copy JSON, no framework page |

### Distinct sections in DOM order

1. **Nav (header)** — logo, Log ind, Kom i gang  
2. **Hero** — headline, subheadline, two CTAs  
3. **Trade marquee** — “Bygget til danske håndværkere” + scrolling trades  
4. **Problem / pain** — four pain cards  
5. **Follow-up (OPFØLGNING)** — auto SMS day 4/8 + screenshot  
6. **Follow-up proof (“Ikke bare opfølgning”)** — mersalg + genaktiver screenshots  
7. **How it works / demo video** — phone shell + MP4  
8. **Showcase STEP 1 (voice)** — “Tal om opgaven…” + record animation (no screenshot)  
9. **Price guide (PRISGUIDE)** — pricing-from-data + screenshot  
10. **Customer offer** — link + one-tap accept + `quote-preview.png`  
11. **Showcase AUTOMATISK** — SMS stack + “Systemet arbejder…”  
12. **Features grid** — “Alt hvad du behøver” (9 feature cards)  
13. **ROI bar** — three value lines  
14. **Pricing** — Start / Plus / Pro  
15. **Lead capture CTA** — “Ring mig op” phone form  
16. **Footer**

### Not present on the page

- No **FAQ** section  
- No **testimonials** section (CSS comment `/* Beta statement (former testimonials) */` remains; no corresponding markup)  
- No dedicated **stat strip** section (CSS for `.stat-section` exists; unused in body)

---

## 2. Current copy by section (quoted)

### Meta / title

- **`<title>`:** `Mesterpakken – Tilbud og opfølgning for håndværkere`
- **meta description:** `Tal om opgaven. Tilbuddet er klar til kunden. Mesterpakken er voice-to-quote til danske håndværkere.`
- **og:description:** `Voice-to-quote SaaS til danske håndværkere. Spar tid og vind flere opgaver.`

### Nav

- Brand: `Mesterpakken`
- Links: `Log ind` → `https://mesterpakken.dk`
- CTA: `Kom i gang` → Stripe Start checkout

### Hero

- **Headline:** `Du er håndværker. Ikke sælger.`
- **Subheadline:** `Tal opgaven ind efter besigtigelse på sekunder. Kunden modtager et professionelt tilbud med det samme — og Mesterpakken følger automatisk op, så varme tilbud ikke går tabt.`
- **CTAs:** `Se hvordan det virker` · `Prøv det på din næste opgave`

### Trade marquee

- Label: `Bygget til danske håndværkere`
- Trades: `Tømrer` · `Maler` · `Murer` · `Tagdækker` · `Gulvlægger` · `Snedker`

### Problem

- **H2:** `Det her koster håndværkere opgaver hver uge`
- **Lead:** `De fleste taber ikke opgaver på deres håndværk — men på manglende opfølgning og manglende overblik.`
- Cards:
  - `Du sender tilbuddet — og kunden forsvinder`
  - `Du priser efter mavefornemmelse — og ved aldrig om det koster dig opgaven`
  - `Du glemmer at følge op — og opgaven går til en anden`
  - `Du mister overblikket over hvem der venter, og hvem der er tabt`

### Follow-up (OPFØLGNING)

- Eyebrow: `OPFØLGNING`
- **H2:** `De fleste følger aldrig op. Det er der penge i.`
- Body: `Mesterpakken sender automatisk en SMS dag 4 og dag 8 hvis kunden ikke har svaret. Du bestemmer selv dagene. Ingen opgaver falder mellem stolene — og du behøver ikke huske noget.`

### Follow-up proof

- **H2:** `Ikke bare opfølgning`
- Captions:
  - `Tilføj valgfrie tilkøb — kunden slår til med ét tryk`
  - `Kunder du ikke har hørt fra i 6+ måneder — én SMS henter dem tilbage`

### How it works / video

- **H2:** `Lav tilbud på sekunder — ikke minutter`
- Video: Supabase `landing-assets/MESTER%20(2).mp4` (no body copy beyond heading)

### Showcase STEP 1 (voice)

- Eyebrow: `STEP 1`
- **H2:** `Tal om opgaven. Det er nok.`
- Copy: `Tryk optag. Beskriv opgaven med din stemme. 60 sekunder er nok — inde fra bilen, på byggepladsen, hvor som helst.`

### Price guide

- Eyebrow: `PRISGUIDE`
- **H2:** `Skift mavefornemmelsen ud med data.`
- Body: `Bag hvert tilbud ligger data fra dine egne vundne og tabte opgaver. Jo mere du bruger systemet, jo skarpere bliver estimaterne. Du sætter den rigtige pris fra dag ét — og systemet bliver klogere for hver opgave.`

### Customer offer

- **H2:** `Kunden åbner et link — og accepterer med ét tryk`
- Sub: `Ingen app. Ingen login. Ingen forvirring.`

### Showcase AUTOMATISK

- Eyebrow: `AUTOMATISK`
- **H2:** `Systemet arbejder mens du er på byggepladsen`
- Copy: `Du får besked når en kunde ikke har svaret, når et tilbud bliver accepteret, og når det er tid til at bede om en anmeldelse. Du behøver ikke huske noget.`

### Features (“Alt hvad du behøver”)

- Lead: `Mesterpakken arbejder for dig — også når du ikke er i appen.`

| Feature title | Description |
|---------------|-------------|
| Stemmeoptagelse | Fra tale til professionelt tilbud på under 2 minutter — ingen tastatur nødvendig. |
| SMS til kunden | Kunden modtager et link og accepterer uden at downloade noget. Det hele sker på 30 sekunder. |
| Automatiske påmindelser | Systemet sender dig en SMS dag 4 og dag 8 hvis kunden ikke har svaret — du bestemmer selv dagene. Du glemmer aldrig en opgave igen. |
| Sæt den rigtige pris første gang | Systemet lærer hvad du normalt vinder til. Næste gang du prissætter en terrasse ved du præcis hvor du skal ligge. |
| Få gamle kunder tilbage | Kunder du ikke har hørt fra i 6 måneder får en personlig SMS. Tidligere kunder køber igen — hvis du husker dem. |
| Få anmeldelser automatisk | 30 dage efter en vundet opgave sender systemet en SMS og beder om en Google-anmeldelse. Du behøver ikke tænke på det. |
| Pipeline overblik | Se alle dine tilbud samlet — hvad der venter, hvad der er sendt, vundet og tabt. Aldrig mere rod i indbakken. |
| Fast pris | Slå til på hvert tilbud. Kunden ved præcis hvad de betaler — og accepterer hurtigere. |
| Mersalg i tilbuddet | Tilføj valgfrie tilkøb kunden selv kan slå til — helårsolie, ekstra rum, udvidet garanti. Du sælger mere uden at sige et ord. |

### ROI bar

- `Én opgave mere om måneden betaler det hele`
- `Én opfølgning er ofte forskellen på ja og ingenting.`
- `Skift mavefornemmelsen ud med data.`

### Pricing

- **H2:** `Vælg den pakke der passer`
- Lead: `Ingen binding. Start småt — eller få hjælp hele vejen fra dag ét.`

**Start**

- `999 kr oprettelse` · `499 kr` `/md`
- Terms: `Ingen binding · 30 dages tilfredshedsgaranti ved aktiv brug`
- Checklist: Kom i gang på 10 minutter · Tilbud fra telefon på 2 minutter · Automatisk opfølgning på ubesvarede tilbud · SMS-besked når kunde åbner dit tilbud · Pipeline & overblik · Kundehistorik
- Desc: `Perfekt til mindre håndværksvirksomheder der vil spare tid og følge bedre op.`
- CTA: `Kom i gang` → Stripe `eVqbJ1eUM4k8aoa1oq6Ri02`

**Plus** (badge: `Mest valgt`)

- `2.999 kr oprettelse` · `999 kr` `/md`
- Terms: `Ingen binding`
- Includes: `Alt i START +` — Vi læser dine tidligere tilbud ind · Systemet kender dine egne priser — ikke standardpriser · Præcise tilbud fra første dag · Prioriteret support
- Desc: `Perfekt til virksomheder der vil have tilbud der rammer plet fra dag ét — bygget på deres egne priser, ikke standardpriser.`
- CTA: `Vælg PLUS` → Stripe `dRmaEX2808Ao1RE4AC6Ri03`

**Pro**

- `9.999 kr oprettelse` · `1.999 kr` `/md`
- Includes: `Alt i PLUS +` — Hjemmeside med leadformular · Integration af leads til Mesterpakken · Custom opsætning og branding · Fast månedlig sparring · Komplet lead- og tilbudsflow
- Desc: `Vi bygger hele setup'et for jer — tilbud, opfølgning og leadflow samlet ét sted.`
- CTA: `Kontakt os` → `mailto:kontakt@mesterpakken.dk`

### Lead capture

- **H2:** `Vil du se det før du beslutter dig?`
- Sub: `Skriv dit nummer. Mathias ringer dig op — ingen salgssnak, bare en kort gennemgang.`
- Button: `Ring mig op` · Note: `Vi ringer normalt tilbage samme dag`

### Footer

- Tagline: `Spar tid. Vind flere opgaver.`
- `Log ind` · `kontakt@mesterpakken.dk` · `+45 22 44 00 80`
- `© 2026 Mesterpakken · Alle rettigheder forbeholdes`

### Dead / unused JS copy (not rendered)

- Script still defines typewriter string `Professionelle tilbud på 2 minutter` targeting `#type-target`, but that element is **not** in the hero markup — so it never appears.

---

## 3. Outdated / mismatch flags vs stated current product

### Pricing — START 999 setup + 499/md

| Check | Result |
|-------|--------|
| START numbers | **Match.** Page shows `999 kr oprettelse` and `499 kr /md`. |
| Also on page | Plus `2.999` + `999/md`, Pro `9.999` + `1.999/md` — not contradicted by the START-only current price you stated; still present as marketed tiers. |

### Positioning — “Du er håndværker. Ikke sælger.” / sales-engine angle

| Check | Result |
|-------|--------|
| Hero headline | **Matches** exactly: `Du er håndværker. Ikke sælger.` |
| Angle | Page leans sales-engine: follow-up SMS, reopen lost customers, mersalg/tilvalg, reviews, pipeline — not pure “quote tool only.” |

### Features: present, thin, or missing vs capabilities you listed

| Capability (your list) | On page today? |
|------------------------|----------------|
| **Voice → quote** | **Yes** — hero, STEP 1, feature “Stemmeoptagelse”, demo video, meta “voice-to-quote”. |
| **Follow-up on sent quotes** | **Yes** — dedicated OPFØLGNING section, feature “Automatiske påmindelser”, pricing Start checklist, AUTOMATISK showcase. |
| **Customer-facing offer** | **Partially** — section “Kunden åbner et link…” + `quote-preview.png`. Copy stresses one-tap accept / no app. |
| **Phase-by-phase customer offer** | **Not named.** No “fase”, “fase-for-fase”, or phase structure in copy. Screenshot shows flat `TILBUDSLINJER` table + `TILVALG`, not an explicit phase breakdown. |
| **Meaning dictionary / craft-word understanding** | **Absent.** No mention of dictionary, fagord, or that the system understands craft language beyond “tal om opgaven”. |

Other product claims on the page (not in your “missing” list, but inventory): price learning from won/lost jobs, genaktivering after 6+ months, Google review SMS after 30 days, pipeline, fast pris, mersalg/tilvalg, Plus “read prior quotes”, Pro website/leads.

Possible stale/example-specific wording:

- Feature example: “næste gang du prissætter **en terrasse**…” — terrasse-specific, not craft-neutral.
- Mersalg examples: “helårsolie, ekstra rum, udvidet garanti”.

### Screenshots / images — source and age risk

**Used on the live page**

| Asset | Source | File dates / notes |
|-------|--------|-------------------|
| `logo.png` | Local root | Apr 10 |
| `assets/mersalg.png` | Local | May 13 — craftsman-side “VALGFRIE TILKØB” UI |
| `assets/quote-preview.png` | Local | May 13 — customer offer UI (flat line items + tilvalg + “Godkend tilbud”); sample job is træterrasse |
| `screen-4-opfolg-kritisk.png` | Supabase `landing-assets/` | Same filename also in local `assets/` dated Apr 10 |
| `screen-6-genaktiver.png` | Supabase | Local twin Apr 10 |
| `screen-raatilbud.png` | Supabase | Local twin Apr 10 |
| `screen-sms-crop.png`, `screen-sms-accept.png`, `screen-sms-reference.png` | Supabase | Local twins Apr 10 |
| Demo video `MESTER (2).mp4` | Supabase only | Static remote file; UI age unknown without opening video |

**Risk:** All product UI visuals are **static files** (local PNG or fixed Supabase public URLs). They do **not** update with the live app. Anything redesigned after ~Apr–May 2026 capture dates would look old until assets are replaced. Supabase URLs can be swapped server-side without a git change; local `assets/` cannot.

**Local files present but not referenced by `index.html`** (old/extra inventory): e.g. `screen-1-optag.png`, `screen-3-kunder.png`, `screen-5-opfolg-reference.png`, `screen-6-sms.png`, `screen-7-accepter.png`, `screen-8-screen.png`, `kundes-tilbud*.png`, `lang-tilbud-kunde.png`, `raat-tilbud.png`, `IMG_5224/5225.PNG` — mostly Apr 10.

### Target audience wording

- **Craft-neutral / multi-trade**, not anlæg-specific: “håndværkere”, marquee lists tømrer/maler/murer/tagdækker/gulvlægger/snedker.
- **No** “anlæg” / landscaping trade name on the page.
- **Example content** in screenshots/features skews outdoor/carpentry (terrasse, helårsolie) rather than pure craft-neutral demos.

---

## 4. Hardcoded copy vs data-driven

| Content | How it is sourced |
|---------|-------------------|
| All headlines, feature text, pricing numbers, CTAs, footer | **Hardcoded** in `index.html` |
| Trade marquee list | **Hardcoded** HTML |
| Images / video paths | **Hardcoded** `src` attributes (local or Supabase URLs) |
| Pricing amounts | **Hardcoded** in HTML (not fetched from Stripe) |
| Lead form | Phone submitted via `fetch` to Supabase REST `leads` — **does not pull** marketing copy |
| Typewriter / steps JS | Leftover script for DOM nodes that are **not** in the page; no external content feed |

**Verdict:** Entire landing narrative and pricing display are static HTML. Nothing is pulled from a CMS or product API for copy.

---

## Rewrite decision checklist (facts only)

- START price on page **already matches** 999 + 499/md.  
- Positioning headline **already matches** “Du er håndværker. Ikke sælger.”  
- Voice→quote and follow-up are **already central**.  
- Gaps vs your current-product list: **phase-by-phase offer** (unnamed), **meaning dictionary** (unmentioned).  
- Visuals are **static** (Apr–May vintage locally; remote twins on Supabase) — primary place UI drift would show.  
- No FAQ / testimonials to rewrite; those sections do not exist in markup.
