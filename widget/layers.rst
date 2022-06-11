Layers
======

The order of widgets can be specified by creating layers and placing widgets on them. A layer has a unique name and an
integer depth. Layers with higher depth values are placed on top:

.. code-block:: cpp

    floah::Panel& panel = ...;

    auto& topLayer    = panel.createLayer("Top", 4);
    auto& middleLayer = panel.createLayer("Middle", 0);
    auto& bottomLayer = panel.createLayer("Bottom", -3);

.. figure:: /_static/images/widget/layers.svg

    The layer with the highest depth value is placed on top.

Widgets in higher layers are rendered on top of those in lower layers. They also receive mouse input (e.g. clicks)
before the widgets on lower layers. A widget's layer can be specified when adding it to the panel:

.. code-block:: cpp

    auto& widget0 = panel.addWidget(std::make_unique<SomeWidget>(...), topLayer);
    auto& widget1 = panel.addWidget(std::make_unique<SomeWidget>(...), bottomLayer);

If a widget has no layer assigned, its depth is assumed to be 0.
