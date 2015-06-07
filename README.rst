This project for test sphinx internationalization
=================================================

Init project
------------

::

    mkdir sphinx_test
    cd sphinx_test/
    mkvirtualenv sphinx_test
    workon sphinx_test
    pip install -U Sphinx
    pip install sphinx-intl
    pip freeze > requirements.txt
    git init
    gvim README.rst

Prepare for internationalizaton
-------------------------------

Add configurations to your conf.py::

    locale_dirs = ['locale/'] # path is example but recommended.
    gettext_compact = False # optional, defalut for sphinx.

run in shell::

    make gettext

You will find pot files in `_build/locale` .

Setup/Update your locale_dir::

    >>> sphinx-intl update -p _build/locale -l zh_CN
    Create: locale/zh_cn/LC_MESSAGES/index.po
    Create: locale/zh_cn/LC_MESSAGES/README.po

Build mo files and make translated document.
You need a language parameter in `conf.py` or you may also specify the
parameter on the command line::

    >>> sphinx-intl build
    Build: locale/zh_cn/LC_MESSAGES/README.mo
    Build: locale/zh_cn/LC_MESSAGES/index.mo

    >>> make -e SPHINXOPTS="-D language='zh_CN'" html


    sphinx-intl update -p _build/locale
