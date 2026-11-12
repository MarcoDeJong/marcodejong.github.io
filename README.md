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

## Deployment

GitHub Pages is configured to publish from the `master` branch and the
repository root using **Deploy from a branch**. GitHub's managed
`pages build and deployment` workflow builds the Jekyll site, uploads the Pages
artifact, and deploys it to the `github-pages` environment.

Keep the custom domain configured as `marco-dejong.nl` in the repository's
Pages settings. The `CNAME` file mirrors that setting, but does not configure
the custom domain by itself.

The workflows in this repository validate the source and the resulting live
site; they do not perform a second deployment. If the publishing source is ever
changed to **GitHub Actions**, replace this setup with GitHub's official Jekyll
deployment workflow instead of running both deployment methods.

## Verification

```sh
bundle exec jekyll doctor
JEKYLL_ENV=production bundle exec jekyll build --strict_front_matter
bundle exec htmlproofer ./_site --disable-external
```

The same checks run automatically for pushes to `master` and for pull
requests. After GitHub Pages reports a successful deployment, a second workflow
checks the live homepage, public assets, HTTPS redirect, and 404 response. The
deployment check can also be started manually from the Actions tab.

## Updating the GitHub Pages runtime

Check the [GitHub Pages dependency versions](https://pages.github.com/versions/),
then update `.ruby-version` and the `github-pages` version in `Gemfile`
together. Run the verification commands before publishing.
