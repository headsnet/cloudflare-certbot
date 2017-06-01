# Cloudflare Certbot Scripts

Pre &amp; post hooks to allow DNS authentication for LetsEncrypt

# Getting Started

Copy `.cloudflare.dist` to `.cloudflare` and edit the API key and email address to those of your own CloudFlare account

```
# Get your API key from https://www.cloudflare.com/a/account/my-account
CLOUDFLARE_USER=user@example.com
CLOUDFLARE_KEY=putyourapikeyhere
```

## Lighttpd

Creating a certificate

```
/usr/bin/certbot certonly --pre-hook "service lighttpd stop" --post-hook "make-lighttpd-pemfile && service lighttpd start" --preferred-challenges=dns --manual --manual-auth-hook ./authenticator.sh --manual-cleanup-hook ./cleanup.sh -d mydomain.com
```
