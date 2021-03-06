Getting Started
===============

IOData can be used to read and write different quantum chemistry file formats.

Script usage
------------

The simplest way to use IOData, without writing any code is to use the ``horton-convert`` script.

.. code-block:: bash

    horton-convert.py in.xyz out.molden

See the :code:`--help` option for more details on usage.

Code usage
----------

More complex use cases can be coded. IOData stores an object containing the data read from the
file.

Reading
^^^^^^^

To read a file, use something like this:

.. code-block:: python

    from iodata import IOData

    mol = IOData.from_file('water.xyz')  # Stored in Angstrom
    print(mol.coordinates)  # prints out in Bohr

The file format is inferred from the extension. **Note that IOData will automatically convert units
from the file format's official specification to atomic units (which is the format used throughout
HORTON3)**

Writing
^^^^^^^

IOData can also be used to write different file formats:

.. code-block:: python

    from iodata import IOData

    mol = IOData.from_file('water.xyz')
    mol.to_file('water.molden')

Data storage
^^^^^^^^^^^^

IOData can be used to store data in a consistent format for writing at a future point.

.. code-block:: python

    import numpy as np
    from iodata import IOData

    mol = IOData(title="water")
    mol.numbers = np.array([8, 1, 1])
    mol.coordinates = np.array([[0, 0, 0,], [0, 1, 0,], [0, -1, 0,]])  # in Bohr