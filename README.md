# NAME

App::proxyforurl - An online proxy PAC file parser

# DESCRIPTION

[App::proxyforurl](https://metacpan.org/pod/App%3A%3Aproxyforurl) is a web application that can be used to test proxy PAC
files.

The [server side](https://metacpan.org/pod/Mojolicious) is used to serve the web page, but does also
provide functionality for resolving hostnames and checking if an IP is within
a given net.

## Demo

Check out [https://thorsen.pm/proxyforurl](https://thorsen.pm/proxyforurl) for a running example.

## Missing features

The client side PAC parser does not fully support `dateRange()`, `timeRange()`
or `weekdayRange()`. These functions simply return true, no matter what the
input is.

# SYNOPSIS

    $ proxyforurl --listen http://*:8080;

With optional environment variables:

    $ PROXYFORURL_TEMPLATES=/path/to/templates \
      PROXYFORURL_BRAND_NAME=Thorsen \
      PROXYFORURL_BRAND_URL=https://thorsen.pm \
      PROXYFORURL_X_REQUEST_BASE="https://thorsen.pm/proxyforurl" \
      proxyforurl --listen http://*:8080;

- PROXYFORURL\_TEMPLATES

    Can be set to a custom directory to override templates.

- PROXYFORURL\_BRAND\_NAME, PROXYFORURL\_BRAND\_URL

    Used to change the menu item text and URL.

- PROXYFORURL\_X\_REQUEST\_BASE

    Can be set to a custom request base, in case the app is not mounted at "/".

# SEE ALSO

- [https://findproxyforurl.com/](https://findproxyforurl.com/)
- [https://github.com/pacparser/pacparser](https://github.com/pacparser/pacparser)

# DISCLAIMER

The parsing is done using good old `eval()` on the client side, which means
that the pasted PAC file could in theory contain code which could steal
cookies, inject alien JavaScript or do other harmful things.

There is a safety net installed to prevent this from happening, but since
this is software, there might be bugs.

# COPYRIGHT AND LICENSE

Copyright (C) Jan Henning Thorsen

This program is free software, you can redistribute it and/or modify it under
the terms of the Artistic License version 2.0.

# AUTHOR

Jan Henning Thorsen - `jhthorsen@cpan.org`
