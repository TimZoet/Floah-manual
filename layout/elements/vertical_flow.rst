Vertical Flow
=============

The :code:`floah::VerticalFlow` element lays out all its sub-elements next to each other along the vertical axis.
The area covered in which the sub-elements are placed is defined by the bounds of the flow element minus its
:code:`innerMargin`.

.. figure:: /_static/images/elements/vertical_flow/base.svg

    Vertical Flow.

Size
----

The size of each sub-element, if not absolute, is calculated relative to the size of the flow area.

.. figure:: /_static/images/elements/vertical_flow/size.svg

    Relative size.

Vertical Alignment
------------------

The vertical positioning of each sub-element is determined using the :code:`verticalAlignment` of the flow element.
Sub-elements are laid out from top-to-bottom or bottom-to-top. The :code:`outerMargin` of each sub-element is used as an
offset between neighbouring elements. The following alignment values are supported:

* :code:`Top`: First sub-element is placed at the top of the flow area, offset to the bottom by
  :code:`sub.outerMargin.top`. All subsequent elements are placed to the bottom, offset by the :code:`top` and
  :code:`bottom` margins.
* :code:`Bottom`: Last sub-element is placed at the bottom of the flow area, offset to the top by
  :code:`sub.outerMargin.bottom`. All subsequent elements are placed to the top, offset by the :code:`top` and
  :code:`bottom` margins.

.. figure:: /_static/images/elements/vertical_flow/valign.svg

    Vertical alignment (:code:`Top`, :code:`Bottom`).

Horizontal Alignment
--------------------

The horizontal positioning of each sub-element is determined using the :code:`horizontalAlignment` of the flow,
optionally offset by the :code:`outerMargin` of the sub-element. The following alignment values are supported:

* :code:`Left`: Sub-element is placed at the left of the flow area, offset to the right by :code:`sub.outerMargin.left`.
* :code:`Center`: Sub-element is placed at the center of the flow area.
* :code:`Right`: Sub-element is placed at the right of the flow area, offset to the left by
  :code:`sub.outerMargin.right`.

.. figure:: /_static/images/elements/vertical_flow/halign.svg

    Horizontal alignment (:code:`Left`, :code:`Center`, :code:`Right`).
