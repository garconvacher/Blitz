# Blitz

An eBook framework (CSS + template) which mantra is to “find simple solutions to complex issues.”

## Compile

### For core

`lessc blitz.less blitz.css`

### For Kindle

Either uncomment `@import 'kindle';` in `blitz.less` or, if you want to compile a specific kindle stylesheet:

`lessc kindle.less kindle.css`

### For Media Queries

You shouldn’t output them in `blitz.css` as legacy RMSDK (ePub 2) will ignore the entire stylesheet if there are media queries in it—excepted `amzn` queries.

`lessc blitz-mq.less blitz-mq.css`

## Design & Goals

Blitz was designed to deal with the significant obstacles a newcomer or even an experienced producer might encounter. Its major goals are:

1. to be simple and robust enough;
2. to offer a sensible default;
3. to manage backwards compatibility (ePub 2.0.1 + mobi 7);
4. to provide useful tools (LESS/SASS);
5. to get around reading modes (night, sepia, etc.);
6. to **not** disable user settings.

We have chosen a functional approach (FCSS) but LESS/SASS “plugins” are planned to provide meaningful class names depending on eBook’s type (poetry, plays, etc.).

## Principles

Blitz is leveraging the concept of inheritance. Values `inherit` and `currentColor` are being used extensively to make the framework compatible with Reading Systems’ default stylesheets, reading modes (`color`) and user settings (`font-size`, `font-family`, `line-height`, etc.).

Defaults and a reset do the heavy lifting so it’s just about building on top of this base. Please note Blitz is taking care of defaults RS aren’t necessarily (HTML5 block elements, hyphens and pagebreaks for selected elements, etc.).

Finally, although we try to rely on RS’ typefaces, typography has been fine tuned.

- The default scale has been chosen to handle various situations well enough (screen/container size, user increasing `font-size`, typeface used, etc.)
- Vertical rhythm (`line-height` + `margin` and `padding`) is automatically computed in LESS/SASS to enforce consistency. By taking care of vertical rhythm, we’re also achieving horizontal harmony when the eBook is rendered on a (fake) spread: “everything text” lines up on the same baseline grid, which makes for a more comfortable reading experience.
- `sup` and `sub` styling is improved to prevent them from affecting line-height.
- The whole [§8. Breaking Within Words](https://drafts.csswg.org/css-text-4/) is implemented in LESS/SASS.

To sum up, we’ve tried to find a balance and feel like Blitz defaults can help producers get around a lot of possible issues: we don’t need hacks, we don’t have to change values in specific situations using complex media queries.

## Related EPUB 3.1 issues

- The EPUB 3.1 spec should address common reader styling scenarios [#671](https://github.com/IDPF/epub-revision/issues/671)
- Defining a minimal default stylesheet in the epub spec [#672](https://github.com/IDPF/epub-revision/issues/672)
- Media Queries [#685](https://github.com/IDPF/epub-revision/issues/685)
- Possible spec language for reading system CSS handling [#693](https://github.com/IDPF/epub-revision/issues/693)

## Roadmap

- Pre-release (v.0.95) + debug
- Convert LESS to SASS
- Create Web Page
- Launch v.1 (codename “Rock the Casbah”)
- LESS/SASS Plugins
- Launch v.2 following EPUB 3.1 rec (we’ll drop support for legacy RMSDK and Mobi 7 at this point, v.1 will be kept available if support for these two is needed)

### TODO ASAP

- epub test suite for RS **[urgent]**
- LESS -> SASS (anyone willing to take on it?)

## Support

- Readium
- iBooks
- Kobo
- Kindle (mobi7 + KF8)
- Google Play Books
- RMSDK (a.k.a. eBooks’ IE 6)

### Licence 

Pre-release under MIT Licence (https://opensource.org/licenses/MIT) © 2016, Jiminy Panoz. May or may not change for v.1 stable—alternative options are currently being reviewed.
