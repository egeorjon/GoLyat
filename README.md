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