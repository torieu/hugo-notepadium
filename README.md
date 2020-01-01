![](https://raw.githubusercontent.com/cntrump/hugo-notepadium/master/images/screenshot.png)

# hugo-notepadium ![](https://img.shields.io/badge/license-MIT-blue.svg) [![Netlify Status](https://api.netlify.com/api/v1/badges/2f389751-e070-437b-9dbd-3773bd57322e/deploy-status)](https://lvv.me)

Request Hugo Version: [0.60.0+](https://github.com/gohugoio/hugo/releases/)

a fast and focus on reading [Hugo](https://gohugo.io) theme, **100% JavaScript-free**.

Features

- Logo and slogan
- Navigation items
- Syntanx highlighting
- Math supporting
- Comments powered by Disqus
- CC License
- Pagination with large number of pages supporting
- Light & Dark Mode
- Google analytics supporting
- Custom CSS supporting
- Custom JS supporting

Preview the exampleSite:

```shell
git clone https://github.com/cntrump/hugo-notepadium.git hugo-notepadium
cd hugo-notepadium/exampleSite
hugo server --themesDir ../..
```

## Quick Start

```shell
git submodule add https://github.com/cntrump/hugo-notepadium.git themes/hugo-notepadium
```

Example `config.toml`:

```toml
baseURL = "https://example.com"
title = "Notepadium"
theme = "hugo-notepadium"
copyright = "©2019 Notepadium."

languageCode = "zh-cn"
hasCJKLanguage = true

enableRobotsTXT = true

# Enable Disqus
#disqusShortname = "XXX"

# Google Analytics
#googleAnalytics = "UA-123-45"

[markup.highlight]
codeFences = true
noClasses = false

[markup.goldmark.renderer]
unsafe = true  # enable raw HTML in Markdown

[params]
style = "auto"  # default: auto. light: light theme, dark: dark theme, auto: based on system.
logo = ""  # if you have a logo png
slogan = "100% JavaScript-free"
license = ""  # CC License

[params.comments]
enable = false  # En/Disable comments globally, default: false. You can always enable comments on per page.

[params.math]
enable = false  # optional: true, false. Enable globally, default: false. You can always enable math on per page.
use = "katex"  # option: "katex", "mathjax". default: "katex"

[params.syntax]
use = "none"  # builtin: "prismjs", "hljs". "none" means Chroma
theme = "dracula"
darkTheme = "xcode-dark"  # apply this theme in dark mode

[params.nav]
showCategories = true       # /categories/
showTags = true             # /tags/

# custom navigation items

[[params.nav.custom]]
title = "About"
url = "/about"

[[params.nav.custom]]
title = "Hugo"
url = "https://gohugo.io/"
```

### Logo and Slogan

```toml
[params]
logo = "/img/logo.png"
slogan = "code my life ~"
```

### Light and Dark Mode

```toml
[params]
style = "auto"  # default: "auto", based on system. "light": light theme, "dark": dark theme.
logo = "/img/logo.png"
slogan = "code my life ~"
```

### Navigation items

```toml
[params.nav]
showCategories = true       # /categories/
showTags = true             # /tags/

# custom items

[[params.nav.custom]]
title = "iOS"
url = "/tags/ios"

[[params.nav.custom]]
title = "Hugo"
url = "https://gohugo.io/"

```

### Syntax highlighting:

```toml
# enable JS highlight
[params.syntax]
use = "hljs"  # 1. prismjs 2. hljs 3. none
theme = "dracula"
darkTheme = "xcode-dark"  # apply this theme in dark mode
```

### Math

```toml
[params.math]
enable = true  # true means globally, or on a per page set "math = true"
use = "katex"  # "mathjax" or "katex"
```

Enable comments on per page:

```md
+++
title = "..."
date = 2019-12-08
...
math = true
+++

...
```

Example

```
When $a \ne 0$, there are two solutions to \(ax^2 + bx + c = 0\) and they are
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$
```

### Comments

Setup Disqus [shortname](https://help.disqus.com/en/articles/1717111-what-s-a-shortname) in config.toml:

```toml
# disqus
disqusShortname = "XXX"  # your short name

[params.comments]
enable = false  # En/Disable comments globally, default: false. You can always enable comments on per page.
```

You can enable comments on per page:

```md
+++
title = "..."
date = 2019-12-08
...
comments = true
+++

...
```

### Pagination

Support large number of pages

![](https://raw.githubusercontent.com/cntrump/hugo-notepadium/master/images/03.png)

### Custom footer copyright layout

Thanks [@Benjamin-Lee](https://github.com/Benjamin-Lee)'s good idea!

Create an user-side partial:

```
.
└── layouts
    └── partials
        └── copyright.html
```

You can relayout copyright like this:

```html
{{- $copyright := . -}}
<div style="display: flex;flex-direction: row; justify-content: space-between;">
<p>{{- $copyright -}}</p>
<p><span>Powered by </span><a href="https://gohugo.io">Hugo</a><span> and the </span><a href="https://themes.gohugo.io/hugo-notepadium/">Notepadium</a></p>
</div>
```

### Custom CSS supporting

```
[params.assets]
css = ["css/font.css", "css/color.css"]
```

On user-side:

```
.
└── assets
    └── css
        ├── color.css
        └── font.css
```

`color.css` and `font.css` will be bundled into `core.css`.

### Custom JS supporting

```
[params.assets]
js = ["js/font.js", "js/color.js"]
```

On user-side:

```
.
└── assets
    └── js
        ├── color.js
        └── font.js
```

`color.js` and `font.js` will be bundled into `core.js`.

## Thanks

- [**Hugo**](https://gohugo.io/)
- [**HighlightJS**](https://highlightjs.org/)
- [**PrismJS**](https://prismjs.com/)
- [**MathJax**](https://www.mathjax.org/)
- [**Katex**](https://katex.org/)
- [**Disqus**](https://disqus.com/)

## Note

For Hugo 0.62.0+ users

 `![](01.png)` render as inline `<img>`, like as Github's style

 ![](https://raw.githubusercontent.com/cntrump/hugo-notepadium/master/images/01.png)

`![](01.png " ")` render as block `<img>`, like as `<figure>` tag style.

![](https://raw.githubusercontent.com/cntrump/hugo-notepadium/master/images/02.png)
