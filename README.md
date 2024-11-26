# Hugo LittleLink
Partial theme implementation of Seth Cottle's [LittleLink](https://github.com/sethcottle/littlelink) and [LitteLink Extended](https://github.com/sethcottle/littlelink-extended) LinkTree alternative. 

## Features
The `littlelink.html` partial is the list wrapped so that it's got a header and centered and all pretty. You also need to include the `littlelink-css.html` partial in your `<head>` to get all of the style properly. (See `example.html`)

If you just want to use the list for example to keep the other styling of your website around the list, you can just use `littlelink-list.html`.


## Installation
## Init hugo site
```shell
hugo new site MyCoolSite
cd MyCoolSite
```

## Install the theme
```shell
git submodule add https://github.com/spslater/hugo-littlelink.git themes/littlelink
```

## Modify Config
### As support theme
Intended use of the theme is to be a small part of a larger site. Only designed for the one page the theme is used on.

Open `hugo.toml` and change `theme` to a list with `littlelink` as the first item
```toml
theme = ['littlelink', 'hyde']
```

### As sole landing page
Open `hugo.toml` and change `theme` to `littlelink`
```toml
theme = 'littlelink'
```

## Configuration
The theme can be configured in multiple places depending on how many LittleLink pages you want on your site.

### Styling
Styling includes the styleTheme (`auto`, `dark`, `light`) and header image.
styleTheme defaults to `auto` and the header image uses the LittleLink logo.

Lookup order for styling:
- Page `frontmatter`
- Site Parameters (`hugo.toml`)
- Defaults

Frontmatter:
```markdown
+++
title = "example"
[littlelink]
  themeStyle = "light"
  header = "images/headshot.png"
+++
```

Site Parameters:
```toml
[params.littlelink]
  themeStyle = "dark"
  header = "images/littlelink.png"
```

### List
The list is pulled from the site config or the data directory. If no values are set the example page will be displayed. The data directory file does not need to be in a yaml file, it can be json, toml, or whatever hugo is able to parse.

Lookup order for the list:
- Site Config (`hugo.toml`)
- Data directory (`data/littlelink.yml`)

Site config:
```toml
[[params.littlelink.links]]
  type = "github"
  title = "Theme's GitHub"
  alt = "Theme's Github Link"
  link = "https://github.com/spslater/hugo-littlelink"
[[params.littlelink.links]]
  type = "generic-cloud"
  title = "Seth Cottle's LittleLink"
  alt = "Seth Cottle's LittleLink"
  link = "https://littlelink.io/"
```

Data directory:
```yaml
- type: generic-blog
  title: Clobbered By hugo.toml
  alt: Even though these are defined here, hugo.toml overrides all links here
  link: https://example.com
- type: github
  title: GitHub
  alt: Theme's Github Link
  link: https://github.com/spslater/hugo-littlelink
```
