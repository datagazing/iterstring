==========
iterstring
==========


.. image:: https://img.shields.io/pypi/v/iterstring.svg
        :target: https://pypi.python.org/pypi/iterstring

.. image:: https://img.shields.io/travis/datagazing/iterstring.svg
        :target: https://travis-ci.com/datagazing/iterstring

.. image:: https://readthedocs.org/projects/iterstring/badge/?version=latest
        :target: https://iterstring.readthedocs.io/en/latest/?version=latest
        :alt: Documentation Status




Simple class that allows writing lists and dicts as heredoc strings


* Free software: MIT license
* Documentation: https://iterstring.readthedocs.io.


Features
--------

* Handles comments (using # characters)
* Strips away extraneous whitespace with reasonable defaults (configurable)
* Coerce items to numbers where possible (see coerce)
* Iterating over the object treats it like a list
* Indexing the object treats it like a dictionary
* Listr and Distr functions are simplest interfaces

Examples
--------

.. code-block:: python

  >>> from iterstring import Listr # or Distr
  
  A simple use case:
  
  >>> some_list = Listr("""
  item one # with a comment
    2
  three
  """)
  >>> some_list
  ['item one', 2, 'three']
  >>> type(some_list)
  <class 'list'>
  
  Using the class directly:
  
  >>> from iterstring import Istr
  >>> asdf = Istr("""
  item one # with a comment
    2
  three
  """)
  >>> asdf.to_list()
  ['item one', 2, 'three']
  >>> type(asdf)
  <class 'iterstring.Istr'>
  
  >>> [x for x in asdf]
  ['item one', 2, 'three']
  
  >>> fdsa = Istr("""
  item one # with a comment
    2 some other value
  key3 3.14159
  """)
  >>> asdf.to_dict()
  {'item': 'one', 2: 'some other value', 'key3': 3.14159}
  >>> asdf.to_dict(coerce=False)
  {'item': 'one', '2': 'some other value', 'key3': '3.14159'}

Credits
-------

This package was created with Cookiecutter_ and the `audreyr/cookiecutter-pypackage`_ project template.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`audreyr/cookiecutter-pypackage`: https://github.com/audreyr/cookiecutter-pypackage