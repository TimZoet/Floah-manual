Radio Button
============

The :code:`floah::RadioButton` widget represents multiple options of which only one can be turned on at a time. For each
option, a separate widget is needed. There should be one main widget, with all other widgets receiving a reference to
that widget on construction. Together, they form a single group of radio buttons of which only one can be selected at a
time. When a button is clicked, the main button will update all buttons.

.. code-block:: cpp

    floah::Panel&         panel = ...;
    floah::LayoutElement& elem0 = ...;
    floah::LayoutElement& elem1 = ...;

    // Setup main RadioButton.
    auto& radio0 = panel.addWidget(std::make_unique<floah::RadioButton>());
    radio0.setLabel("Option A");
    radio0.setPanelLayoutElement(elem0);
    
    // Setup secondary RadioButton with reference to main.
    auto& radio1 = panel.addWidget(std::make_unique<floah::RadioButton>(radio0));
    radio1.setLabel("Option B");
    radio1.setPanelLayoutElement(elem1);

Data
----

The :code:`floah::RadioButton` widget retrieves its value from an :code:`floah::IBoolDataSource`. Each button in a group
should receive its own data source.

.. code-block:: cpp

    floah::IBoolDataSource& dataSource0 = ...;
    floah::IBoolDataSource& dataSource1 = ...;
    radio0.setDataSource(&dataSource0);
    radio1.setDataSource(&dataSource1);

Style
-----

.. csv-table:: 
    :file: /_static/tables/widget/radiobutton_style.csv
    :header-rows: 1

Layout
------

.. figure:: /_static/images/widget/radio_button/layout.svg

    RadioButton layout.

Scenegraph
----------

.. figure:: /_static/images/widget/radio_button/scenegraph.svg

    RadioButton scenegraph.
