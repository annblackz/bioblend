.. image:: https://img.shields.io/pypi/v/bioblend.svg
    :target: https://pypi.python.org/pypi/bioblend/
    :alt: latest version available on PyPI

.. image:: https://img.shields.io/pypi/dm/bioblend.svg
    :target: https://pypi.python.org/pypi/bioblend/
    :alt: PyPI downloads in the last month

.. image:: https://readthedocs.org/projects/bioblend/badge/
    :alt: Documentation Status
    :target: https://bioblend.readthedocs.org/

.. image:: https://travis-ci.org/galaxyproject/bioblend.png
    :target: https://travis-ci.org/galaxyproject/bioblend
    :alt: Build Status

.. image:: https://landscape.io/github/galaxyproject/bioblend/master/landscape.svg?style=flat
    :target: https://landscape.io/github/galaxyproject/bioblend/master
    :alt: Code Health


BioBlend is a Python library for interacting with `CloudMan`_ and `Galaxy`_'s
API.

BioBlend is supported and tested on:

- Python 2.6, 2.7, 3.3 and 3.4
- Galaxy release_14.10 and later.

Full docs are available at http://bioblend.readthedocs.org with a quick library
overview also available in `ABOUT.rst <./ABOUT.rst>`_.

.. References/hyperlinks used above
.. _CloudMan: https://wiki.galaxyproject.org/CloudMan
.. _Galaxy: http://usegalaxy.org/


MORL FORK NOTES
The only file changed was the tool client logic which uploads files to galaxy.  See bioblend/galaxy/tools/__init__.py.  The logic was altered to support passing in a URL to use when interacting with Galaxy to upload files.  We needed this because the default URL used (api/tools) was bypassing nginx.  We needed to specify the following URL during file upload in order to allow nginx to handle the uploads from the API (note that uploading from the UI went through nginx): _upload?nginx_redir=/api/tools

We confirmed that nginx was not handling api uploads by initiating a http upload and tailing/monitoring the nginx log files (and comparing to what the log file looked like from a manual UI initiated upload of a file over http).
