# Houssam Moallem — Portfolio Website

Source code for [houssammoallem.com](https://houssammoallem.com)

> Internal operations docs (architecture, DNS, server, deploy) are kept **private**
> and are not tracked in this public repository.

## Quick Deploy

```bash
cd ~/houssammoallem-com && git pull && sudo rsync -a --delete \
  --exclude='.git' --exclude='docs' --exclude='nginx' \
  --exclude='README.md' --exclude='.gitignore' \
  --exclude='*.docx' --exclude='*.bak' \
  ./ /var/www/houssammoallem/
```

> Deploy copies **only** site assets. `docs/`, `nginx/`, and other repo-only files
> are excluded so they are never published to the web root. `--delete` also removes
> stale files from the web root that are no longer in the repo.
