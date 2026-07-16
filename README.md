# Houssam Moallem — Portfolio Website

Source code for [houssammoallem.com](https://houssammoallem.com)

## Documentation

| Document | Purpose |
|----------|---------|
| [docs/README.md](docs/README.md) | Project overview, features, page structure |
| [docs/TECHNICAL.md](docs/TECHNICAL.md) | Architecture, DNS, nginx, SSL, security, commands |
| [docs/SETUP.md](docs/SETUP.md) | Editing workflow, deployment, Git, troubleshooting |
| [docs/PRD.md](docs/PRD.md) | Product vision, pages, design decisions, roadmap |

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
