=====
Forms
=====

The Django Form system is one of the core components of Django and exists to
ease the development of HTML forms, both server and client side. The
alternative is a lot of code duplication.

Defining a form
---------------

Forms are subclasses of :class:`django.forms.Form`. You can define a form
by assigning Django `fields` as attributes to the subclass, like so:

.. code-block:: python

    from django import forms

    class MovieForm(forms.Form):
        name = forms.CharField()
        year = forms.CharField()
