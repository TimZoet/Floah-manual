Data Sources
============

As stated, this module only defines data source interfaces. All interface classes derive from :code:`floah::DataSource`
and declare a number of virtual methods that must be implemented by concrete classes. The simplest built-in interface
would probably be :code:`floah::IBoolDataSource`, implementations of which should provide access to a single boolean
value. Whether or not such an implementation owns that boolean, or has itself a reference to some object that holds a
value that isn't even a boolean, but converted in the get and set method of the data source, is left to the user.

All widgets need a reference to one or more data sources in order to display and modify their values. More complex
widgets can for instance combine a :code:`floah::IListDataSource` with a :code:`floah::IIntegralValueDataSource`, using
the latter as an index into the former.

Whenever data changes, widgets might need updating. Data sources keep a list of listeners that are informed of changes
when the data source calls its :code:`emitDataSourceUpdate` method. A proper data source implementation will call this
method in all its members that modify the underlying data. In case changes to the data are not made through the data
sources, you can still call this method from outside, though. Refer to :doc:`listener` for information on how widgets
can register for update events.
