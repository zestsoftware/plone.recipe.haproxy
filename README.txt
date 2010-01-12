
.. contents::

- Code repository: http://svn.plone.org/svn/collective/buildout/plone.recipe.haproxy
- Questions and comments to aclark@aclark.net.
- Report bugs aclark@aclark.net.

Supported options
=================

This recipe supports the following options:

url
    URL pointing to the ``haproxy`` compressed archive. http://dist.plone.org/thirdparty/haproxy-1.3.22.tar.gz
    by default.

target
    TARGET=(linux22|linux24|linux24e|linux24eold|linux26|solaris|freebsd|openbsd|generic)

cpu
    CPU=(i686|i586|ultrasparc|generic)

pcre
    USE_PCRE=(1)


Example usage
=============

By default, this recipe should work with no options specified, e.g.::

    [buildout]
    parts +=
        ...
        haproxy

    [haproxy]
    recipe = plone.recipe.haproxy

This will configure the default options for ``url``, ``target``, ``pcre``, and ``cpu``.
If you like or need to, you can override any of these parameters,
e.g.::

    [haproxy]
    recipe = plone.recipe.haproxy
    url = http://haproxy.1wt.eu/download/1.3/src/haproxy-1.3.22.tar.gz
    target = linux26
    cpu = i686
    pcre = 1

Tests
=====

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

Running the buildout with a known bad URL gives us::

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

XXX If you are reading this, please consider adding more tests ;-) 

