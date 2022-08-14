Layout Elements
===============

.. toctree::
    :maxdepth: 3
    :titlesonly:
    :hidden:

    elements/grid
    elements/horizontal_flow
    elements/vertical_flow

All elements in a layout are objects deriving from :code:`floah::LayoutElement`. In addition to various shared values
(e.g. size, inner- and outer margin), each class comes with its own set of configurable options. These are all
documented extensively on their respective page.

:code:`Floah` comes with a number of built-in layout element classes. Adding a new class is fairly straightforward. It
requires implementing no more than a handful of methods.
