# Boundless Endeavors LLC Website

This is a simple static website for Boundless Endeavors LLC.

## Files

- `index.html` - the full website.

## DNS and Cloudflare Pages

Yes, you can keep DNS at Hover so your email records stay there. Point only the
website-related DNS records to Cloudflare Pages.

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
