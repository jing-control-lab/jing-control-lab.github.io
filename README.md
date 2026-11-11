# JCL

**Jing Control Lab** · [Website](https://jing-control-lab.github.io/)

A lightweight Jekyll group website, published with GitHub Pages.

Navigation: Home · Course · Blog · News · Contact.

Research, People, and Publications remain available at their existing URLs and are temporarily hidden from the navigation. Course links to the external learning resource.

## Editing

See [instruction.md](instruction.md) for the Chinese maintenance guide. Content lives in `index.html`, `_pages/`, `_data/`, and `_blogs/`. No JavaScript framework, database, or login service is required.

The blog example is excluded from the build and marked `published: false`. Confirmed people and group publications can be added later; no personal publication record is imported. Public contact details live in `_data/contact.yml`.

## GitHub Pages

In **Settings → Pages**, choose **Deploy from a branch**, **main**, and **/ (root)**. GitHub Pages builds this Jekyll source after changes are committed. Do not add `.nojekyll`.

For a local Jekyll preview with Ruby and Bundler installed:

```sh
bundle install
bundle exec jekyll serve
```

## Source and license

Layout and selected CSS patterns are adapted from [zjin73/zjin73.github.io](https://github.com/zjin73/zjin73.github.io), inspected at commit `77f8842477821d6c142345cd4955a579c7133c2d`. Only the necessary layout and styles were adapted. See [NOTICE.md](NOTICE.md) and [LICENSE](LICENSE) for attribution and the retained MIT notice.
