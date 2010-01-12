Supported options
=================

The recipe supports the following options:

The recipe supports the following options:

url
    URL pointing to the ``haproxy`` compressed archive.
http://dist.plone.org/thirdparty/haproxy-1.3.22.zip by default.

target
    TARGET=(linux22|linux24|linux24e|linux24eold|linux26|solaris|freebsd|openbsd|generic)

cpu
    CPU=(i686|i586|ultrasparc|generic)

pcre
    USE_PCRE=(0|1)


Example usage
=============

We'll start by creating a buildout that uses the recipe::

    >>> write('buildout.cfg',
    ... """
    ... [buildout]
    ... parts = haproxy
    ...
    ... [haproxy]
    ... recipe = plone.recipe.haproxy
    ... url = %(url)s
    ... """ % { 'url' : 'http://dist.plone.org/thirdparty/yxorpah-1.3.22.zip'})

Running the buildout gives us::

    >>> print system(buildout)
    Installing haproxy.
    haproxy: Downloading http://dist.plone.org/thirdparty/yxorpah-1.3.22.zip
    While:
      Installing haproxy.
    <BLANKLINE>
    An internal error occured due to a bug in either zc.buildout or in a
    recipe being used:
    Traceback (most recent call last):
    ...
    HTTPError: HTTP Error 404: Not Found
    <BLANKLINE>

