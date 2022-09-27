Input Element
=============

The :code:`floah::InputElement` class defines a large number of interface methods for receiving input events.

At minimum, all deriving classes must implement the :code:`intersect` method. This is used by the input context to
determine if the mouse is hovering over an element, and therefore drives the sending of many mouse and keyboard events.

.. code-block:: cpp

    class YourWidget : public floah::Widget // floah::Widget inherits from floah::InputElement.
    {
    public:

        [[nodiscard]] bool intersect(math::int2 point) const noexcept override
        {
            // Do some kind of intersection test, for example with the bounds of some layout element.
            return intersectsWithThis(point);
        }
    };

Refer to :doc:`layers` for information on how elements are stacked on top of one another, and how the order in which
they receive events is determined.

Local / Global Space
--------------------

Panels (see :doc:`/widget/panel`) operate in their own local space. Therefore the cursor position must be transformed
from global space (typically the window coordinate system) to local space. This can be achieved by implementing the
:code:`getInputOffset` method.

The value returned will be used to offset the cursor position passed to the element for intersection and any of its
event methods. Note that the input context does not apply offsets recursively when it is traversing the input elements.
If an element has an offset and its parent has an offset as well, you are responsible for returning the sum of these two
values for the child element.

.. code-block:: cpp

    // Implementation of getInputOffset for the base Widget class.
    math::int2 Widget::getInputOffset() const noexcept
    {
        return panel->getInputOffset();
    }

Currently, :code:`Floah` supports translation only. Scaling is not (yet) implemented.

Mouse Events
------------

When it comes to mouse events, there are methods for all of the usual suspects: :code:`onMouseEnter`, 
:code:`onMouseClick`, :code:`onMouseScroll`, etc. Each method takes an :code:`*Event` object, describing what just
happened. For each event there is also a corresponding :code:`*Result` object, which can be used to instruct the input
context what to do with further events. Note that some of these event and result objects are as of yet empty.

When clicked, an element can claim further input events where normally other elements would take priority (either
because the mouse has completely left the element, or because an overlapping element is in a higher layer). This is
achieved by setting the :code:`claim` member of the :code:`MouseClickResult`. This can be used for e.g. a widget with a
text input field, where all key presses must be routed to the widget when selected. Or for a draggable slider, where the
mouse going outside of the element should be ignored until the left mouse button is released.

Keyboard Events
---------------

.. note::

    There are no keyboard events yet :(.
