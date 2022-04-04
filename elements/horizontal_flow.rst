Horizontal Flow
===============

The :code:`floah::HorizontalFlow` element lays out all its sub-elements next to each other along the horizontal axis.
The area covered in which the sub-elements are placed is defined by the bounds of the flow element minus its
:code:`innerMargin`.

.. figure:: /_static/images/elements/horizontal_flow/base.svg

    Horizontal Flow.

Size
----

The size of each sub-element, if not absolute, is calculated relative to the size of the flow area.

.. figure:: /_static/images/elements/horizontal_flow/size.svg

    Relative size.

Horizontal Alignment
--------------------

The horizontal positioning of each sub-element is determined using the :code:`horizontalAlignment` of the flow element.
Sub-elements are laid out from left-to-right or right-to-left. The :code:`outerMargin` of each sub-element is used as an
offset between neighbouring elements. The following alignment values are supported:

* :code:`Left`: First sub-element is placed at the left of the flow area, offset to the right by
  :code:`sub.outerMargin.left`. All subsequent elements are placed to the right, offset by the :code:`left` and :code:`right` margins.
* :code:`Right`: Last sub-element is placed at the right of the flow area, offset to the left by
  :code:`sub.outerMargin.right`. All subsequent elements are placed to the left, offset by the :code:`left` and :code:`right` margins.

.. figure:: /_static/images/elements/horizontal_flow/halign.svg

    Horizontal alignment (:code:`Left`, :code:`Right`).

Vertical Alignment
------------------

The vertical positioning of each sub-element is determined using the :code:`verticalAlignment` of the flow, optionally
offset by the :code:`outerMargin` of the sub-element. The following alignment values are supported:

* :code:`Top`: Sub-element is placed at the top of the flow area, offset to the bottom by :code:`sub.outerMargin.top`.
* :code:`Middle`: Sub-element is placed at the middle of the flow area.
* :code:`Bottom`: Sub-element is placed at the bottom of the flow area, offset to the top by :code:`sub.outerMargin.bottom`.

.. figure:: /_static/images/elements/horizontal_flow/valign.svg

    Vertical alignment (:code:`Top`, :code:`Middle`, :code:`Bottom`).
