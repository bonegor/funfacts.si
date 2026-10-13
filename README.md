# funfacts.si

A one-page site that shows random fun facts about machine learning, statistics, AI and data science. Plain HTML and JavaScript: no build step, no dependencies.

- `index.html`: the page (styles and script are inline)
- `facts.js`: the list of facts. Each one has a `tag` (the topic shown on the card), its `text`, and optionally a `timeline` of `[year, text]` pairs shown under it.
- `404.html`: shown for any URL that doesn't exist
- `CNAME`: tells GitHub Pages to serve the site at `funfacts.si`

The first fact in `facts.js` is always the one shown when the page opens; every fact after that comes in random order, with no repeats until all have been shown. The share button shares the fact's text along with the site link.

## Run it locally

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Hosting on GitHub Pages

1. **Make the repo public** (Settings → General → Danger Zone → Change visibility). On a free GitHub account, Pages only works for public repos.
2. **Turn on Pages**: Settings → Pages → Build and deployment → Source: *Deploy from a branch*, Branch: `main`, folder `/ (root)` → Save.
3. **Point the domain at GitHub**: at the company you registered `funfacts.si` with, open the DNS settings and add:

   | Type  | Name  | Value                |
   |-------|-------|----------------------|
   | A     | `@`   | `185.199.108.153`    |
   | A     | `@`   | `185.199.109.153`    |
   | A     | `@`   | `185.199.110.153`    |
   | A     | `@`   | `185.199.111.153`    |
   | AAAA  | `@`   | `2606:50c0:8000::153` |
   | AAAA  | `@`   | `2606:50c0:8001::153` |
   | AAAA  | `@`   | `2606:50c0:8002::153` |
   | AAAA  | `@`   | `2606:50c0:8003::153` |
   | CNAME | `www` | `bonegor.github.io`  |

   Delete any existing A/AAAA records on `@` (often a registrar "parking" page) and any existing `www` record first.
4. **Wait, then enable HTTPS**: DNS changes can take from a few minutes to a few hours. Once Settings → Pages shows the DNS check as passed, tick **Enforce HTTPS** (the certificate can take up to an hour to be issued).
5. **Verify the domain** (recommended): your GitHub profile Settings → Pages → Add a domain → `funfacts.si`, and add the TXT record it shows you. This stops anyone else from claiming the domain on GitHub Pages.

After that, every push to `main` updates the site within a minute or two.
