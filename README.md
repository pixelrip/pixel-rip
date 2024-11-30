# pixel.rip

A little website for a little studio. 

- Jekyll
- Sass
- Cloudflare


### Local Development

first time: `bundle install`

to run: `bundle exec jekyll serve`


### Deploying

Currently setup to automatically deploy to `master` when changes are made on github via Cloudflare.


### Categories and Front Matter
Each category lives in a subfolder of `_posts`. Configuration for `category` and `layout` for each folder is in `_config.yml`

- `resource`: links to useful tools, videos, etc
    - `title: `
    - `category: resources`
    - `layout: resource`
    - `xurl: `
    - `tags: [tag1, tag2]`
    - `pinned: true | false`


- `codex`: debateably useful knowlege i've picked up along the way. proofs of concept, demos, etc. 
    - `title:`
    - `category: codex`
    - `layout: codex-entry`
    - `tags: [tag1, tag2]`
    - `pinned: true | false`


- `notes`: meta content, updates, news, etc
    - `title`
    - `category: notes`
    - `layout: note`
    - `tags: [tag1, tag2]`
    - `pinned: true | false`

### Todo

#### Phase 1
- [x] tag pages
- [x] tag links in hello world
- [x] /all posts page
- [x] code highlighting (~~pico 8 colors?~~)
- [x] codex: atan2
- [x] codex: sin and cos
- [x] fix post list ul
- [x] responsive sidebar
- [x] black color around avatar.png
- [x] footer
    - [x] rss
    - [x] github
    - [x] email
- [x] /codex page
- [x] /resources page
- [x] /notes page

#### Phase 2
- [ ] revise and test navigation
- [ ] automate posting to social
- [ ] /contact page (form)
- [ ] /newsletter page (form)