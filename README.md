# CND - Shadowpixel

A Google Tag Manager custom tag template that sends a tracking pixel to a Cloud Nine Digital collection endpoint, enriched with dataLayer, device, browser, and live-session context.

## What it does

On firing, the tag:

1. Reads the current `dataLayer` and matches the entry associated with the active `gtm.uniqueEventId`.
2. Builds a payload containing the event name, domain, current URL, device type, browser, page section (DLM page-type variable), and a JSON-serialized copy of the matched dataLayer entry.
3. Detects "live session" mode via the `dlm_live_session` / `dlm_live_session_id` query parameters or an existing `dlm_live_session_id` cookie, and appends session identifiers to the payload when active.
4. Sends the payload as a pixel (`sendPixel`) to:
   `{endPoint}/{domain}/datalayers-img/` (or `/datalayers-img-live/` during a live session).

## Template fields

| Field | Description |
|---|---|
| **Endpoint URL** | The Cloud Nine Digital collection endpoint. Provided by your CND consultant or found in your DLM setup documentation. |
| **Page Type (DLM variable)** | The dynamic DLM page-type variable value for the current page (e.g. `homepage`, `checkout`, `article`). |
| **Domain / Client ID** | The predefined client abbreviation for this domain (e.g. `CND` for `www.cloudninedigital.nl`). Provided by your CND consultant or found in your DLM setup documentation. |
| **userAgent** | Reference to a Custom JavaScript variable that returns `navigator.userAgent`. |

## Setup

1. Import this template into your GTM workspace (via the Community Template Gallery, or manually from `template.tpl`).
2. Create a Custom JavaScript variable that returns `navigator.userAgent` and reference it in the **userAgent** field.
3. Create a tag using this template, fill in the Endpoint URL, Domain/Client ID (as provided by your CND consultant), and Page Type.
4. Attach a trigger (e.g. a custom event trigger matching your relevant events) and publish.

## Version

Current version: **1.0** — see the changelog header inside `template.tpl`'s Sandboxed JavaScript for details.

## Support

Found a bug or have a question? Open an issue in this repository.

## License

Apache License 2.0 — see [LICENSE](./LICENSE).
