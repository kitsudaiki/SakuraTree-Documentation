``apt``
-------

Provides interactions with ``apt-get`` for Debian-based systems.

**DEPRECATED: this type is marked as deprecated and will be reworked with version 0.3.0**

``update``
~~~~~~~~~~

**DEPRECATED: this type is marked as deprecated and will be reworked with version 0.3.0**

Run an ``apt-get udpate``

**Example**:

::

    apt("update")  
    -> update


**Input**:

    no input-values

**Output**:

    no output


``upgrade``
~~~~~~~~~~~

**DEPRECATED: this type is marked as deprecated and will be reworked with version 0.3.0**

Run an ``apt-get -y upgrade``

**Example**:

::

    apt("upgrade")  
    -> upgrade
    

**Input**:

    no input values

**Output**:

    no output


``present``
~~~~~~~~~~~

**DEPRECATED: this type is marked as deprecated and will be reworked with version 0.3.0**

Check if a list of apt-packages is installed and install all packages with ``apt-get install -y ..``, which do not exist. All existing packages are skipped.

**Example**:

::

    - new_packages = [ "nano", "vim" ]

    apt("check and install if necessary")  
    -> update
    -> present:
      - packages = new_packages


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - packages
      - array-item with string-values
      - all packages, which should be installed, if they do not exist on the system

**Output**:

    no output


``latest``
~~~~~~~~~~

**DEPRECATED: this type is marked as deprecated and will be reworked with version 0.3.0**

Install if not exist or update if exist a list of apt-packages with ``apt-get install -y ..``.

**Example**:

::

    - new_packages = [ "nano", "vim" ]

    apt("install and update")  
    -> latest:
      - packages = new_packages


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - packages
      - array-item with string-values
      - all packages, which should be installed and up-to-date

**Output**:

    no output


``absent``
~~~~~~~~~~

**DEPRECATED: this type is marked as deprecated and will be reworked with version 0.3.0**

Remove all apt-packages of a given list, which still exist on the system with ``apt-get remove -y ..``.

**Example**:

::

    - new_packages = [ "nano", "vim" ]

    apt("remove")  
    -> absent:
      - packages = new_packages


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - packages
      - array-item with string-values
      - all packages, which should be removed

**Output**:

    no output

.. raw:: latex

    \newpage
    