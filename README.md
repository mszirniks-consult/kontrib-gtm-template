# KONTRIB tag template for Google Tag Manager

Tag template for the [KONTRIB](https://kontrib.io) attribution platform. One tag type with a **Task** field:

| Task | What it does | Trigger |
|---|---|---|
| Base – load tag (all pages) | Loads `aa.js` from your KONTRIB tracking domain, passes consent (Google Consent Mode v2, variables, or none) and options | Initialization – All Pages |
| Conversion (purchase or lead) | Sends order number, value, currency and optional properties | Custom Event `purchase` / thank-you page |
| Event | Sends a named event with properties | any |
| Page view (single-page app) | Sends a page view | History Change |
| Set consent (without Consent Mode) | Passes the four consent types from your consent tool's variables | consent event of your CMP |
| Identify user (e-mail hash) | Links sessions of the same user; hashed in the browser, only with `ad_user_data` | login / form |

## Setup

1. Import this template (Templates → Tag Templates → New → ⋮ → Import) or add it from the Community Template Gallery.
2. Create a tag of type **KONTRIB**, task **Base**, enter your endpoint (`https://track.your-domain.com`, shown in KONTRIB under Administration → Tenant), trigger *Initialization – All Pages*.
3. Create a tag with task **Conversion** on your purchase event (`transaction_id`, `value`, `currency` from Data Layer Variables).
4. Verify in GTM preview: a request to `<endpoint>/c` with status 204. KONTRIB's tracking assistant confirms the first hit from the template.

Full guide: the onboarding document in your KONTRIB account, section "Installation via Google Tag Manager".

## Permissions

- `access_globals`: `aa` (read/write/execute), `aaq` (read/write), `__aa_loaded` (read) — the argument queue that `aa.js` takes over
- `inject_script`: `https://track.kontrib.io/aa.js` — the tag script is loaded from KONTRIB's platform domain; all data goes to the endpoint you enter (`https://track.<your-domain>`, must be `https://`)
- `access_consent`: the four consent types, read only
- `logging`: debug mode only

Data is sent only to the endpoint you enter. Loading the script from track.kontrib.io transmits no visitor data; no data goes to KONTRIB's own servers unless the endpoint is a KONTRIB-hosted tracking domain.

## Source

Built from `packages/gtm-template` in the KONTRIB repository; issues and questions: open an issue here or write to support@kontrib.io.

## License

Apache License 2.0, see [LICENSE](LICENSE).
