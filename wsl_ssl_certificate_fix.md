<https://github.com/bayaro/windows-certs-2-wsl>

Copy `/etc/ssl/certs.orig/java/` to `/etc/ssl/certs/` before running
`update-ca-certificates`.

# Git bash clone SSL certificate fix

```bash
git config --global http.sslBackend schannel
```
