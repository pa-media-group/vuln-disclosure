# vuln-disclosure

Canonical, centrally-hosted `security.txt` (RFC 9116) for The PA and its properties.

Every domain and subdomain we operate redirects `/.well-known/security.txt` to the file hosted in this repository. This keeps contact and disclosure information current in one place rather than duplicated across many sites.

## Files

```
.well-known/
  security.txt      # the live file, served via raw.githubusercontent.com or GitHub Pages
```

## How to report a vulnerability

See the `Contact` and `Policy` fields in [`.well-known/security.txt`](.well-known/security.txt) for current reporting channels and our disclosure policy.

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
