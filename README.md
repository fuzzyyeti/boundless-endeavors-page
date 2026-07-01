# Boundless Endeavors LLC Website

This is a simple static website for Boundless Endeavors LLC, built for GitHub
Pages.

## Files

- `index.html` - the full website.

## GitHub Pages Setup

Use GitHub Pages with the repository root as the publishing source:

```text
Source: Deploy from a branch
Branch: main
Folder: / (root)
```

On GitHub Free, GitHub Pages is available for public repositories. Private
repository Pages generally requires a paid GitHub plan.

## Custom Domain With Hover

Use the `www` subdomain as the public website address, for example:

```text
www.yourdomain.com
```

In the GitHub repository, go to:

```text
Settings -> Pages -> Custom domain
```

Enter the exact `www` hostname. GitHub will create or expect a `CNAME` file
containing that hostname.

In Hover DNS, add:

```text
Type: CNAME
Host: www
Value: your-github-username.github.io
```

Leave Hover's email records unchanged, including `MX`, SPF/DKIM/DMARC `TXT`,
and any other email-related records.

## Root Domain

If you want the bare/root domain, such as `yourdomain.com`, to work too, use
Hover's domain forwarding to redirect it to `www.yourdomain.com`.

This keeps DNS and email at Hover and avoids moving nameservers.
