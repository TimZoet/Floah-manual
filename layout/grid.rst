Grid
====

The :code:`floah::Grid` element defines :code:`N x M` cells into which other elements can be inserted. Thus, these
sub-elements are placed at regular intervals. The area covered by the cells is defined by the bounds of the grid element
minus its :code:`innerMargin`. Therefore, each cell has a width and height that is equal to:

.. code-block:: cpp

    cell.width  = (bounds.width  - innerMargin.left - innerMargin.right)  / columnCount;
    cell.height = (bounds.height - innerMargin.top  - innerMargin.bottom) / rowCount;

.. figure:: /_static/images/elements/grid/base.svg

    A 2x2 :code:`Grid`.

Size
----

The size of each sub-element, if not absolute, is calculated relative to the size of a cell.

.. figure:: /_static/images/elements/grid/size.svg

    Relative size.

Horizontal Alignment
--------------------

The horizontal positioning of each sub-element inside its cell is determined using the :code:`horizontalAlignment` of
the grid, optionally offset by the :code:`outerMargin` of the sub-element. The following alignment values are supported:

* :code:`Left`: Sub-element is placed at the left of the grid cell, offset to the right by :code:`sub.outerMargin.left`.
* :code:`Center`: Sub-element is placed at the center of the grid cell.
* :code:`Right`: Sub-element is placed at the right of the grid cell, offset to the left by :code:`sub.outerMargin.right`.

.. figure:: /_static/images/elements/grid/halign.svg

    Horizontal alignment (:code:`Left`, :code:`Center`, :code:`Right`).

Vertical Alignment
------------------

The vertical positioning of each sub-element inside its cell is determined using the :code:`verticalAlignment` of the
grid, optionally offset by the :code:`outerMargin` of the sub-element. The following alignment values are supported:

* :code:`Top`: Sub-element is placed at the top of the grid cell, offset to the bottom by :code:`sub.outerMargin.top`.
* :code:`Middle`: Sub-element is placed at the middle of the grid cell.
* :code:`Bottom`: Sub-element is placed at the bottom of the grid cell, offset to the top by :code:`sub.outerMargin.bottom`.

.. figure:: /_static/images/elements/grid/valign.svg

    Vertical alignment (:code:`Top`, :code:`Middle`, :code:`Bottom`).
