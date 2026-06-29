# email worker

A tiny Cloudflare Worker that connects **your own domain** to [mail.estrogen.delivery](https://mail.estrogen.delivery), fully on your own Cloudflare account. No SMTP, no server.

It receives mail for your domain (via Email Routing) and sends mail as your domain (via Email Sending), bridging both to the mailbox app over an HMAC-authenticated channel.

## Deploy

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/tiagozip/email-worker-template)

1. Click the button. It clones this Worker into your account.
2. When asked for **`RELAY_CONFIG`**, paste the single value from the mail app (Settings → Domains). That's the only thing to set.
3. In the Cloudflare dashboard for your domain, set the **Email Routing** catch-all to **Send to a Worker → this worker**, and enable **Email Sending** for the domain.
4. Back in the app, paste the Worker URL and verify.

`RELAY_CONFIG` is a base64 bundle of the shared secret, your domain, and the mail endpoint. Nothing else to configure.
