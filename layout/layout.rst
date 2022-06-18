Layout
======

The :code:`floah::Layout` class holds a collection of hierarchical :code:`floah::LayoutElement` objects. After adding
and configuring these elements, you can generate 

A layout always requires an absolute size. Together with an (also absolute) offset, the area within which the layout
elements are placed is determined:

.. code-block:: cpp

    floah::Layout layout;

    // Set size to 256x512.
    layout.getSize().setWidth(floah::Length(256));
    layout.getSize().setHeight(floah::Length(512));

    // Set offset to 64x64.
    layout.getOffset().setWidth(floah::Length(64));
    layout.getOffset().setHeight(floah::Length(64));

Each layout must have exactly one root element. This root can be a layout element of any type. The size of elements can
be absolute or relative (or a mixture, e.g. a relative width but an absolute height):

.. code-block:: cpp

    // Create root element and configure with relative size to fill up whole layout.
    auto& root = layout.setRoot(std::make_unique<floah::HorizontalFlow>());
    root.getSize().setWidth(floah::Length(1.0f));
    root.getSize().setHeight(floah::Length(1.0f));

With a root element in place, you can start building a whole hierarchy of elements:

.. code-block:: cpp

    // Add 3 elements to root that have an absolute width that sums to 256,
    // and a relative height equal to the root height.
    auto& elem0 = root.append(std::make_unique<floah::LayoutElement>());
    elem0.getSize().setWidth(floah::Length(64));
    elem0.getSize().setHeight(floah::Length(1.0f));
    auto& elem1 = root.append(std::make_unique<floah::LayoutElement>());
    elem1.getSize().setWidth(floah::Length(64));
    elem1.getSize().setHeight(floah::Length(1.0f));
    auto& elem2 = root.append(std::make_unique<floah::LayoutElement>());
    elem2.getSize().setWidth(floah::Length(128));
    elem2.getSize().setHeight(floah::Length(1.0f));

Once you are happy with your layout, it is possible to generate it:

.. code-block:: cpp

    std::vector<floah::Block> blocks = layout.generate();

These :code:`floah::Block` structures are completely decoupled from the layout and elements, so you can discard those
if you no longer need them.
