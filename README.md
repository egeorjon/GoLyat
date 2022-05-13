# GoYat

**Goyat** is a theme for the Hugo static site generator. This my second theme for this tool, built for my own blog.

Goyat is for huGO Yet Another Theme.

You can find a live demo of the original Fresh theme [here](https://www.emmanuelgeorjon.com) (will be completed when the theme will be deployed in production).
This theme is intended for personal website and blog. If you'd like to extend the theme to include other functionalities, please submit a pull request.

## Table of Contents

- [Goliath](#goliath)
  - [Features](#features)
  - [Tools and libraries](#tools-and-libraries)
  - [Installation](#Installation)
  - [Usage](#usage)
  - [Markups](#markups)
  - [Shortcodes](#shortcodes)
    - [Attachments](#attachments)
    - [imggallery ](#imggallery )
    - [Language](#language)
    - [Date format](#date-format)
    - [Pagination](#pagination)
    - [Site title / brand](#site-title--brand)
    - [Navigation](#Navigation)
    - [Search configuration](#search-configuration)
  - [SEO and other configurations](#seo-and-other-configurations)
    - [SEO configuration](#SEO configuration)
    - [RSS configuration](#rss-configuration)
    - [File site.manifest](#file-sitemanifest)
  - [Content configuration](#content-configuration)
    - [Meta information](#meta-information)
    - [Widgets](#widgets)
    - [Footer](#footer)
  - [Design configuration](#design-configuration)
  - [Configuration of the social media](#configuration-of-the-social-media)
    - [SEO features](#seo-features)
    - [Favicons](#favicons)
    - [RSS feeds](#rss-feeds)
    - [Sitemap](#sitemap)
  - [Advanced configuration](#advanced-configuration)
    - [Manifest file](#manifest-file)
    - [Styles](#styles)
 

## Features

* Responsive design,
* No sidebar,
* Customizable,
* Widget based,
* Search features,
* Contact form (by Netlify),
* Piwik Pro integration,
* Google WebMaster tool integration,
* SEO features

## Tools and libraries

This theme uses
* [BootStrap 5.1.3](https://getbootstrap.com/docs/5.0/getting-started/introduction/)
* [BootStrap Icons 1.8.1](https://icons.getbootstrap.com/)
* [Simple Lightbox 2.10.1](https://simplelightbox.com/)
* [FuseJS 6.5.3](https://fusejs.io/

## Installation

**GoLyat** is a Hugo theme. So, before installing the theme, you need to 

* Install [Hugo](https://gohugo.io), 
* and create a new site ([procedure](https://gohugo.io/getting-started/quick-start/#step-2-create-a-new-site)).

Then **Goliath** can be deployed as many other themes, with 3 possible ways:

1. Git clone
2. Git submodule
3. Download ZIP and manual install

### Option 1: Git clone

From the root directory of your site, 
```bash
git clone https://github.com/egeorjon/Goliath themes/Goliath
```
This method could generate some issues with some hosting platforms (like Netlify).

### Option 2: Git submodule (recommended)

From the root directory of your site,
```bash
git submodule add https://github.com/egeorjon/Goliath themes/Goliath
```
This is the method officially supported by Netlify.

### Option 3: Download ZIP and manual install

[Download the ZIP file](https://github.com/egeorjon/Goliath/archive/refs/heads/main.zip), and unpack it into the folder `themes/Goliath`.

### Once the theme is deployed 

Edit the file `config.toml`, and update the first line
```toml
theme = "goliath"
```

## Usage

If you have some content, just start Hugo built-in server to see your site!

```bash
hugo server -D
```

if not, you can get the content from `examplesite`
```bash
cd my-site
cp themes/Goliath/examplesite content
hugo server -D
```

Then, to see the result, use the following url [`localhost:1313`](http://localhost:1313) in your favorite browser, 

==> Style guide

## Markups

The theme provides two markups

* The first one improves the links design: when you write a link with markdown, like `[the link](the url's link)`, icons are added if the link is an external link, a link to GitHub, or a link to Wikipedia.
* The second one manages the images: a markdown sentence like the following `![image.png](url to the image)` will generate a fuilly responsive image in HTML

```HTML
<figure class="figure-img figure-center">
  <a href="url to the image" title="Framework Archimate">
    <img sizes="(max-width: 576px) 480px, 
                (max-width: 768px) 660px, 
                (max-width: 992px) 900px, 
                100vw" 
          srcset="url to the 480 image" 480w,
                "url to the 660 image" 660w,
                "url to the 800 image" 800w
          src="url to the image" 
          alt="Framework Archimate" 
          title="Framework Archimate" 
          width="800px" 
          height="593px">
        </a>
  <figcaption>Caption of the image</figcaption>
</figure>
```

## Shortcodes

The theme provides some shortcodes 

| Shortcodes   | Description    |
|--------------|----------------|
| attachments | Display the list of documents attached to the current post |
| imggallery   | Display a photo gallery |

### Attachments

Parameters: 

| Parameter | type   | Purpose | Mandatory | Default | Possible values |
|-----------|--------|-----------|---------|-----------------|
| files     | string | relative path to the attachments | Yes |  | |
| fields    | string | list of fields to display | No | icon,title,size | icon,title,filename,size |

By default, the shortcode knows only the files' name. If you want to display the title of the files, you have to fill the title in the Front-Matter of the page, like in the following example:
```toml
[[resources]]
  src = "attachments/matrice_eisenhower.xlsx"
  title = "Matrice d'Eisenhower sous Excel"
[[resources]]
  src = "attachments/archimate_poster.pdf"
  title = "The Archimate elements"
``` 
With the Front Matter above, the syntax of the shortcode could be
```
{{< attachements file="attachements/*" >}}
``` 
and the result will be
![List of attachments displayed by the shortcode](#)

==> 

### imggallery 

Parameters: 

| Parameter | type    | Purpose | Mandatory | Default | Possible values |
|-----------|---------|-----------|---------|-----------------|
| files     | string  | relative path to the images | Yes | | |
| size      | int     | size of the thumbnails      | No  | 250 | Any numeric value |
| caption   | boolean | Display the caption or not  | No | true | 1, true: display the caption, 0,false: don't display |
| overlay   | string  | Position of the caption     | No | bottom | top, bottom or center |


Similarly to the `attachments`shortcode, you can add a title (that will be the caption) to the thumbnails of the gallery. You can also specify if you want to display EXIF data.
The following example show the Front-Matter of a page, with 3 galleries, 2 photos in each, and the EXIF data enabled in the second one:
 ```toml
[[resources]]
title = "title 1"
src = "gallery1/photo1.jpg"

[[resources]]
title = "title 2"
src = "gallery1/photo2.jpg"

[[resources]]
title = "title 3"
src = "gallery2/photo4.jpg"

==>

[[resources]]
title = "title 4"
src = "gallery2/photo5.jpg"

==>

[[resources]]
title = "title 5"
src = "gallery3/photo7.jpg"

[[resources]]
title = "title 6"
src = "gallery3/photo8.jpg"

[[resources]]
title = "title 7"
src = "gallery3/photo9.jpg"
 ```

The following parameters
```
{{<imggallery files="gallery2" overlay="center" >}}
```
will give the following result:

![Example of a photo gallery](#)

==>

### The specific case of blockquote

We have no shortcode for `blockquotes`, but **Goliath** takes into account the styles you can provide below the blockquote: 

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
{.info | .warning | .error}

==> image

## Initial configuration

### Tests and production

By default, the theme runs in test mode.
For moving to the production mode, you have to set the environment variable `HUGO_ENV`
```bash
export HUGO_ENV=production
```

if you are not using bash (and/or if you are in a Microsoft Windows environment
```cmd
SET HUGO_ENV=production
```

In the Production environment,

==> 
* Google Analytics is enabled,
* RSS links are enabled,
* ROBOTS directive are set to INDEX, FOLLOW.

### Language

Available translations are in the `/i18n` directory of the theme. Today only frenh, and english are available.
You can configure the language modifying the following key, in the site configuration file (usually `config.toml`).

```toml
DefaultContentLanguage = "fr"
languageCode           = "fr-fr"
```

### Date format

By default, the date format is `dd-mmm-yyyy` everywhere (like 17-Apr-2022). You can configure this format, by using the following in the configuration file:
```toml
[params]
  formatdate = "<date layout>"
```

The `date layout` string can be either:

* Go’s Layout String: The full documentation for the date formats is [HERE](https://golang.org/pkg/time/#pkg-constants "Package time"), or [HERE](https://golang.org/src/time/format.go?h=date "Source file src/time/format.go")
* A custom Hugo layout identifier. See the [Hugo's documentation](https://gohugo.io/functions/dateformat/#datetime-formatting-layouts "Date/time formatting layouts") (requires the Hugo versions 0.87.0 and above)

Examples:
```toml
[params]
  formatdate = "Jan 2, 2006"
  formatdate = ":date_medium"
```
will display Apr 19, 2022.

### Pagination

You can define the number of posts listed in each page of the lists. In the configuration file `config.toml`

```toml
paginate = "<the number of posts>"
```

### Site title / brand

The navigation bar includes the main menu, and the title of the site/blog (the brand). You can fully customize the brand. In the configuration file of the site:

```toml
[params]
  brandlogo   = "<the path of the image related to the /static folder>"
  brandtitle  = "<the title of the site>"
```

Examples:

1. Example 1: Display both logo

```toml
[params]
   brandlogo = "img/logo.png"   # The file must be put in the folder /static/img.
```

2. Example 2: Display the blog's title 

```toml
[params]
   brandtitle = "John Doe"
```

3. Example 3: Nothing specify

```toml
theme="goliath"
title=< title of the blog >
[params]
#    ...
#    brandlogo is not specified, nor brandtitle
#    ...
```
In this case, the theme will display the title of the blog as a brand title.

### Navigation

You have two ways for configuring the navigation menu (in the top bar).
You can start by
```toml
  sectionPagesMenu = "main"
```
The menu will list the sections, and the pages in `/content`.

You can also customize the menu
```toml
[menu]

[[menu.main]]
identifier = "id of the item 1"
name = "Item 1"
url = "/<url of the item 1>"
weight = 10

[[menu.main]]
identifier = "id of the item 2"
name = "Item 2"
pre  = "html code to be added before the name"
url = "/<url of the item 2>"
weight = 20
# ...
```
The `weight` field define the order of the item in the list (smaller weights are displayed first).

Example:
```toml
[[menu.main]] 
  identifier = "photo"
  name       = "Photography"
  pre        = "<i class='bi-camera'></i>"
  url        = "/photo/"
  weight     = 20
```

### Search configuration

For a more accurate search, you can specify the sections in which your posts are, using the `mainSection` parameter:

```toml
[params]
  mainSections = [ "blog", "architecture", "project", "photo" ]
```

## SEO and other configurations

### SEO configuration

**Goliath** proposes a complete head in each page with metadata, links, and informations used by searchbot, and social medias.

```
theme                  = "golyat"
title                  = "< title of the blog >"
baseURL                = "< root url >"
DefaultContentLanguage = "ll"
LanguageCode           = "ll-cc"
copyright              = "2008-2022 (c) Emmanuel Georjon"  # Use in the RSS Internal template

[params]
  description         = "< description used if not description is found in the page to display"
  keywords            = [ "Project Management", "Architecture IT", "Photo", "gestion de projet", "urbanisation" ]
  themecolor          = "< main color of the theme >"
  opengraph           = "theme"      # Internal (default Hugo template), theme (the theme's template), or none
  twitterCards        = "theme"      # Internal (default Hugo template), theme (the theme's template), or none
  schema              = "theme"      # Internal (default Hugo template), theme (the theme's template), or none

[author]
  name                = "< name of the site webmaster >"
```

About `opengraph`, `twitter` and `schema`: 
* By default, Hugo provides internal templates. 
* The theme **Goliath** provides its own template, in order to provide additional features.
* You can choose to use internal templates, **Goliath** template by setting `theme`, `internal` values.

==> Sitemap

### RSS configuration

By default, Hugo provide an internal template for generating the RSS files.
The theme **Goliat** proposes an enhanced version of the RSS template, including images, link to the licence.

** If you want to use the internal RSS feeds, 

* You have to delete the file `/themes/goliat/layout/_default/rss.xml`**
* The following parameters will be used

```toml
title         = "< title of the blog >"
LanguageCode  = "fr-fr" # or en-US, ...
copyright     = "< Copyright sentence >"

[Config.Services.RSS]
  Limit       = 5

[author]
  name        = "< name of the site webmaster >"
  email       = "< email adress >"
```

** If you want to use the theme's RSS feeds, you need to ensure the the following fields**

You can configure the RSS feeds by using the following parameters:

```toml
title         = "< title of the blog >"
LanguageCode  = "fr-fr" # or en-US, ...
copyright     = "< Copyright sentence >"

[params]
  LicenceURL  = "https:// < url to the licence > "  # Example: http://creativecommons.org/licenses/by-nc/4.0/
  Description = "< description >"

[Config.Services.RSS]
  Limit       = 5

[author]
  name        = "< name of the site webmaster >"
  email       = "< email adress >"
```

** In both cases**

Whatever your choice (internal template, or Goliath's template), you have to specify in the file `config.toml`, where you want to build the RSS feeds.
In the following example, the RSS files will be generate for the home page, and each of the sections:

```toml
[outputs]
  home        = [ "HTML", "RSS" ]
  section     = [ "HTML", "RSS" ]
```

### File site.manifest

**Goliath** can generate the manifest file of your site. In order to enable this feature, the `config.toml` file must contain the following parameters:
```toml
[mediaTypes]
  [mediaTypes."application/manifest+json"]
    suffixes = [ "webmanifest" ]

[outputFormats]
  [outputFormats.webmanifest]
    baseName    = 'site'
    isPlainText = true
    mediaType   = 'application/manifest+json'
    rel         = "manifest"

[outputs]
  home    = [ "HTML", "... ...", "webmanifest" ]
```

With this configuration, Hugo will generate a file `site.webmanifest`, in the root of the site. 
Then, the information that will be put into the file, can be tuned with the following parameters:

```toml
[params.manifest]
  name            = ""    # Default: Site title
  shortName       = ""    # no default
  lang            = ""    # Default: languageCode
  display         = ""    # Default: browser
  start_url       = ""    # Default: .Site.BaseURL
  theme_color     = ""    # Default: themecolor field in [Params] or #fff
  backgroundColor = ""    # Default: #fff
  description     = ""    # Default: Description field in [Params]
  orientation     = ""    # Default: Portrait
  scope           = ""    # Default: Scope
  favicons        = ""    # Default: /assets/favicons
```

## Content configuration

### Meta information

* `meta`: list of meta field to be displayed, with the display order. The available fields are
  * section,
  * date,
  * reading (the estimation duration of read),
  * tags,
  * authors,
  * category.

Example: 

```toml
[params.list]
  postcolumns   = { "sm" = 1, "md" = 1, "lg" = 2, "xl" = 2 }
  displayimage  = false
  meta = { 1 = "section", 2 = "date", 3 = "reading", 4 = "tags" }
#    meta = { 1 = "section", 2 = "date", 3 = "reading", 4 = "tags", 5 = "authors", 6 = "category" }
```

### Widgets

==> Widgets

Three widgets area

* The homepage itself,
* The bottom area of the posts,
* The footer


You can also configure what is displayed at the bottom of the post. You can selected "widgets".

Example: 
```toml
[params.Single.Widgets]
  related     = { type = "series-or-related", weight = 3 }
  share       = { type = "share-links",       weight = 2 }
  author      = { type = "authors",           weight = 1 }
``` 

The `weight` allow to display the widgets is a specific order.
The possible widgets listed in the chapter [Footer](#Footer)

### Footer

The top part of the footer contains widgets. You can select the widgets you want to display. The syntax is the following:

```toml
[params.FooterWidgets]
  columns    = { <number of columns according the screen's width> }
  [params.FooterWidgets.Widgets]
    [params.FooterWidgets.Widgets.<widget id>]
      type   = "<type of the widget>"
      weight = <order>
```

Example:
```toml
[params.FooterWidgets]
  columns    = { "sm" = 1, "md" = 2, "lg" = 2, "xl" = 3 }
  [params.FooterWidgets.Widgets]
    [params.FooterWidgets.Widgets.series]
      type   = "series"
      weight = 1
    [params.FooterWidgets.Widgets.about-links]
      type   = "text"
      weight = 2
      params = "links"
    [params.FooterWidgets.Widgets.followme]
      type   = "follow"
      weight = 3
```

The possible widgets are 

| Widget            | Description  |
|-------------------|----------------------------------------------|
| authors           | Display the list of the authors of the posts |
| categories        | Give the lst of sections |
| follow            | Display a list of "follow" links |
| related-posts     | Give a list of posts related to the current post |
| same-series       | Display the list of posts belonging to the same serie than the current post |
| series-or-related | a combination of the two previous widgets |
| series            | List of the series |
| share-links       | set of links to share the current post |
| tags-cloud        | Display the cloud of the tags |
| tags              | List of tags |
| text              | Display the content of a file / post |


Of course, if you want, you can develop you own widget, and put it in the folder `themes\Goliath\layout\partial\widgets`.

### Footer (bottom)

The bottom part of the footer shows the copyright information of the site.
The parameters are grouped into the `[Params.copyright]` section.

```toml
[params.copyright]
  FirstDate     = "first date of the publication"
  Attribution   = "Name of the blog's owner"
  SentenceSmall = "reduced copyright sentence"
  SentenceFull  = "the full copyright sentence, with all details"
```

Example:

```toml
[params.copyright]
  FirstDate     = "2008"
  Attribution   = "Emmanuel Georjon"
  SentenceSmall = "[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode), thème [Goliath](https://github.com/egeorjon/Goliath)"
  SentenceFull  = "Contenu sous license Creative Commons [BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode), thème [Goliath](https://github.com/egeorjon/Goliath)"
```

## Design configuration

The design of the site can be updated in several manners

* You can change the color scheme, by modifying the stylesheet,
* You can change the way the site manages device width,
* You can choose the posts format in the posts list (whatever the list)

**Change the color scheme**

For changing colors, you can edit the file `themes/goliath/assets/styles.scss`, and change the following lines

```scss
    $primary:       "color 1";
    $secondary:     "color 2";
    $light:         "color 3";
    $medium:        "color 4";
    $dark:          "color 5";
```

**Change the site's layout according the device width**

**Goliath** is based on the [BootStrap](https://getbootstrap.com/) framework. This framework use a set of breakpoints to adjust the site layout according the device with
```scss
    $grid-breakpoints: (
    xs: 0,          # eXtra Small
    sm: 576px,      # SMall
    md: 768px,      # MeDium
    lg: 992px,      # LarGe
    xl: 1200px,     # eXtra Large
    xxl: 1400px     # eXtra eXtra Large
) !default;
```

In the configuration file `config.toml`, you can change this adjustment, by selecting the number of columns you want according the width. For example, if you want to display the list of posts using two columns (and not only one), you can update the following value:
```toml
[params.list]
  columns = { "sm" = 1, "md" = 2, "lg" = 2, "xl" = 2 }
```

=> Image.

The parameter `columns` is used in many places in the theme, mainly in the widgets area (in the homepage, for example, or the footer).

**Change the format of the posts displayed in the post's list**

You can choose the format of the posts displayed in lists (sections, tags, categories, series, ...). You have 4 formats available:

| image-left | image-right | image-top | no-image |
|------------|-------------|-----------|----------|
| ![](#) | ![](#) | ![](#) | ![](#) |

**Combination of columns, and posts' format**

If you combine the two last points, you can drastically change the theme layout: 

==> ![](#)


## Configuration of the social media

The social links can be configured also
```toml
[params.followlinks]
twitter = "<link to your Twitter account"
github = "<link to your GitHub account>"
facebook = "<link to your facebook account>"
pinterest = "<link to your PInterest account>"
linkedin = "<link to your LinkedIn account>"
rss = "<link to your RSS file>"
```
Example:
```toml
[params.followlinks]
twitter = "https://twitter.com/johndoe"
github = "https://github.com/johndoe"
facebook = ""
pinterest = ""
linkedin = "https://linkedin.com/in/johndoe"
rss = ""
```

### SEO features

You can configure the S.E.O features with the following parameters:

```toml
[params]
  description   = "short description of the blog" # Short description for the meta description
  keywords      = [ "keyword 1", "keyword 2", "... ...", "keyword n" ] # List of tags for the meta keywords
  opengraph     = true # Enable OpenGraph if true
  schema        = true # Enable Schema JSON file
  twitter_cards = true # Enable Twitter Cards if true
  themecolor    = "#ffffff"
```

### Favicons

If you want to setup [favicons](https://en.wikipedia.org/wiki/Favicon "Favicons definition in Wikipedia"), you just need to put the file in the folder `/static/assets/favicons`.

The name of the icons 

* for IOS (apple), must start by `apple`,
* for androit must start by `android`, 
* for the legacy browsers with `favicon.ico`, 
* for the microsoft operating systems, must start with `ms-`, 

You can configure also an SVG icon (any name with the `svg` extension).

For example:
```
android-icon-512x512.png
android-icon-96x96.png
android-icon_192x192.png
apple-touch-icon-120x120.png
apple-touch-icon-152x152.png
apple-touch-icon-167x167.png
apple-touch-icon-180x180.png
favicon.ico
ms-icon-144x144.png
site-logo.svg
```

### RSS feeds

The RSS file is generated by the default Hugo template. The feeds can be configured using the following parameters:
```toml
copyright = "(c) 2008-2022 Your own copyright string"  # Use in the RSS Internal template

[config.services.rss]
  limit = 10 # max number of posts to be displayed

[author] # Used in RSS internal template
  name  = "Firstname Lastname"
  email = "blog@firstname.suffix"
```

You have also to specify for which page you want to generate a RSS file
In the following example, the RSS file will generated for the home page, and for each section.

```toml
[outputs]
  home    = ["HTML", "RSS", "JSON", "MANIFEST"]
  section = ["HTML", "RSS"]
```

### Sitemap

The theme generates the `sitemap.xml`.
It uses the standard Hugo's template. The configuration can be done with the parameters described in the [Hugo's documentation](https://gohugo.io/variables/sitemap/#readout)

Example: 

```toml
[sitemap]
  changefreq = "weekly"
  filename = "sitemap.xml"
  priority = 0.5
```


## Advanced configuration

### Manifest file

The theme is able to generate the **manifest** file of the site.
In order to allow this, you have to add the following parameters

```toml
[outputFormats]
  [outputFormats.MANIFEST]
    mediaType       = "application/json"
    baseName        = "manifest"
    isPlainText     = true
    notAlternative  = true

[outputs]
  home    = ["HTML", "RSS", "JSON", "MANIFEST"]
```

### Styles

So far, the theme doen't provide an easy way to customize styles.
However, you can customize the theme with two ways

* All default `Bootstrap` values used by the theme are in the file `themes/Goliath/assets/customization.scss`.
* The theme styles are in the file `themes/Goliath/assets/styles.scss`

The theme uses the icons from [FontAwesome](https://fontawesome.com/). You can add icons if required, by editing the file `themes/Goliath/assets/fontawesome-free-5.15.2-web/scss/_icons.scss`, and uncomment the line corresponding to the icon you want to display.