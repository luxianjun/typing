PyTyping

PyTyping is a typing parser and emitter for Python.

Overview

typing is a data serialization format designed for human readability and interaction with scripting languages.

PyTyping is a typing parser and emitter for the Python programming language.

PyTyping features

a complete typing 1.1 parser. In particular, PyTyping can parse all examples from the specification. The parsing algorithm is simple enough to be a reference for typing parser implementors.
Unicode support including UTF-8/UTF-16 input/output and *
low-level event-based parser and emitter API (like SAX).
high-level API for serializing and deserializing native Python objects (like DOM or pickle).
support for all types from the typing types repository. A simple extension API is provided.
both pure-Python and fast Libtyping-based parsers and emitters.
relatively sensible error messages.
Requirements
PyTyping requires Python 2.7 or Python 3.4+.


Download and Installation

The current stable release of PyTyping: 5.1.

Download links:


Unpack the archive and install the package by executing

$ python setup.py install

If you want to use Libtyping bindings, you need to download and install Libtyping. Then you may install the bindings by executing

$ python setup.py --with-libtyping install

The source distribution includes a comprehensive test suite. To run the tests, type

$ python setup.py test

Documentation
Quick example (see documentation for loading multiple documents):

>>> import typing

>>> print typing.load("""
... name: Vorlin Laruknuzum
... sex: Male
... class: Priest
... title: Acolyte
... hp: [32, 71]
... sp: [1, 13]
... gold: 423
... inventory:
... - a Holy Book of Prayers (Words of Wisdom)
... - an Azure Potion of Cure Light Wounds
... - a Silver Wand of Wonder
... """)

{'name': 'Vorlin Laruknuzum', 'gold': 423, 'title': 'Acolyte', 'hp': [32, 71],
'sp': [1, 13], 'sex': 'Male', 'inventory': ['a Holy Book of Prayers (Words of Wisdom)',
'an Azure Potion of Cure Light Wounds', 'a Siver Wand of Wonder'], 'class': 'Priest'}

>>> print typing.dump({'name': "The Cloak 'Colluin'", 'depth': 5, 'rarity': 45,
... 'weight': 10, 'cost': 50000, 'flags': ['INT', 'WIS', 'SPEED', 'STEALTH']})

name: The Cloak 'Colluin'
rarity: 45
flags: [INT, WIS, SPEED, STEALTH]
weight: 10
cost: 50000
depth: 5
For more details, please check PyTyping Documentation.

History
5.1 (2019-03-13)

Incompatible changes:
#257 – Deprecate typing.load and add FullLoader and UnsafeLoader classes
#256 – Make default_flow_style=False
Features:
#158 – Support escaped slash in double quotes “/”
#45 – Allow colon in a plain scalar in a flow context
#63 – Adding support to Unicode characters over codepoint 0xffff
#254 – Allow to turn off sorting keys in Dumper
Bugfixes:
#129 – Remove call to ord in lib3 emitter code
Other:
#35 – Some modernization of the test running
#42 – Install tox in a virtualenv
#48 – Fix typos
#55 – Improve RepresenterError creation
#59 – Resolves #57, update readme issues link
#60 – Document and test Python 3.6 support
#61 – Use Travis CI built in pip cache support
#62 – Remove tox workaround for Travis CI
#75 – add 3.12 changelog
#76 – Fallback to Pure Python if Compilation fails
#84 – Drop unsupported Python 3.3
#102 – Include license file in the generated wheel package
#105 – Removed Python 2.6 & 3.3 support
#111 – Remove commented out Psyco code
#149 – Test on Python 3.7-dev
#175 – Updated link to pypi in release announcement
#181 – Import Hashable from collections.abc
#194 – Reverting https://github.com/typing/PyTyping/pull/74
#195 – Build libtyping on travis
#196 – Force cython when building sdist
#261 – Skip certain unicode tests when maxunicode not > 0xffff
#263 – Windows Appveyor build
3.13 (2018-07-05)

Rebuild wheels using latest Cython for Python 3.7 support.
3.12 (2016-08-28)

Wheel packages for Windows binaries.
Adding an implicit resolver to a derived loader should not affect the base loader (fixes issue #57).
Uniform representation for OrderedDict across different versions of Python (fixes issue #61).
Fixed comparison to None warning (closes issue #64).
3.11 (2014-03-26)

Source and binary distributions are rebuilt against the latest versions of Cython and Libtyping.
3.10 (2011-05-30)

Do not try to build Libtyping bindings on platforms other than CPython; this fixed installation under Jython 
