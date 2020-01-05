CLI
===

SakuraTree
----------

The tool can be executed with the following command line call:

::

    SakuraTree --seed-path <FILE_PATH> [--i <ITEM_NAME>=<ITEM_CONTENT>] [--i <ITEM_NAME>=<ITEM_CONTENT>] ...


**Arguments**:

    * ``--seed-path``:

        * **Description**: Path to the initial tree-file, which should be executed by the tool. 

        * **Restriction**: It has to be an absolute path. (update expected with version 0.3.0)


    * ``--input`` or ``-i``:

        * **Description**: Key-value pairs to override the initial values inside of the file. This flag can be used multiple times for each item which should be overwritten.

        * **Restriction**: The value is internally a string-value. Even when you use *-i value=42* the *42* is internally handled as string-value and NOT as an int-value. (update with version 0.3.0)


**Example**

Create a test file for example as a file named *test-file.tree* with following content:

::

    ["test example file"]
    - test_output = "test"

    print("test-print")
    - output = test_output


To execute the test file without further options, it's called like this:

::

    SakuraTree --seed-path /path/to/test-file/test-file.tree


To execute the test file with *asdf* as initial content for the item *test_output*, it can be called like this:

::

    SakuraTree --seed-path /path/to/test-file/test-file.tree -i test_output=asdf

