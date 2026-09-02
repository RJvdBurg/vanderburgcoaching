# Van der Burg Coaching — website

Statische website, gehost op GitHub Pages: <https://rjvdburg.github.io/vanderburgcoaching/>

De gepubliceerde pagina's zijn **platte, self-contained HTML**: `theme.css` staat inline, de
header/footer/WhatsApp zijn vast ingebakken, en er is **geen** runtime-afhankelijkheid van de
theme-repo. 10-jaar-proof.

## ✏️ Bewerken (CMS)

Beheerd met de losse, herbruikbare **Stateless CMS**-engine. Start voor déze site via:

**→ <https://rjvdburg.github.io/stateless-cms/?repo=RJvdBurg/vanderburgcoaching>**

Je GitHub-token en Gemini-sleutel blijven lokaal in je browser (localStorage) — nooit in een repo.

### Werkwijze

| Wil je wijzigen… | Doe je… |
|------------------|---------|
| **Pagina-content** | bewerk de pagina in de CMS → publiceer |
| **Design / menu / footer / logo / kleuren** | open **🎨 Theme Builder** in de CMS → pas aan met live preview → **🧱 Bak & publiceer** |

De **Theme Builder** bewerkt `site.json` (chrome) en de theme-kleuren/fonts (`theme.css`) visueel.
Bij publiceren "bakt" de CMS het theme + `site.json` + content in tot platte HTML.

> Sinds de pagina's plat zijn, verandert een aanpassing aan `site.json`/`theme.css` de live site
> pas na één keer **🧱 Bak & publiceer** (dat is de build-stap, in de browser).

## Config-bestanden

| Bestand | Configureert | Voorbeelden |
|--------|--------------|-------------|
| [`cms.config.json`](cms.config.json) | de **CMS-tool** | site-naam, GA-id, AI-prompt, images-map, `themeBase` |
| [`site.json`](site.json) | de **zichtbare chrome** | merk, logo, menu, footer/NAP, socials, WhatsApp |

Merk-assets (logo's, favicon) staan in [`assets/`](assets/) van **deze** repo (site-specifiek).

## Architectuur (3 repo's, 100% statisch, alles op GitHub Pages)

| Repo | Rol |
|------|-----|
| [`stateless-cms`](https://github.com/RJvdBurg/stateless-cms) | Herbruikbare CMS-engine + Theme Builder |
| [`vanderburg-theme`](https://github.com/RJvdBurg/vanderburg-theme) | Design-bron: `theme.css` + `theme.js` + defaults |
| `vanderburgcoaching` (deze repo) | Platte pagina's + `assets/` + `cms.config.json` + `site.json` |

Eén theme kan meerdere sites aansturen (elke site eigen `site.json` + `assets/`). Geen
build-toolchain, geen backend — output is altijd platte HTML op GitHub Pages.
