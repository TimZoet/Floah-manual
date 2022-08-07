Checkbox
========

The :code:`floah::Checkbox` widget represents an option that can be turned on or off.

.. code-block:: cpp

    floah::Panel&        panel = ...;
    floah::LayoutElement& elem = ...;

    auto& checkbox = panel.addWidget(std::make_unique<floah::Checkbox>());
    checkbox.setLabel("Toggle Something");
    checkbox.setPanelLayoutElement(elem);

Data
----

The :code:`floah::Checkbox` widget retrieves its value from an :code:`floah::IBoolDataSource`.

.. code-block:: cpp

    floah::IBoolDataSource& dataSource = ...;
    checkbox.setDataSource(&dataSource);

Style
-----

.. csv-table:: 
    :file: /_static/tables/widget/checkbox_style.csv
    :header-rows: 1
