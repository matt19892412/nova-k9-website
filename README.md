# NOVA K9 Training — Website

The official website for NOVA K9 Training. A single-page static site (plain HTML/CSS/JS, no build step) hosted on **GitHub Pages**, with the domain **nova-k9-training.co.uk** registered at IONOS.

---

## What's in here

| File | Purpose |
|------|---------|
| `index.html` | The entire website (self-contained — styles, scripts and logo are all inside this one file) |
| `404.html` | Branded "page not found" page |
| `CNAME` | Tells GitHub Pages the custom domain (`nova-k9-training.co.uk`) |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is (don't run Jekyll) |
| `robots.txt` / `sitemap.xml` | Basic SEO so search engines can find the site |

To edit the site, change `index.html` and push — GitHub Pages redeploys automatically.

---

## Part 1 — Put it on GitHub Pages

1. **Create a new repository** on GitHub (e.g. `nova-k9-website`). It can be public or private (Pages works on both with a free account for public; private needs Pages enabled).
2. **Add these files** to the repository (drag them into the GitHub web uploader, or push with git):
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Set **Branch** to `main` and **folder** to `/ (root)`, then **Save**.
6. Wait 1–2 minutes. GitHub shows a green tick and a live URL like `https://<your-username>.github.io/<your-repo>/`. Check it works.

---

## Part 2 — Point the domain (at IONOS)

> **Important:** the domain is currently connected to IONOS **MyWebsite**. Pointing the DNS moves it off the builder. **Do not cancel MyWebsite until the new site is confirmed live.** Everything below is reversible.

### A. In GitHub
1. Repo **Settings → Pages → Custom domain**: enter `nova-k9-training.co.uk` and **Save**.
   (This matches the `CNAME` file already in the repo.)
2. Leave **Enforce HTTPS** unticked for now — tick it once the certificate is issued (can take up to ~24h).

### B. In IONOS (Domains → nova-k9-training.co.uk → DNS)
You need to point both the apex domain and `www` at GitHub.

**Apex domain** (`nova-k9-training.co.uk`) — create four **A records** pointing to GitHub's IPs:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

**Optional (IPv6 support)** — you can also add four **AAAA records** on `@`:

| Type | Name | Value |
|------|------|-------|
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |

**www subdomain** — create one **CNAME record**:

| Type | Name | Value |
|------|------|-------|
| CNAME | www | `<your-username>.github.io` |

(Replace `<your-username>` with your actual GitHub username. Note the trailing setup — enter it exactly as GitHub shows it.)

3. Remove/replace any old A or CNAME records that point at MyWebsite, or they'll conflict.
4. Save. DNS changes take anywhere from a few minutes to a few hours to take effect.

### C. Confirm
- Visit `https://nova-k9-training.co.uk` — you should see the new site.
- Once it's stable, go back to GitHub Pages and tick **Enforce HTTPS**.
- Only now, once you're happy, cancel/retire the IONOS MyWebsite site.

---

## Updating the site later
Edit `index.html`, commit, and push. The live site updates within a minute or two.

---

*Building Confident Dogs Through Clear Communication*
