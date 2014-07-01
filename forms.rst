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

Immutable, bound and unbound
----------------------------

Once a form has been instantiated it should be considered immutable, this is
to ensure integrity. What ever state you instantiate the form instance in is
the state it should stay in.

There are two states to instantiate a form with, *bound* and *unbound*.

    unbound
      Has no data associated with it. Used only for rendering a method of
      data input (HTML form).

      .. code-block:: python

          unbound_form = MovieForm()

    bound
      Has submitted data associated with it. Used for validating input,
      rendering a method of data input (HTML form) and displaying error
      messages if there are validation errors.

      .. code-block:: python

          bound_form = MovieForm({
              'name': 'Locke',
              'year': '2013',
          })

There's no perfect analogy for how Django's forms work (then, there isn't for
anything). An instance of an unbound form could be thought of as a wheelie bin.
You've provided the user with somewhere to put something, along with
instructions on how to pass the contents back to you (leave them out on
Wednesday). And you could think of an instance of a bound form as a box with
an electronic display panel on the side. You can't open the box to change
what's inside, but you can see exactly what is inside and information about it
via the panel.

Validation
----------

Bound forms have the ability to tell you whether or not the data they are
associated with is *valid*. A form is considered valid if the data adheres
to a set of rules defined in the form itself or it's fields.

Unbound forms are always *invalid*.
