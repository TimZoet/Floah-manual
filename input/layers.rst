Layers
======

The input layering system was made with the panel and widget system of :code:`Floah` in mind. Imagine you are
configuring two panels, each with their own widgets. If these panels intersect, you probably want widgets from one panel
to consistently be placed on top of the other panel's widgets. With just a depth value per widget, you have to carefully
order all of them correctly. That's a bit inconvenient. Therefore, a hierarchical approach is used. Panels are also
input layers with their own depth, and their child widgets are first sorted according to the panel depth and then,
inside of the panel layer, their own depth.

The input context or elements do not have an explicit list of layers. Instead, layers are defined implicitly through
parenting and an integer value. All classes deriving from :code:`floah::InputElement` can implement the
:code:`getInputParent` and :code:`getInputLayer`. These should return a pointer to a parent input element and an integer
depth, respectively. Mind you, there is actually no awareness of panels or widgets in this module. There's just a tree
of input elements, that can represent anything.

There are essentially 3 rules that determine how elements are ordered. If we have two elements :code:`A` and :code:`B`,
:code:`A` is placed on top if:

1. They share a parent (or both have no parent) and :code:`A.getInputLayer() > B.getInputLayer()`, or
2. :code:`A` is a descendant of :code:`B`, or
3. for the nearest ancestors :code:`A'` and :code:`B'` that share a parent, :code:`A'` is placed on top of :code:`B'`
   according to rule 1 and 2.

Observe:

.. figure:: /_static/images/input/input_layers.svg

    A hierarchy of input elements and the value returned by :code:`getInputLayer`. :code:`J` would be visited first.

:code:`F` is placed on top of :code:`A` because of rule 1. :code:`E` is placed on top of :code:`A` because of rule 2.
:code:`K` is placed on top of :code:`B` because of rule 3. The full order in which events are passed to the input
elements is: :code:`J > I > H > G > K > F > E > D > C > B > A`.
