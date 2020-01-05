``text_file``
-------------

``read``
~~~~~~~~

Read the content of a text file and write it into a item.

**Example**:

::

    - test_output = "{{}}"

	text_file("read test-file")
    - file_path = "/tmp/test_template"
    -> read:
       - blossom_output >> test_output


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - file_path
      - string-value
      - Path to the already existing text-file.

**Output**:

    string-value with the content of the text file


``write``
~~~~~~~~~

Create and fill a new text file or replace the whole content of an existing text file.

**Example**:

::

	text_file("write into a text-file")
    - file_path = "/tmp/test_template"
    -> write:
        - text = "test"



**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - file_path
      - string-value
      - Path to the already existing text-file.

    * - text
      - string-value
      - New content of the file.

**Output**:

    no output


``replace``
~~~~~~~~~~~

Replace a substring inside a text file.

**Example**:

::

	text_file("replace in exiting file")
    - file_path = "/tmp/test_template"
    -> replace:
        - old_text = "test"
        - new_text = "asdf"



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

    * - old_text
      - string-value
      - Old text in the file, which should be replace.

    * - new_text
      - string-value
      - New text to replace the old one.

**Output**:

    no output


``append``
~~~~~~~~~~

Add content to a text file.

**Example**:

::

    text_file("append to exiting file")
    - file_path = "/tmp/test_template"
    -> append:
        - text = "test"


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

    * - text
      - string-value
      - Content to append to the existing file.

**Output**:

    no output



.. raw:: latex

    \newpage
    