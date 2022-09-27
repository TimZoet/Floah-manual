Input Context
=============

The :code:`floah::InputContext` class holds a collection of hierarchical :code:`floah::InputElement` objects. Typically,
a context will correspond directly to a window, and the input elements to panels and widgets inside of it.

Input Elements
--------------

To have objects receive input events, you must add them to a context. This is fairly straightforward, just pass them
to the context's :code:`addElement` method. Since the context does not take ownership, be sure to call
:code:`removeElement` before they are destroyed.

Polling
-------

This module has no awareness of any input libraries. You are responsible for doing polling using your chosen library,
and passing on any relevant events and information to the input context. In case you are using the :code:`GLFW` library,
which is used in all examples that come with :code:`Floah`, this might look more or less like the following:

.. code-block:: cpp

    // Callback for GLFW mouse button event.
    void mouseButtonCallback(GLFWwindow* window, const int button, const int action, int mods)
    {
        floah::InputContext& context = *static_cast<floah::InputContext*>(glfwGetWindowUserPointer(window));
        
        // Pass event on to context.
        context.setMouseButton(...);
        ...
    }

    // Assuming a previously created window and context.
    GLFWwindow*           window = ...;
    floah::InputContext* context = ...;

    // Setup GLFW callbacks.
    glfwSetWindowUserPointer(window, inputContext);
    glfwSetMouseButtonCallback(window, mouseButtonCallback);

    while (true)
    {
        // Do pre poll, to e.g. clear previous mouse button.
        inputContext->prePoll();

        // Invoke GLFW, which will reroute events to the context.
        glfwPollEvents();

        // Have the context pass all events to the input elements.
        inputContext->postPoll();
    }
