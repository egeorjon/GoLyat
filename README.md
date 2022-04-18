# GoLyat
GoHugo Theme


### Search configuration

For a more accurate search, you can specify the sections in which your posts are, using the `mainSection` parameter:

```toml
[params]
  mainSections = [ "blog", "architecture", "project", "photo" ]
```

### RSS configuration

Hugo generates a RSS file for the site, and for each of the sections. You can configure the RSS feeds by using the following parameters:

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

[outputs]
  home        = [ "HTML", "RSS" ]
  section     = [ "HTML", "RSS" ]
```

### Configuration du fichier site.manifest

In order to tell to Hugo that it has to generate the file, the `config.toml`file must contain the following parameters:
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
  home    = [ "HTML", "RSS", "JSON", "webmanifest" ]
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