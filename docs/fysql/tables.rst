.. _tables:

Tables
======

* :ref:`simple-table`
* :ref:`complex-table`

.. _simple-table:

A simple user Table
-------------------

For database check :ref:`database`.

.. code-block:: python
    
    class FyTables(Table):
        db = database 

    class User(FyTables):
        username = CharColumn()

.. _complex-table:

Tables for a blog
-----------------

.. code-block:: python

    class User(FyTables):
        firstname = CharColumn(max_length=50)
        lastname  = CharColumn(max_length=50)
        role      = CharColumn(index=True, unique=True)

    class Post(FyTables):
        title   = CharColumn(default='Post title', max_length=255)
        id_user = FKeyColumn(table=User, reference='user')


Create your tables
-------------------
Two ways to create your tables:

.. code-block:: python

    User.create_table()
    Post.create_table()

    # or

    database.create_all()