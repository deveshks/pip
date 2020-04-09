.. _`pip show`:

========
pip show
========

.. contents::


Usage
=====

.. pip-command-usage:: show


Description
===========

.. pip-command-description:: show


Options
=======

.. pip-command-options:: show


Format
======

The various fields in the output and their  explanation is as follows. Note that the keys in JSON format are lowercased.
The fields below are present in the METADATA file, which follows the specification
laid down in `PEP-241`_, `PEP-314`_ and `PEP-345`_, with the same name as the fields, unless otherwise noted

The following fields are exposed by default.

- Name: The name of the distribution.
- Version: A string containing the distribution's version number.
- Summary: A one-line summary of what the distribution does.
- Home-page: A string containing the URL for the distribution's home page.
- Author: A string containing the author's name at a minimum; additional contact information may be provided.
- Author-email: A string containing the author's e-mail address.
- License: Text indicating the license covering the distribution where the license is not a selection from the "License" Trove classifiers.
  This field may also be used to specify a particular version of a license which is named via the Classifier field, or to indicate a variation or exception to such a license.
- Location: A string containing the path where the distribution is installed.
- Requires: Each entry contains a string describing some other module or package required by this package. (Requires-Dist in METADATA file)
- Required-by: Each entry contains a string describing some dependency in the system that the distribution is to be used.
  This is fetched by listing all distributions for which this distribution is in Requires-Dist of their METADATA file.

In verbose mode you also have access to:

- Metadata-Version: Version of the file format
- Installer: Value to to keep track of who installed the distribution (Defined in he `INSTALLER`_ section of PEP-376)
- Classifiers: Each entry is a string giving a single classification value for the distribution.
- Entry-points: Components provided by the distribution to be discovered and used by other code (Defined in `entry point specifications`_ of Python Packaging User Guide)

Finally, in files mode, you have access to:

- Files: List of installed files by the distribution (Defined in the `RECORD`_ section of PEP-376)

.. _PEP-241: https://www.python.org/dev/peps/pep-0241/
.. _PEP-314: https://www.python.org/dev/peps/pep-0314/
.. _PEP-345: https://www.python.org/dev/peps/pep-0345/
.. _INSTALLER: https://www.python.org/dev/peps/pep-0376/#installer
.. _RECORD: https://www.python.org/dev/peps/pep-0376/#record
.. _`entry point specifications`: https://packaging.python.org/specifications/entry-points/

Examples
========

#. Show information about a package in header format:

    ::

      $ pip show sphinx
      Name: Sphinx
      Version: 1.4.5
      Summary: Python documentation generator
      Home-page: http://sphinx-doc.org/
      Author: Georg Brandl
      Author-email: georg@python.org
      License: BSD
      Location: /my/env/lib/python2.7/site-packages
      Requires: docutils, snowballstemmer, alabaster, Pygments, imagesize, Jinja2, babel, six

#. Show all information about a package in header format excluding files:

    ::

      $ pip show --verbose sphinx
      Name: Sphinx
      Version: 1.4.5
      Summary: Python documentation generator
      Home-page: http://sphinx-doc.org/
      Author: Georg Brandl
      Author-email: georg@python.org
      License: BSD
      Location: /my/env/lib/python2.7/site-packages
      Requires: docutils, snowballstemmer, alabaster, Pygments, imagesize, Jinja2, babel, six
      Metadata-Version: 2.0
      Installer:
      Classifiers:
        Development Status :: 5 - Production/Stable
        Environment :: Console
        Environment :: Web Environment
        Intended Audience :: Developers
        Intended Audience :: Education
        License :: OSI Approved :: BSD License
        Operating System :: OS Independent
        Programming Language :: Python
        Programming Language :: Python :: 2
        Programming Language :: Python :: 3
        Framework :: Sphinx
        Framework :: Sphinx :: Extension
        Framework :: Sphinx :: Theme
        Topic :: Documentation
        Topic :: Documentation :: Sphinx
        Topic :: Text Processing
        Topic :: Utilities
      Entry-points:
        [console_scripts]
        sphinx-apidoc = sphinx.apidoc:main
        sphinx-autogen = sphinx.ext.autosummary.generate:main
        sphinx-build = sphinx:main
        sphinx-quickstart = sphinx.quickstart:main
        [distutils.commands]
        build_sphinx = sphinx.setup_command:BuildDoc

#. Show all information about a package in header format including files:

    ::

      $ pip show --verbose sphinx
      Name: Sphinx
      Version: 1.4.5
      Summary: Python documentation generator
      Home-page: http://sphinx-doc.org/
      Author: Georg Brandl
      Author-email: georg@python.org
      License: BSD
      Location: /my/env/lib/python2.7/site-packages
      Requires: docutils, snowballstemmer, alabaster, Pygments, imagesize, Jinja2, babel, six
      Metadata-Version: 2.0
      Installer:
      Classifiers:
        Development Status :: 5 - Production/Stable
        Environment :: Console
        Environment :: Web Environment
        Intended Audience :: Developers
        Intended Audience :: Education
        License :: OSI Approved :: BSD License
        Operating System :: OS Independent
        Programming Language :: Python
        Programming Language :: Python :: 2
        Programming Language :: Python :: 3
        Framework :: Sphinx
        Framework :: Sphinx :: Extension
        Framework :: Sphinx :: Theme
        Topic :: Documentation
        Topic :: Documentation :: Sphinx
        Topic :: Text Processing
        Topic :: Utilities
      Entry-points:
        [console_scripts]
        sphinx-apidoc = sphinx.apidoc:main
        sphinx-autogen = sphinx.ext.autosummary.generate:main
        sphinx-build = sphinx:main
        sphinx-quickstart = sphinx.quickstart:main
        [distutils.commands]
        build_sphinx = sphinx.setup_command:BuildDoc
      Files:
          ../../../bin/sphinx-apidoc
          ../../../bin/sphinx-autogen
          ../../../bin/sphinx-build
          ../../../bin/sphinx-quickstart
          Sphinx-1.4.5.dist-info/DESCRIPTION.rst
          Sphinx-1.4.5.dist-info/INSTALLER
          Sphinx-1.4.5.dist-info/METADATA
          Sphinx-1.4.5.dist-info/RECORD
          Sphinx-1.4.5.dist-info/WHEEL
          Sphinx-1.4.5.dist-info/entry_points.txt
          Sphinx-1.4.5.dist-info/metadata.json
          Sphinx-1.4.5.dist-info/top_level.txt
          .....

#. Show information about a package in json format:

    ::

        $ pip show sphinx
        [{
            "name": "Sphinx",
            "version": "1.4.5",
            "summary": "Python documentation generator",
            "home-page": "http://sphinx-doc.org/",
            "author": "Georg Brandl",
            "author-email": "georg@python.org",
            "license": "BSD",
            "location": "/Users/devesh/pip/.env/lib/python3.8/site-packages",
            "requires": ["snowballstemmer", "babel", "alabaster", "six", "docutils", "imagesize", "Pygments", "Jinja2"],
            "required-by": []
        }]

#. Show all information about a package in json format excluding files:

    ::

        $ pip show --verbose sphinx --format=json
        [{
            "name": "Sphinx",
            "version": "1.4.5",
            "summary": "Python documentation generator",
            "home-page": "http://sphinx-doc.org/",
            "author": "Georg Brandl",
            "author-email": "georg@python.org",
            "license": "BSD",
            "location": "/Users/devesh/pip/.env/lib/python3.8/site-packages",
            "requires": ["docutils", "babel", "snowballstemmer", "Pygments", "alabaster", "six", "Jinja2", "imagesize"],
            "required-by": [],
            "metadata-version": "2.0",
            "installer": "pip",
            "classifiers": ["Development Status :: 5 - Production/Stable", "Environment :: Console", "Environment :: Web Environment", "Intended Audience :: Developers", "Intended Audience :: Education", "License :: OSI Approved :: BSD License", "Operating System :: OS Independent", "Programming Language :: Python", "Programming Language :: Python :: 2", "Programming Language :: Python :: 3", "Framework :: Sphinx", "Framework :: Sphinx :: Extension", "Framework :: Sphinx :: Theme", "Topic :: Documentation", "Topic :: Documentation :: Sphinx", "Topic :: Text Processing", "Topic :: Utilities"],
            "entry-points": ["[console_scripts]", "sphinx-apidoc = sphinx.apidoc:main", "sphinx-autogen = sphinx.ext.autosummary.generate:main", "sphinx-build = sphinx:main", "sphinx-quickstart = sphinx.quickstart:main", "[distutils.commands]", "build_sphinx = sphinx.setup_command:BuildDoc"]
        }]

#. Show all information about a package in json format including files:

    ::

        $ pip show --verbose -f sphinx --format=json
        [{
            "name": "Sphinx",
            "version": "1.4.5",
            "summary": "Python documentation generator",
            "home-page": "http://sphinx-doc.org/",
            "author": "Georg Brandl",
            "author-email": "georg@python.org",
            "license": "BSD",
            "location": "/Users/devesh/pip/.env/lib/python3.8/site-packages",
            "requires": ["Jinja2", "docutils", "babel", "snowballstemmer", "alabaster", "imagesize", "six", "Pygments"],
            "required-by": [],
            "metadata-version": "2.0",
            "installer": "pip",
            "classifiers": ["Development Status :: 5 - Production/Stable", "Environment :: Console", "Environment :: Web Environment", "Intended Audience :: Developers", "Intended Audience :: Education", "License :: OSI Approved :: BSD License", "Operating System :: OS Independent", "Programming Language :: Python", "Programming Language :: Python :: 2", "Programming Language :: Python :: 3", "Framework :: Sphinx", "Framework :: Sphinx :: Extension", "Framework :: Sphinx :: Theme", "Topic :: Documentation", "Topic :: Documentation :: Sphinx", "Topic :: Text Processing", "Topic :: Utilities"],
            "entry-points": ["[console_scripts]", "sphinx-apidoc = sphinx.apidoc:main", "sphinx-autogen = sphinx.ext.autosummary.generate:main", "sphinx-build = sphinx:main", "sphinx-quickstart = sphinx.quickstart:main", "[distutils.commands]", "build_sphinx = sphinx.setup_command:BuildDoc"],
            "files": ["../../../bin/sphinx-apidoc", "../../../bin/sphinx-autogen", "../../../bin/sphinx-build", "../../../bin/sphinx-quickstart", "Sphinx-1.4.5.dist-info/DESCRIPTION.rst", "Sphinx-1.4.5.dist-info/INSTALLER", "Sphinx-1.4.5.dist-info/METADATA", "Sphinx-1.4.5.dist-info/RECORD", "Sphinx-1.4.5.dist-info/WHEEL", "Sphinx-1.4.5.dist-info/entry_points.txt", "Sphinx-1.4.5.dist-info/metadata.json", "Sphinx-1.4.5.dist-info/top_level.txt"]
        }]
