# silverbullet-config

Public, generic SilverBullet config. Shared by work and home.

- `Library/Local/` — pages copied into `<space>/Library/Local` at each stack start.
  Local edits in that folder are overwritten. Put private pages elsewhere in the space.
- `deploy/` — compose files for Portainer (git stack) and local Docker.

## Deploy

Home (Portainer): new stack, build method Repository, compose path
`deploy/docker-compose.yml`. Set the variables from `deploy/.env.example`.

Work: add `-f deploy/docker-compose.work.yml` and set `CA_BUNDLE`.

## Pages

| Page | Purpose |
|---|---|
| `Theme` | Light and dark theme: colors, type, code, quiet top bar |
| `Tree` | Left sidebar tree. Built in. No plug. |
| `Banner` | Page banner from `banner:` frontmatter |
| `Keys`, `Dashboard` | Shortcut and dashboard |

Never commit secrets or internal names here.
