---
type: research
area: work
topic: app-builder
status: draft
created: 2026-01-29
---

# Frontend-/App-Builder Alternativen (Store-fähiges Produkt)

Ziel: **echtes Produkt**, **1–2 Devs**, Timeline **≥ 2 Monate**, Veröffentlichung über **Google Play / Apple App Store**.  
Fokus: schneller Output ohne UI-Design-Overhead, aber mit sauberem Weg zu wartbarem Code.

---

## Vergleichsmatrix

| Tool         |                                                                         Kosten (Listenpreis) | Speed (MVP)             | Code-Export                 | Hosting                          | Auth/DB-Integrationen                                   | Mobile-Tauglichkeit / Store                          |
| ------------ | -------------------------------------------------------------------------------------------: | ----------------------- | --------------------------- | -------------------------------- | ------------------------------------------------------- | ---------------------------------------------------- |
| **Lovable**  | Business: **$50/Monat**; Credits-Topups: Pro **$15/50 Credits**, Business **$30/50 Credits** | sehr hoch               | **ja** (GitHub/Repo)        | Lovable hosting + extern möglich | **Supabase nativ**                                      | Web-first; Store typ. via Wrapper (Hybrid)           |
| **Cursor**   |                                     Pro **$20**, Pro+ **$60**, Ultra **$200** / User / Monat | mittel–hoch             | **ja** (Repo-first)         | extern (Vercel/Render/etc.)      | beliebig (selbst integriert)                            | **sehr gut** für echte native Apps (RN/Expo/Flutter) |
| **Bolt.new** |                                                             Free **$0**, Teams **$30/Monat** | sehr hoch               | ja (Projektdateien/Export)  | Bolt Cloud                       | Plattform-Stack (DB/Auth in Bolt Cloud)                 | Web-first; Store typ. via Wrapper (Hybrid)           |
| **Replit**   |                           Core **$20/Monat** (jährlich), Teams **$35/User/Monat** (jährlich) | hoch                    | **ja**                      | **ja** (Publish/Deploy)          | Replit Auth/DB + Integrationen je nach Stack            | gut für RN/Expo Builds; kein UI-Designer             |
| **Softr**    |            Basic **$49/$59**, Pro **$139/$167**, Business **$269/$323** (jährlich/monatlich) | sehr hoch (Portal/CRUD) | **nein**                    | ja                               | Data-source Connector Fokus (Sheets/Airtable/REST etc.) | primär Web; Store nur indirekt/Wrapper               |
| **Bubble**   |                      Starter **$59**, Growth **$209**, Team **$549** / Monat (annual billed) | hoch                    | **kein echter Code-Export** | ja                               | All-in-one (DB/Workflows/Auth)                          | Store möglich (Bubble bewirbt Web + Mobile)          |

---

## Kurzbewertung pro Tool (für Store-Produkt)

### Lovable
- Stärke: extrem schnell von 0 → UI + CRUD + Supabase (Auth/DB/RLS).
- Risiko: Web-first; Store-Release üblicherweise über Hybrid-Wrapper. Langfristig sinnvoll als Bootstrap, nicht als Endzustand.

### Cursor
- Stärke: repo-first, saubere Engineering-Basis (Tests/CI/Release, refactoring, Code Review).
- Nachteil: kein “UI-Design per Klick”; UI kommt über Komponentenbibliotheken/Design-System (z. B. RN UI Kit, Tailwind/shadcn für Web).

### Bolt.new
- Stärke: AI-first Builder + Cloud, schnell wie Lovable.
- Risiko: Plattform-Stack; für langfristige Codepflege zählt Exportqualität und Repo-Workflow.

### Replit
- Stärke: Cloud-IDE + Deploy in einem, gut für schnelle Iteration im echten Code.
- Nachteil: kein UI-Builder; UI-Qualität hängt an euren Komponenten/Kits.

### Softr
- Stärke: sehr schnell für Data-Portale.
- Risiko: für ein eigenständiges Consumer-Produkt meist zu eng; kein echter Code-Export.

### Bubble
- Stärke: mächtig ohne klassischen Code, Store möglich.
- Risiko: Lock-in (kein echter Quellcode-Export), Workload/Plankosten, spätere Migration teuer.

---

## Empfehlung (konkret)

1) **Cursor + React Native (Expo) + UI-Kit**  
   - Ziel: echte native App, stabiler Store-Flow, langfristig wartbar.

2) **Lovable (oder Bolt) nur als Beschleuniger für Prototyping / UI-Scaffolding**  
   - Danach Code in Repo übernehmen und dort weiterarbeiten.

3) **Replit** als Alternative, wenn “Cloud-IDE + Deploy” im Team bevorzugt wird  
   - Besonders sinnvoll bei einfacher Infra und schneller Iteration im Code.

Bubble/Softr nur, wenn Lock-in/No-code bewusst akzeptiert wird und die App primär Portal-Charakter hat.

---

## Warum frühe Migration in ein eigenes Repo wichtig ist

- **Reviewbarkeit:** Änderungen sind als Git-Diff nachvollziehbar (statt Prompt-Historie).  
- **Testbarkeit:** Unit/Integration-Tests, Linting, Typechecks, CI/CD werden erst mit Repo-Workflow praktikabel.  
- **Store-Builds:** iOS/Android Signing, Xcode/Gradle-Fixes, Release-Automation brauchen reproduzierbare Builds.  
- **Skalierbarkeit der Zusammenarbeit:** Branches/PRs/Code-Reviews sind Standard für 2 Devs, auch bei kleiner Codebase.  
- **Kosten- und Risiko-Kontrolle:** weniger “Prompt-Drift”, weniger Credit-Burn durch Trial-and-Error, saubereres Refactoring.
