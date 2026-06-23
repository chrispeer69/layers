# LAYERS — Book Marketing Site

The official one-page marketing site for **LAYERS: How to Recognize and Face the
Unresolved Layers in Your Marriage** by Christopher & Lisa Peer.

It covers the book, the five layers, chapter list, real-couple stories, 1:1
coaching, a blog, speaking inquiries, author bio, and a Stripe-powered donation
form.

## Tech

- A single static `index.html` (all CSS/JS inline — no build step).
- A tiny zero-dependency Node static server (`server.js`) for production hosting.

## Run locally

```bash
npm start
# then open http://localhost:3000
```

(Any static server works too — e.g. `npx serve`.)

## Deploy (Railway)

This repo is configured for [Railway](https://railway.app) via `railway.json`:

- Builder: Nixpacks (auto-detects Node + runs `npm start`).
- Health check: `/healthz`.

Push to the connected GitHub repo and Railway deploys automatically, or run
`railway up` from the project directory.

## Configuration

### Stripe (donations)

The donation form uses Stripe Elements. Replace the placeholder publishable key
in `index.html`:

```js
const STRIPE_KEY = 'pk_test_YOUR_PUBLISHABLE_KEY';
```

Donations also need a backend endpoint that creates and confirms a Stripe
`PaymentIntent` (see the `processDonation` comment in `index.html`). Until that
is wired up, the form shows a friendly "add your key" notice and does not charge.

### Forms

The registration, coaching, and speaking forms currently show a success state on
submit without sending data anywhere. Connect them to your email service or
backend as needed.

### Contact email

Speaking inquiries point to `book@layersbook.com`.
