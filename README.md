# technocore.one

Static one-page site for Technocore Inc. No build step, no dependencies, no third-party requests.

```
index.html    landing page (anchor sections)
privacy.html  privacy policy
styles.css    all styles
favicon.svg
CNAME         custom domain for GitHub Pages
.nojekyll     serve files as-is
```

Local preview: `python3 -m http.server 8787` → http://127.0.0.1:8787

## Before publishing

Replace the highlighted placeholders (`grep -n 'class="todo"' index.html`):
- Delaware file number
- EIN

## Deploy (GitHub Pages)

1. Verify the domain: github.com/settings/pages → Add a domain → `technocore.one`.
   Add the TXT record GitHub shows (`_github-pages-challenge-frstrtr`) in Squarespace DNS, then click Verify.
2. Push this folder to a repo, then Settings → Pages → Source: `main` / `/ (root)`.
3. Settings → Pages → Custom domain: `technocore.one`.
4. Squarespace DNS (web records only — leave MX / SPF / DKIM / DMARC / Google verification untouched):
   - Remove the **Squarespace Domain Forwarding** preset (A `@` → 198.49.23.145).
   - Add A `@`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Add AAAA `@`: `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
   - Change CNAME `www`: `ghs.googlehosted.com` → `frstrtr.github.io`
5. Once the certificate is issued, enable **Enforce HTTPS**.
