# Ferrari Technologies website (ferrrari-dev)

A small static website for "Ferrari Technologies", built with the [Hugo](https://gohugo.io/) static site generator and the Casper blog theme. It is a fork of the "Victor Hugo" starter template, with the site title, description and branding changed. The site is currently a skeleton: the home page and navigation work, but there are no posts or pages yet.

## What it does

- Builds a single-column, blog-style site with a cover image, logo, author box and post list.
- Compiles CSS with PostCSS (cssnext) and JavaScript with Babel and webpack through Gulp.
- Includes an optional Netlify CMS admin page at `/admin` for editing posts in the browser (it needs a GitHub repository and Netlify login, see below).
- Produces plain static files in `dist/`, so it can be hosted anywhere.

## Tech stack

- Hugo (static site generator) with the `hugo-theme-casper` theme in `site/themes/`
- Gulp 3, webpack 1, Babel 6, PostCSS (Node build tooling from 2016)
- Netlify CMS 1.x (loaded from a CDN) and Netlify for deployment

## Run it

You need Node.js and npm, plus Hugo on your PATH. The tooling is old (Gulp 3 and webpack 1), so use an older Node release (Node 10 or earlier) and an older Hugo release (the theme was written for Hugo 0.1x and may not build on the newest Hugo). This was not rebuilt during the inspection, because package installs were not available.

```bash
npm install
npm start
```

Then open http://localhost:3000/. BrowserSync reloads the page when CSS, JavaScript or content changes.

## Build static files for hosting

```bash
npm run build
```

The finished site is written to `dist/`. Serve that folder with any static host, for example:

```bash
npx serve dist
```

No API keys or secrets are needed to build or host the site. The `netlify.toml` file already tells Netlify to run `npm run build` and publish `dist/`.

## Project layout

```
site/                 Everything Hugo builds
  config.toml         Site title, description, author and theme settings
  content/            Pages and posts (currently empty)
  static/             Files copied as is (images, admin page)
  themes/             The Casper theme
src/css, src/js       Assets that go through the Gulp and webpack pipeline
gulpfile.babel.js     Build tasks
webpack.conf.js       JavaScript bundling
```

To add a post, create a Markdown file under `site/content/post/`. Settings such as the title, cover image and author live in `site/config.toml`.

## Optional: edit content with Netlify CMS

1. Open `site/static/admin/config.yml` and replace `owner/repository` with `maxawad/ferrrari-dev`.
2. Deploy the repository to Netlify.
3. Set up GitHub as an authentication provider in the Netlify dashboard, following the [Netlify documentation](https://www.netlify.com/docs/authentication-providers).
4. Visit `/admin` on the deployed site and log in.

## Status

Prototype. The site structure and theme are in place, but the content is a placeholder ("Under Construction") and the last change was made in 2020.

## Credits

- Starter template: Victor Hugo / Casper CMS template, via [bdougie/casper-cms-template](https://github.com/bdougie/casper-cms-template) by Brian Douglas (bdougie), and contributors.
- Theme: [hugo-theme-casper](https://github.com/vjeantet/hugo-theme-casper) by Valère Jeantet, ported from the [Casper theme for Ghost](https://github.com/TryGhost/Casper).
- Site customization: Max Awad.

## License

The upstream starter and theme are MIT licensed (see `site/themes/hugo-theme-casper/LICENSE.md`). This repository does not yet have a top-level license file.
