# Chatwoot — ProjectSites Fork

> Fork of [chatwoot/chatwoot](https://github.com/chatwoot/chatwoot) (MIT).
> Custom extensions for the ProjectSites.dev support platform.
> Rebase target: `chatwoot/chatwoot:develop` — monthly cadence.

## What's different from upstream

- **Custom Docker image** — `Dockerfile.projectsites` extends official image with pre-seeded labels, macros, inbox config, and ProjectSites branding
- **Widget theming override** — reads `PROJECTSITES_BRAND_COLOR` and `PROJECTSITES_WIDGET_POSITION` env vars at boot
- **Pre-configured inbox** — seeds a "ProjectSites Support" web widget inbox on first boot if none exists

## Deploy

```bash
# Build and push
docker build -f Dockerfile.projectsites -t ghcr.io/professormanhattan/chatwoot-projectsites:latest .
docker push ghcr.io/professormanhattan/chatwoot-projectsites:latest

# Deploy to Fly
flyctl deploy --config infra/fly/support-chatwoot/fly.toml --app support-chatwoot
```

## Rebase from upstream

```bash
git fetch upstream develop
git rebase upstream/develop
# Resolve conflicts, test, rebuild image, deploy
```
