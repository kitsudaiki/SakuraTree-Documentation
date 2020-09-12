``ini_file``
------------

Provides functions to edit existing INI files.

``set``
~~~~~~~

Check if a list of apt-packages is installed and install all packages with ``apt-get install -y ..``, which do not exist. All existing packages are skipped.

**Example**:

::

    ini_file("get value from a test-ini-file")
    - file_path = "/tmp/test_file"
    - group = "DEFAULT"
    -> set:
        - entry = "asdf"
        - value = "123456789"


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - file_path
      - string-value
      - Path to the already existing INI file.

    * - group
      - string-value
      - group to insert the new value. If the group doesn't exist, it will be created.

    * - entry
      - string-value
      - entry within the group, where the new value should be set. If the entry doesn't exist, it will be created.

    * - value
      - value-item
      - value to write into the defined position in the INI file

**Output**:

    no output



``get``
~~~~~~~

Read a specific value from an INI file.

**Example**:

::

	- test_output = "{{}}"

    ini_file("get value from a test-ini-file")
    - file_path = "/tmp/test_file"
    - group = "DEFAULT"
    -> get:
        - entry = "asdf"
        - value >> test_output


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - file_path
      - string-value
      - Path to the already existing INI file.

    * - group
      - string-value
      - Group with the requested value.

    * - entry
      - string-value
      - Entry to identify the value.

**Output**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - value
      - data-item
      - Value of the given group- and entry-name. Type of the value depends on the type of the value inside the INI file, so it can be any value-item or an array-item.


``delete``
~~~~~~~~~~

Delete an entry or a complete group from an existing INI file.

**Example**:

::

    ini_file("get value from a test-ini-file")
    - file_path = "/tmp/test_file"
    - group = "DEFAULT"
    -> delete:
        - entry = "asdf"


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - file_path
      - string-value
      - Path to the already existing INI file.

    * - group
      - string-value
      - Name of the group with the entry to delete or group which should be deleted completely, if no ``entry`` was set.

    * - entry
      - string-value
      - (Optional) Entry which should be deleted from the file. If ``entry`` is not set, the whole group will be deleted.

**Output**:

    no output

.. raw:: latex

    \newpage
    