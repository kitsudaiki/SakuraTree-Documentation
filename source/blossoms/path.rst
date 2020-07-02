``path``
--------

This type provides functionality to interact with files and directory on the local disk. Handling the difference between files and directories correctly is difficult, that's why it was merged under the generic name ``path``.


``copy``
~~~~~~~~

Copy a file or directory from one location on the disk to another one or copy a file or directory from the local "files" directory to any location on the disk.

**Example**:

::

    path("copy a testfile")
    -> copy:
       - source_path = "test_file"
       - dest_path = "/tmp/test_file"
       - owner = "deployer"
       - mode = 644


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - source_path
      - string-value
      - Path to the source file or source directory. Either an absolute path starting with "/" or a relative path inside the "files" directory beside the sakura-file.

    * - dest_path
      - string-value
      - Absolute path to the destination of the file.

    * - owner
	  - string-value or int-value
	  - User name or user id to set for the destination file.

    * - mode
      - int-value
      - Mode to set for the destination file.

**Output**:

    no output


``delete``
~~~~~~~~~~

Delete a file or directory from the disk.

**Example**:

::

    path("delete testfile")
    -> delete:
       - path = "/tmp/test_file"


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - path
      - string-value
      - Absolute path of the file or directory which should be renamed

**Output**:

    no output


``rename``
~~~~~~~~~~

Rename a file or directory on the disk.

**Example**:

::

    path("rename testfile")
    -> rename:
       - path = "/tmp/test_file"
       - new_name = "/tmp/new_test_fil"


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - path
      - string-value
      - Absolut path of the file or directory, which should be renamed

    * - new_name
      - string-value
      - New name (not a path) of the file or directory with the same parent directory.

**Output**:

    no output


``chmod``
~~~~~~~~~

Rename a file or directory from the disk.

**Example**:

::

    path("change file-permission")
    -> chmod:
       - path = "/tmp/test_file"
       - permission = 644


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - path
      - string-value
      - Absolute path of the file or directory which should be changed

    * - permission
      - string-value or int-value
      - New permission of the target

**Output**:

    no output


``chown``
~~~~~~~~~

Change the owner of a file or directory with ``chown``.

**Example**:

::

    path("change file-owner")
    -> chown:
       - path = "/tmp/test_file"
       - owner = "ubuntu"


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - path
      - string-value
      - Absolute path of the file or directory which should be changed

    * - owner
      - string-value
      - Name of the new owner or the target

**Output**:

    no output

.. raw:: latex

    \newpage
    