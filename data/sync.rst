Synchronization
===============

There is no built-in support for synchronizing access to data sources. You can take two different approaches to ensuring
thread safety.

Option 1
--------

The first and more simple option is by avoiding the problem altogether. Just don't update the GUI while your application
is accessing the data sources. Simple.

Option 2
--------

The second option involves implementing some kind of synchronization in the data sources. At present, :code:`Floah` does
not provide any facilities to ease this process.

There are some obvious pitfalls that should be avoided. Widgets can have multiple data sources, making it very easy
to cause deadlocks. If a widget calls a setter on a data source, the data source will notify listeners inside of that
setter. If those listeners call the getter, that too has a potential for deadlocks.
