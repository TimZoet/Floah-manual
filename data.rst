floah.data
==========

.. toctree::
    :maxdepth: 3
    :titlesonly:
    :hidden:

    data/source
    data/listener
    data/sync

The :code:`floah.data` module mainly defines :code:`DataSource` interfaces. These interfaces must be implemented, and 
should provide access to some underlying data. With a reference to one or more data sources, widgets can then read the
values for display and write them based on user input. Where the data is stored exactly, inside of the data sources or
elsewhere, is up to you. The built-in widgets never own the data, and only rely on data sources. When extending
:code:`Floah`, you should maintain this decoupling.

Additionally, a :code:`DataListener` class is available. All widgets should implement its interface. They can then
subscribe to update events from their sources, which are emitted when the data is modified.

.. figure:: /_static/images/data/data.svg

    Relationship between the application, data sources, and data listeners. Note the ambiguous :code:`<data>` box.
    Relationships and ownership are left to you, the user.
