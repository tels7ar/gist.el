gist.el -- Emacs integration for gist.github.com
================================================

Uses your local GitHub config if it can find it.
See <http://github.com/blog/180-local-github-config>

Install
=======

    $ cd ~/.emacs.d/vendor
    $ git clone git://github.com/defunkt/gist.el.git

In your emacs config:

    (add-to-list 'load-path "~/.emacs.d/vendor/gist.el")
    (require 'gist)

You may want to tell tls.el to just use openssl to do fetches
instead of trying to use gnutls-cli:

    (setq tls-program '("openssl s_client -connect %h:%p -no_ssl2 -ign_eof"))

In my testing on Mac OS using https, gnutls-cli likes to hang forever.

Other branches of this script use curl instead of tls, so you might want
to check that out if you have problems with tls.

Functions
=========

    gist-list - Lists your gists in a new buffer. Use arrow keys
    to browse, RET to open one in the other buffer.

    gist-region - Copies Gist URL into the kill ring.
    With a prefix argument, makes a private gist.

    gist-region-private - Explicitly create a private gist.

    gist-buffer - Copies Gist URL into the kill ring.
    With a prefix argument, makes a private gist.

    gist-buffer-private - Explicitly create a private gist.

    gist-region-or-buffer - Post either the current region, or if mark
    is not set, the current buffer as a new paste at gist.github.com .
    Copies the URL into the kill ring.
    With a prefix argument, makes a private paste.

    gist-region-or-buffer-private - Explicitly create a gist from the
    region or buffer.

Config
======

Set `gist-view-gist` to non-nil if you want to view your Gist using
`browse-url` after it is created.

Set `github-user` and `github-token` to your GitHub credentials to
avoid checking `git-config`.

See <http://github.com/blog/180-local-github-config>

Meta
====

* Code: `git clone git://github.com/defunkt/gist.el.git`
* Home: <http://github.com/defunkt/gist.el>
* Bugs: <http://github.com/defunkt/gist.el/issues>

Hackery
=======

This version of gist.el includes support for dowloading private gists,
although it does not list them via gist-list.

This version also includes the switch from http to https github urls.
