Installation
************

.. rubric:: dependencies

Alot depends on recent versions of notmuch and urwid. Note that due to restrictions
on argparse and subprocess, you need to run *`3.0` > python ≥ `2.7`* (see :ref:`faq <faq_7>`).
A full list of dependencies is below:

* `libmagic and python bindings <http://darwinsys.com/file/>`_, ≥ `5.04`:
* `configobj <http://www.voidspace.org.uk/python/configobj.html>`_, ≥ `4.7.0`:
* `twisted <http://twistedmatrix.com/trac/>`_, ≥ `10.2.0`:
* `libnotmuch <http://notmuchmail.org/>`_ and it's python bindings, ≥ `0.13`.
* `urwid <http://excess.org/urwid/>`_ toolkit, ≥ `1.1.0`
* `PyGPGME <https://launchpad.net/pygpgme>`_ ≥ `0.2`

On debian/ubuntu these are packaged as::

  python-setuptools python-magic python-configobj python-twisted python-notmuch python-urwid python-gpgme

On fedora/redhat these are packaged as::

  python-setuptools python-magic python-configobj python-twisted python-notmuch python-urwid pygpgme

Alot uses `mailcap <http://en.wikipedia.org/wiki/Mailcap>`_ to look up mime-handler for inline
rendering and opening of attachments.  For a full description of the maicap protocol consider the
manpage :manpage:`mailcap(5)` or :rfc:`1524`. To avoid surprises you should at least have an inline
renderer (copiousoutput) set up for `text/html`, i.e. have something like this in your
:file:`~/.mailcap`::

  text/html;  w3m -dump -o document_charset=%{charset} '%s'; nametemplate=%s.html; copiousoutput

.. rubric:: get and install alot

You can use `pip` to install directly from GitHub::

  $ pip install --user https://github.com/pazz/alot/archive/master.zip

Or check out a more recent version, e.g. the master branch::

  $ pip install --user https://github.com/pazz/alot/archive/master.zip

Don't have pip installed? Just download and extract, then run::

  python setup.py install --user

Make sure :file:`~/.local/bin` is in your :envvar:`PATH`. For system-wide
installation omit the :option:`--user` flag and call with the respective
permissions.

.. rubric:: generate manual and manpage

To generate the documentation you need `sphinx <http://sphinx.pocoo.org/>`_, ≥ `1.07` installed.
Go to :file:`docs/` and do a::

  make html
  make man

to generate the user manual and a man page. Both will end up in their respective subfolders in
:file:`docs/build`.
