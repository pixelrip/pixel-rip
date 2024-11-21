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

- [x] tag pages
- [x] tag links in hello world
- [x] /all posts page
- [x] code highlighting (~~pico 8 colors?~~)
- [ ] codex: atan2
- [ ] codex: velocity
- [ ] codex: sin and cos
- [ ] /contact page (form)
- [ ] external links
    - [ ] github
    - [ ] newsletter
- [ ] /codex page
- [ ] /resources page
- [ ] /notes page
- [ ] responsive sidebar
- [ ] rss
- [ ] black color around avatar.png
- [ ] flatten
- [ ] revise and test navigation
