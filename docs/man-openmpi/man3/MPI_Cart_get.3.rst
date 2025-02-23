.. _mpi_cart_get:

MPI_Cart_get
============

.. include_body

:ref:`MPI_Cart_get` - Retrieves Cartesian topology information associated with
a communicator.

SYNTAX
------

C Syntax
^^^^^^^^

.. code:: C

   #include <mpi.h>

   int MPI_Cart_get(MPI_Comm comm, int maxdims, int dims[], int periods[],
       int coords[])

Fortran Syntax
^^^^^^^^^^^^^^

.. code:: Fortran

   USE MPI
   ! or the older form: INCLUDE 'mpif.h'

   MPI_CART_GET(COMM, MAXDIMS, DIMS, PERIODS, COORDS, IERROR)
       INTEGER COMM, MAXDIMS, DIMS(*), COORDS(*), IERROR
       LOGICAL PERIODS(*)

Fortran 2008 Syntax
^^^^^^^^^^^^^^^^^^^

.. code:: Fortran

   USE mpi_f08

   MPI_Cart_get(comm, maxdims, dims, periods, coords, ierror)
       TYPE(MPI_Comm), INTENT(IN) :: comm
       INTEGER, INTENT(IN) :: maxdims
       INTEGER, INTENT(OUT) :: dims(maxdims), coords(maxdims)
       LOGICAL, INTENT(OUT) :: periods(maxdims)
       INTEGER, OPTIONAL, INTENT(OUT) :: ierror

INPUT PARAMETERS
----------------

-  comm : Communicator with Cartesian structure (handle).
-  maxdims : Length of vectors dims, periods, and coords in the calling
   program (integer).

OUTPUT PARAMETERS
-----------------

-  dims : Number of processes for each Cartesian dimension (array of
   integers).
-  periods : Periodicity (true/false) for each Cartesian dimension
   (array of logicals).
-  coords : Coordinates of calling process in Cartesian structure (array
   of integers).
-  IERROR : Fortran only: Error status (integer).

DESCRIPTION
-----------

The functions :ref:`MPI_Cartdim_get` and :ref:`MPI_Cart_get` return the Cartesian
topology information that was associated with a communicator by
:ref:`MPI_Cart_create`.

ERRORS
------

.. include:: ./ERRORS.rst

.. seealso:: :ref:`MPI_Cartdim_get`
