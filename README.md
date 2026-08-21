# CWM SMS program landing (Twilio website field)

Static HTML for TCR/Twilio website crawl: `id=sms-opt-in`, START / STOP / HELP, phone **+1 619-914-6819**, privacy/terms on **legal.carwashmgmt.com**. **Zero** links to `www.carwashmgmt.com`.

Intended live URL after DNS + Pages bind:

- https://sms.carwashmgmt.com/

Same entity as today: **Car Wash Services LLC d/b/a Car Wash Management** (FEIN 33-4786509). Do **not** create a new LLC, EIN, or Twilio Brand for this page -- a new Brand is days/weeks, not tonight.

## Hosting (same pattern as legal)

Repo: `andrewbwm275/cwm-sms-program` -> GitHub Pages (branch `main` / root).

**CNAME file is intentionally not in the repo yet** (Pages auto-binds it and breaks github.io while `sms` NXDOMAIN). After GoDaddy Saves `sms`, AI adds root file `CNAME` with `sms.carwashmgmt.com` and binds Pages.

| Step | Who | Action |
|---|---|---|
| 1 | Andrew | GoDaddy DNS: Add **CNAME** host `sms` -> `andrewbwm275.github.io` (TTL 1/2 Hour). **Save** (+ SMS 2FA if prompted). Leave `legal` alone. Do **not** invent a new Brand. |
| 2 | Andrew or AI | After NS shows `sms` -> `andrewbwm275.github.io`: add repo `CNAME` = `sms.carwashmgmt.com`, push; GitHub Settings -> Pages -> Custom domain `sms.carwashmgmt.com` -> Save -> DNS check green -> **Enforce HTTPS**. |
| 3 | AI | Verify `https://sms.carwashmgmt.com/` 200, cert CN includes `sms.carwashmgmt.com`, View Source has START/STOP/HELP + `id="sms-opt-in"`, zero `www.carwashmgmt` strings. Then Twilio Website field can use this URL. **Do not POST Twilio from this packet unless Jarvis asks.** |

### Exact GoDaddy DNS (matches legal)

| Type | Name | Value | TTL |
|---|---|---|---|
| CNAME | `legal` | `andrewbwm275.github.io` | (existing -- do not change) |
| CNAME | `sms` | `andrewbwm275.github.io` | 1/2 Hour (**add**) |

Do not point `sms` at Base44. Do not put a github.io URL in the Twilio website field -- only `https://sms.carwashmgmt.com/` after HTTPS is real.

## Speed ranking (ASAP lead)

1. **Tonight / zero DNS:** Twilio Website = https://legal.carwashmgmt.com/ (already HTTPS OK, crawlable START/STOP/HELP). Same Brand.
2. **This packet (dedicated page):** `sms` CNAME + Pages bind above -> https://sms.carwashmgmt.com/ (same cert path that worked for `legal`).
3. **Option B -- Cloudflare orange-cloud on `www`:** If waiting on GitHub Pages TLS for `www` (`CN=*.github.io` / state `new`), put `www` behind Cloudflare proxy (orange cloud) so **Universal SSL** issues a real `www.carwashmgmt.com` cert. Requires Cloudflare zone on `carwashmgmt.com`, DNS record for `www` proxied, wait for Universal SSL active, then confirm HTTPS CN. Does **not** need a new LLC/Brand. May be faster than waiting on Pages `https_certificate.state=new`, but is more moving parts than using `legal` or `sms`.

## Brand / entity note

Reuse existing Twilio Brand + Campaign for Car Wash Services LLC. New Brand registration is **not** an ASAP path.
