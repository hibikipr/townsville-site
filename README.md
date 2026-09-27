# townsville.cc — Homepage

Homepage for [townsville.cc](https://townsville.cc), the apex domain for all
the townsville.cc apps (custom domain on the `townsville.cc` Cloudflare
zone, HTTPS enforced). Also served at `www.townsville.cc`.

- `index.html` — single-page site: hero, then three "sectors" (3D Printing,
  Homelab, Everyday) linking out to each app's own site or repo.
- `assets/` — icons and illustrations, exported to WebP to keep the page light.
- `CNAME` — pins the custom domain to the bare apex; don't delete unless you
  mean to detach it (see below).

Plain static HTML/CSS, no build step. Deploys automatically on push to `main`
via GitHub Pages.

## Updating

Edit `index.html` directly and push to `main` — Pages rebuilds in under a
minute. Adding a new app means a new card in the relevant sector, following
the existing pattern: a `--saber` / `--tint` / `--label` color triplet set
via inline `style` on the card, an icon (WebP, ~144px) if there is one, and a
link out to the app's own site or GitHub repo.

## If the HTTPS certificate ever gets stuck

GitHub Pages certificate provisioning can occasionally stall on the generic
`*.github.io` wildcard cert instead of issuing one for the custom domain, and
Cloudflare proxying (orange-cloud) on the DNS record blocks issuance outright
— GitHub's Let's Encrypt validation needs to reach it directly. Fix: make
sure the `townsville.cc` and `www` DNS records are **DNS only** (grey cloud),
then remove the `CNAME` file, let Pages rebuild, and add it back — this
re-triggers certificate issuance. You can switch Cloudflare proxying back on
afterward once the cert shows `approved`.

## Related repos

- [filatint-site](https://github.com/hibikipr/filatint-site)
- [homesiem-site](https://github.com/hibikipr/homesiem-site)
- [listnudge-site](https://github.com/hibikipr/listnudge-site)
- [nozzlecast-site](https://github.com/hibikipr/nozzlecast-site)
- [kaireads-site](https://github.com/hibikipr/kaireads-site)
