# Feedburst!

[![Build status](https://ci.appveyor.com/api/projects/status/wsg83k3i456yi32s?svg=true)](https://ci.appveyor.com/project/porglezomp/feedburst)
[![Build Status](https://travis-ci.org/porglezomp-misc/feedburst.svg)](https://travis-ci.org/porglezomp-misc/feedburst)

Feedburst is a tool that presents you your RSS feeds in chunks, according to a policy that you set.

## Configuring

Feedburst is configured with a config file containing all the comics you'd like to read, and policy about when and how you'd like to read them.
Entries in that config file look like the following:

```
# A nice friendly comic
"Goodbye to Halos" <http://goodbyetohalos.com/feed/> @ 2 new comics @ overlap 1 comic @ on monday
```

The `"Title"` is whatever title you’d like to display the comic as.
The `<link>` is a link to the RSS feed to pull the comics from.
The `@policy` are rules for when and how you’d like that comic feed to be presented to you.
Any line that begins with with a `#` will be treated as a comment and ignored.

- `@ # new comic(s)`: Wait for there to be at least # new comics before you see them.
- `@ overlap # comic(s)`: Show the last # comics that you read.
- `@ on monday/tuesday/etc…`: Show the comics once the corresponding day has passed.
- `@ every # day(s)`: Wait at least # days since you last read the comic.


Due to a bug, you currently must make sure that the config file ends with a newline.
Sorry for the inconvenience, it should be fixed shortly.

## Config Location

By default, on macOS and Linux, the config file is stored at:

```
~/.config/feedburst/config.feeds
```

and on Windows, it's stored at

```
C:\Users\USERNAME\AppData\Roaming\porglezomp\feeedburst\config.feeds
```

Technically, on macOS and Linux, the config file is stored according to the `$XDG_CONFIG_DIR` environment variable.
If you want to customize it beyond that, on any platform, you can set a base path with the `$FEEDBURST_CONFIG_PATH` environment variable.
If you want to use a different config for a single run, then use `--config FILE` on the command line.