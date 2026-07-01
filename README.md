# Boundless Endeavors LLC Website

This is a simple static website for Boundless Endeavors LLC.

## Files

- `public/index.html` - the full website.
- `wrangler.jsonc` - Cloudflare Workers Static Assets configuration.

## DNS and Hosting Options

Yes, you can keep DNS at Hover so your email records stay there. The cleanest
way to do that is still Cloudflare Pages with a `www` subdomain CNAME.

Cloudflare Workers Static Assets is also configured for this repo, but Workers
custom domains require the domain to be an active Cloudflare zone. That means
you would need to move authoritative DNS from Hover to Cloudflare if you want
`www.yourdomain.com` to point directly at a Worker without exposing the
`*.workers.dev` URL.

## Cloudflare Pages With Hover DNS

The simplest setup is to publish the site at `www.yourdomain.com`. In
Cloudflare Pages, add `www.yourdomain.com` as a custom domain first. Cloudflare
will show the target, normally your Pages subdomain, such as
`your-project.pages.dev`.

Then create this record in Hover:

```text
Host: www
Type: CNAME
Value: your-project.pages.dev
```

Keep Hover's existing MX/TXT records for email unchanged.

## Cloudflare Workers Static Assets

This repo can also deploy as a Worker using Workers Static Assets:

```text
npm install
npm run deploy
```

The static website lives in `public/index.html`, and `wrangler.jsonc` points
Workers at that directory.

If you deploy only to the default Workers URL, it will look like this:

```text
https://boundless-endeavors.<your-workers-subdomain>.workers.dev
```

That URL may include a personal or account-specific Workers subdomain. A custom
domain hides it, but Workers custom domains require Cloudflare DNS for the zone.

## Root Domain

If you want the bare/root domain, such as `yourdomain.com`, to work directly on
Cloudflare Pages, Cloudflare currently expects the domain to be added as a
Cloudflare zone and to use Cloudflare nameservers.

That would move authoritative DNS from Hover to Cloudflare. You can still keep
email hosted by Hover by copying the Hover email MX/TXT records into Cloudflare
DNS, but if your priority is keeping all DNS records at Hover, use
`www.yourdomain.com` as the real website host.

For the root domain while keeping DNS at Hover, use Hover's domain forwarding
feature, if available, to redirect `yourdomain.com` to `www.yourdomain.com`.

## Deployment Settings

For Cloudflare Pages, use:

```text
Framework preset: None
Build command: leave blank
Build output directory: /
```
