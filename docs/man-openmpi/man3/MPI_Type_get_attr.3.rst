.. _mpi_type_get_attr:


MPI_Type_get_attr
=================

.. include_body

:ref:`MPI_Type_get_attr` - Returns the attribute associated with a data
type.


SYNTAX
------


C Syntax
^^^^^^^^

.. code-block:: c

   #include <mpi.h>

   int MPI_Type_get_attr(MPI_Datatype type, int type_keyval, void *attribute_val, int *flag)


Fortran Syntax (see FORTRAN 77 NOTES)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: fortran

   USE MPI
   ! or the older form: INCLUDE 'mpif.h'
   MPI_TYPE_GET_ATTR(TYPE, TYPE_KEYVAL, ATTRIBUTE_VAL, FLAG, IERROR)
   	INTEGER	TYPE, TYPE_KEYVAL, IERROR
   	INTEGER(KIND=MPI_ADDRESS_KIND) ATTRIBUTE_VAL
   	LOGICAL FLAG


Fortran 2008 Syntax
^^^^^^^^^^^^^^^^^^^

.. code-block:: fortran

   USE mpi_f08
   MPI_Type_get_attr(datatype, type_keyval, attribute_val, flag, ierror)
   	TYPE(MPI_Datatype), INTENT(IN) :: datatype
   	INTEGER, INTENT(IN) :: type_keyval
   	INTEGER(KIND=MPI_ADDRESS_KIND), INTENT(OUT) :: attribute_val
   	LOGICAL, INTENT(OUT) :: flag
   	INTEGER, OPTIONAL, INTENT(OUT) :: ierror


INPUT PARAMETERS
----------------
* ``type``: Data type to which the attribute is attached (handle).
* ``type_keyval``: Key value (integer).

OUTPUT PARAMETERS
-----------------
* ``attribute_val``: Attribute value, unless *flag* = false
* ``flag``: "false" if no attribute is associated with the key (logical).
* ``IERROR``: Fortran only: Error status (integer).

DESCRIPTION
-----------

For the given data type, :ref:`MPI_Type_get_attr` returns an attribute value
that corresponds to the specified key value.


FORTRAN 77 NOTES
----------------

The MPI standard prescribes portable Fortran syntax for the
*ATTRIBUTE_VAL* argument only for Fortran 90. Sun FORTRAN 77 users may
use the non-portable syntax

::

        INTEGER*MPI_ADDRESS_KIND ATTRIBUTE_VAL

where MPI_ADDRESS_KIND is a constant defined in mpif.h and gives the
length of the declared integer in bytes.


ERRORS
------

.. include:: ./ERRORS.rst

.. seealso::
   :ref:`MPI_Type_set_attr`
