# Van der Burg Coaching — website

Statische website, gehost op GitHub Pages: <https://rjvdburg.github.io/vanderburgcoaching/>

## ✏️ Bewerken (CMS)

Deze site wordt beheerd met de losse, herbruikbare **Stateless CMS**-engine. Start de CMS
voor déze site via:

**→ <https://rjvdburg.github.io/stateless-cms/?repo=RJvdBurg/vanderburgcoaching>**

Je GitHub-token en Gemini-sleutel blijven lokaal in je browser (localStorage) — die staan nooit in een repo.

## Twee config-bestanden

| Bestand | Configureert | Voorbeelden |
|--------|--------------|-------------|
| [`cms.config.json`](cms.config.json) | de **CMS-tool** | site-naam, GA-id, AI-prompt, images-map |
| [`site.json`](site.json) | de **zichtbare chrome** (header/footer) | merk, logo, menu, footer/NAP, socials, WhatsApp |

Het logo en andere merk-assets staan in [`assets/`](assets/) van **deze** repo (site-specifiek).

## Architectuur

| Repo | Rol |
|------|-----|
| [`stateless-cms`](https://github.com/RJvdBurg/stateless-cms) | Herbruikbare CMS-engine (Pages) |
| [`vanderburg-theme`](https://github.com/RJvdBurg/vanderburg-theme) | Gedeeld design — `theme.css` + `theme.js` + generieke default-assets (Pages) |
| `vanderburgcoaching` (deze repo) | Content-pagina's + `assets/` + `cms.config.json` + `site.json` |

Elke pagina linkt `theme.css` en `theme.js` van het theme via absolute URL. `theme.js` leest
`site.json` en bouwt daarmee de header/footer/WhatsApp — dus **één theme kan meerdere sites
aansturen**. Een nieuwe site = eigen content + eigen `assets/` + eigen `site.json`.

Alles is volledig statisch en draait op GitHub Pages — geen build-stap, geen backend.

> Doel op termijn: de CMS bakt het theme + `site.json` + content bij publiceren in tot
> **self-contained platte HTML** (inline CSS, vaste header/footer) — dan is er ook geen
> runtime-afhankelijkheid van het theme meer.
