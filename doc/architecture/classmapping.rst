=================
  Class Mapping
=================

PyAMF allows you to register aliases for remote Python classes that can be mapped to their corresponding Actionscript classes.

In this example we use the Python classes below.

.. literalinclude:: examples/class-mapping/example-classes.py
   :linenos:

With the corresponding Actionscript 3.0 classes that were
registered in the Flash Player using the `flash.net.registerClassAlias`
utility: 

.. literalinclude:: examples/class-mapping/example-classes.as
   :linenos:


Registering Classes
===================

Classes can be registered and removed using the following tools:

- :func:`pyamf.register_class`
- :func:`pyamf.unregister_class`
- :func:`pyamf.get_class_alias`
- :func:`pyamf.register_package`

Continue reading for examples of these APIs.

Single Class
------------

To register a class alias for a single class::

    >>> pyamf.register_class("org.pyamf.User", User)

Find the alias registered to the class::

    >>> print pyamf.get_class_alias(User)
    org.pyamf.User

And to unregister by alias::

    >>> pyamf.unregister_class("org.pyamf.User")

Or unregister by class::

    >>> pyamf.unregister_class(User)


Multiple Classes
----------------

If you want to register multiple classes at the same time, or all
classes in a module::

    >>> import mymodule
    >>> pyamf.register_package(mymodule, 'org.pyamf')


Class Decorators
================

Python 2.6 introduced_ class decorators_ that help you to avoid writing
most of the boilerplate code that is used when registering classes in
Python. An example:

.. literalinclude:: examples/class-mapping/alias-decorator.py
   :linenos:


.. _introduced: http://docs.python.org/whatsnew/2.6.html#pep-3129-class-decorators
.. _decorators: http://docs.python.org/glossary.html#term-decorator