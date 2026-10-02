# vuln-disclosure

Canonical, centrally-hosted `security.txt` (RFC 9116) for The PA and its properties.

Every domain and subdomain we operate redirects `/.well-known/security.txt` to the copy served at `https://security.thepa.com/.well-known/security.txt` (GitHub Pages, built from this repository). This keeps contact and disclosure information current in one place rather than duplicated across many sites.

## Files

```
.well-known/
  security.txt      # the live file, served via GitHub Pages
pa-security-pubkey.asc  # security team PGP public key (referenced by the Encryption field)
.nojekyll           # required: stops Pages/Jekyll dropping the .well-known directory
```

## How to report a vulnerability

See the `Contact` field in [`.well-known/security.txt`](.well-known/security.txt) for the current reporting channel.

## Encrypting reports

Reports can be encrypted to the security team's PGP key: [`pa-security-pubkey.asc`](pa-security-pubkey.asc)

```
PA Media Security Team <security-team@thepa.com>
Fingerprint: CBC7 B8F1 D8F3 56A2 E4E3  EA42 413B 7BF0 12B2 8AFA
Expires:     2028-10-01
```

Verify the fingerprint after importing (`gpg --import pa-security-pubkey.asc && gpg --fingerprint security-team@thepa.com`) before trusting the key.

## Hosting

Served by GitHub Pages from the `main` branch (root folder) on the custom domain `security.thepa.com`, with HTTPS enforced. Do not remove `.nojekyll`. Changes go live when merged to `main`.

## Why this repo is public

RFC 9116 requires `security.txt` to be retrievable over HTTPS at a well-known path. Hosting it here lets us:

- Redirect every domain/subdomain to a single, version-controlled source of truth
- Track changes to contact info and expiry via commit history
- Keep the file itself minimal — no infrastructure detail beyond what the RFC requires

## Maintenance

- **Expires** field must be kept current — do not let it lapse (see RFC 9116 §5.3)
- Update `Contact`/`Policy`/`Encryption` fields as processes change
- Consider PGP-signing the file and listing verified locations under `Canonical` if signature verification becomes a priority

## Not included here

This repo intentionally does not enumerate internal subdomains, infrastructure names, or anything beyond what's required for vulnerability disclosure.
