# Cloudflare Certbot Scripts

Pre &amp; post hooks to allow DNS authentication for LetsEncrypt

## Lighttpd

Creating a certificate

```
/usr/bin/certbot certonly --pre-hook "service lighttpd stop" --post-hook "make-lighttpd-pemfile && service lighttpd start" --preferred-challenges=dns --manual --manual-auth-hook ./authenticator.sh --manual-cleanup-hook ./cleanup.sh -d mydomain.com
```
