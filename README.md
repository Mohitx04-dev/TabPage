# Tab — Payment Request page

A single static file (`index.html`), no build step, no dependencies, no backend.

## Deploy to GitHub Pages

1. Push this folder's contents to a repo (a dedicated one, or a `gh-pages` branch of an existing one).
2. Repo → Settings → Pages → set the source to that branch/folder.
3. GitHub gives you a URL like `https://<username>.github.io/<repo>/`.
4. Update `PaymentLinkEncoder.baseURLString` in the Tab app to that URL.

## What it does

Reads everything from the `?d=` query parameter (produced by `PaymentLinkEncoder.swift`), verifies the hash suffix, and renders the request — title, itemized expenses, and one row per participant with a "Pay" button (a `upi://pay` deep link, opens whatever UPI app is already on the visitor's phone) and an "I've paid" button (opens WhatsApp with a pre-filled confirmation message, so a payer can report back through a channel the requester actually watches).

Nothing here is a payment processor. Money moves directly between the payer's and payee's own UPI accounts; this page never sees it, holds it, or confirms it — see the in-app doc comment on `PaymentLinkEncoder` for the trust model that implies.
