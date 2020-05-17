``print``
---------

Print one or more data-items as a table.

**Example**:

::

    - packages = [ "nano", "vim" ]
    - test_output = "test"
    - test_file = "/proc/cpuinfo"

    print("test-output")
    - packages = packages
    - some_output = test_output
    - command = "cat {{test_file}}"


Output:

::

    +-------------+-------------------+
    | Item-Name   | Value             |
    +=============+===================+
    | command     | cat /proc/cpuinfo |
    +-------------+-------------------+
    | packages    | ["nano","vim"]    |
    +-------------+-------------------+
    | some_output | test              |
    +-------------+-------------------+


**Input**:

.. tabularcolumns:: |m{0.4\textwidth}|m{0.15\textwidth}|m{0.38\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - (any name, which should be shown in the output)
      - any data type
      - Item which should be printed on the terminal. Even array- and map-items can be printed.

**Output**:

    no output


``item_update``
---------------

Update already existing items within the current file. Within the blossom you can assign an item a totally different value or other item or you can change items by calling functions and assign the result of the function.

**Example**:

::

    - test_output = "test"
    - test_map = { "test": ["poi1", "poi2"]}
    
    item_update("test-update")
    - test_map = test_map.insert("asdf2", test_map)
    - test_output = "test2"
    
    print("test-output")
    - test_output = test_output
    - size = test_map.size()
    - content = test_map.get("asdf2")


**Input**:

.. tabularcolumns:: |m{0.4\textwidth}|m{0.15\textwidth}|m{0.38\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - (any item-name, of the items which should be changed or overwritten)
      - any data type
      - value, item or item with function-call, which should be assigned as new item-content

**Output**:

    no output


``assert``
----------

Assert for one or more data-items to have a specific content.

**Example**:

::

    - test_item = "test"
    - another_item = ["test"]

    assert("test-assert")
    - test_item == "test"
    - test_item == another_item.get(0)


**Input**:

* left side: name of the item, which should be checked

* right side: value or data-item to compare with
     

**Output**:

    no output

**Restrictions**

    * On the left side, only a single item name is allowed. Calling a function on the left side would result in a parser error.

    * At the moment only "==" is supported.



``cmd``
-------

Run a custom shell command.

**Example**:

::

    - test_file = "/proc/cpuinfo"

    cmd("test-command")
    - command = "cat {{test_file}}"
    - ignore_errors = true


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - command
      - string-value
      - Command, which should be executed

    * - ignore_errors 
      - bool-value
      - (Optional) Can be set to *true* to ignore the exit value of the called command. (Default: false)
     

**Output**:

    - string-value with the stdout/stderr content of the called tool
    

``exit``
--------

Kill the current run and close the tool with a specific exit code.

**Example**:

::

    exit("kill run")
    - status = 42

**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - status
      - int-value
      - exit status code of the tool
     

**Output**:

    no output

.. raw:: latex

    \newpage
