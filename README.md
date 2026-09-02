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

De gepubliceerde pagina's zijn **platte, self-contained HTML**: theme.css staat inline, de
header/footer/WhatsApp zijn vast ingebakken, en er is **geen** runtime-afhankelijkheid van de
theme-repo. 10-jaar-proof.

Het theme (`theme.css` + `theme.js` + `site.json`) is de **bron** waaruit gebakken wordt — niet
iets dat de live site op runtime ophaalt. Werkwijze:

- **Content wijzigen** → bewerk de pagina in de CMS en publiceer.
- **Design/menu/footer wijzigen** → pas `site.json` of `theme.css`/`theme.js` aan en klik in de
  CMS op **🧱 Platte HTML** → alle pagina's worden opnieuw gebakken (de `<main>`-content blijft).

Zo stuurt **één theme meerdere sites** aan (elke site eigen `site.json` + `assets/`), terwijl de
output altijd platte HTML op GitHub Pages is — geen build-toolchain, geen backend.
