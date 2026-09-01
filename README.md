# Van der Burg Coaching — website

Statische website, gehost op GitHub Pages: <https://rjvdburg.github.io/vanderburgcoaching/>

## ✏️ Bewerken (CMS)

Deze site wordt beheerd met de losse, herbruikbare **Stateless CMS**-engine. Start de CMS
voor déze site via:

**→ <https://rjvdburg.github.io/stateless-cms/?repo=RJvdBurg/vanderburgcoaching>**

De CMS leest de site-instellingen uit [`cms.config.json`](cms.config.json). Je GitHub-token en
Gemini-sleutel blijven lokaal in je browser (localStorage) — die staan nooit in een repo.

## Architectuur

| Repo | Rol |
|------|-----|
| [`stateless-cms`](https://github.com/RJvdBurg/stateless-cms) | Herbruikbare CMS-engine (Pages) |
| [`vanderburg-theme`](https://github.com/RJvdBurg/vanderburg-theme) | Gedeeld design — `theme.css` (Pages) |
| `vanderburgcoaching` (deze repo) | De content-pagina's + `cms.config.json` |

Elke pagina linkt het design via `<link href="https://rjvdburg.github.io/vanderburg-theme/theme.css">`.
Alles is volledig statisch en draait op GitHub Pages — geen build-stap, geen backend.
