# pixel.rip

Documenting the journey of a little indie game studio.

**Live site**: [pixel.rip](https://pixel.rip)

## What's Here

- **Notes**: Studio updates and meta content
- **Codex**: Game dev learnings with interactive demos
- **Resources**: Curated tools and references

## Tech Stack

- Jekyll static site
- Sass styling  
- Cloudflare deployment
- Pico-8 integration

## Development

```bash
# First time
bundle install

# Run locally
bundle exec jekyll serve
```

## Content Structure

Posts live in `_posts/` with category-based organization:

- **resources**: `layout: resource`, requires `xurl:`
- **codex**: `layout: codex-entry` 
- **notes**: `layout: note`

All posts support `tags:` and `pinned: true/false`.

## Deployment

Auto-deploys to `master` via Cloudflare when changes are pushed to GitHub.