# Decalux

Two pages, one domain.

```
/                      the website  (index.html)
/app/                  the app      (installable PWA)
/app/manifest.webmanifest
/app/sw.js             offline + install (network-first)
/app/icons/            home-screen icons
CNAME                  www.decalux.art
.nojekyll              serve files as-is
```

The website's elephant logo opens a QR pointing to https://www.decalux.art/app .
On a phone that URL opens the app in the browser, which then offers
"Add to Home Screen" — an installed app with no App Store and no Play Store.

## Deploy on GitHub Pages
1. Create a repo and drop these files at its root (keep the folder structure).
2. Repo -> Settings -> Pages -> Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
3. Custom domain: the CNAME file already sets `www.decalux.art`. In your DNS,
   point a CNAME record for `www` at `<your-username>.github.io`.
   (If `www.decalux.art` already resolves to your current host, just move it here.)
4. Wait for the green check, then enable "Enforce HTTPS".

## IMPORTANT — the microphone needs HTTPS
The app asks for the mic on first tap. That prompt only appears over **https**
(GitHub Pages is https). It will NOT prompt if you open the file by
double-clicking it locally (file://). Always test on the live URL.

To change what the QR points to, edit `APP_DOWNLOAD_URL` near the top of the
script in `index.html`.
