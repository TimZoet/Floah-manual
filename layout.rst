floah.layout
============

.. toctree::
    :maxdepth: 3
    :titlesonly:
    :hidden:

    layout/layout
    layout/layout_elements

The :code:`sol.layout` module contains classes to generate layouts for panels and widgets. Layout engines can get pretty
complicated, just look at what modern browsers do. In :code:`Floah`, the choice has been made to keep things a lot more
simple:

1. A layout has an absolute size. All elements below it either have an absolute size as well, or a size relative to
   their parent element. Child elements do not affect the size of their parent.
2. All sizes (whether they be lengths, offsets, margins, etc.) are unitless integers. It is up to you to decide if they
   represent pixels, centimeters, millimeters.
3. No animations. Scrolling through a list of items, cool rotating buttons... these must all be implemented on top of
   this module.

This keeps resolving layouts performant and predictable.
