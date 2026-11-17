# Webex Connect Chat Test

A dependency-free static test page for the supplied Webex Connect chat widget.

## Files

- `index.html`: test page and the supplied widget identifiers.
- `widget.js`: supplied Cisco widget loader and browser fallback.
- `styles.css`: page styling, independent of the chat widget.

The copied `{3}` placeholder was removed so JavaScript can parse. Loader event
handlers are registered before insertion, and fallback close messages are checked
against the fallback iframe. The widget identifiers and Cisco endpoint are unchanged.

## GitHub Pages

In the repository's **Settings > Pages**, choose **Deploy from a branch**,
then select **main** and **/ (root)**.

Expected URL: https://scampaBS.github.io/webex-connect-chat-test/

This repository is public because the account's current plan rejected Pages
activation for a private repository. Pages is enabled on `main` at the root.

Pages from a private repository requires an eligible paid GitHub plan. A private
repository does not make the published Pages site private: visitors can still
inspect the widget identifiers and all served HTML, CSS, and JavaScript.
Do not store secrets here. The `noindex` directive is not access control.

## Testing

1. Open the published HTTPS URL in a current browser.
2. Wait for the bottom-right chat launcher, then open it.
3. Send a non-sensitive test message and verify delivery in the configured
   Webex Connect flow or agent interface.

If domain restrictions are configured for the widget, allow `scampaBS.github.io`
in Webex Connect. Check widget enablement, availability rules, browser content
blockers, and the browser console/network panel if the launcher does not appear.
The loader's success console message only confirms the script downloaded, not
that a conversation was delivered.

The vendor-provided fallback says the browser is unsupported whenever the loader
fails; network blocking can cause the same message.

## Initial live verification

On November 17, 2026, the Pages deployment succeeded and the live page loaded
the Cisco initializer, general script, and widget iframe. However, the Cisco
widget settings endpoint returned HTTP 404 for the supplied widget ID and
`host=scampabs.github.io`:

```text
https://widget-api.produs1.ciscoccservice.com/livechats/8482B03F-3962-4381-B6B5-B6D76837E3D0/settings?host=scampabs.github.io&$callback=?
```

The chat launcher remained hidden, so end-to-end messaging could not be tested.
Ask the Webex administrator to verify the widget ID, deployment region,
publication/enablement, and allowed website domain. The 404 alone does not
identify which configuration needs changing.

No build step, package installation, or API credentials are required.
