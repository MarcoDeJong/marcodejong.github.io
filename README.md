# marco-dejong.nl

Personal songwriter site, built with Jekyll and published through GitHub Pages.

## Requirements

- Ruby 3.3.4
- Bundler 2.5.11

These versions match the GitHub Pages runtime. Use a Ruby version manager such
as mise, rbenv, or asdf; do not use the system Ruby included with macOS.

## Setup

```sh
gem install bundler -v 2.5.11
bundle install
```

`Gemfile.lock` is intentionally ignored. GitHub Pages provides a fixed,
supported dependency set through the pinned `github-pages` gem.

## Local development

```sh
bundle exec jekyll serve --livereload
```

Open <http://localhost:4000>.

## Verification

```sh
bundle exec jekyll doctor
JEKYLL_ENV=production bundle exec jekyll build --strict_front_matter
```

The same production build runs automatically for pushes to `master` and for
pull requests.

## Updating the GitHub Pages runtime

Check the [GitHub Pages dependency versions](https://pages.github.com/versions/),
then update `.ruby-version` and the `github-pages` version in `Gemfile`
together. Run the verification commands before publishing.
