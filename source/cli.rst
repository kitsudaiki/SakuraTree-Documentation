CLI
===

SakuraTree
----------

The tool can be executed with the following command line call:

::

    SakuraTree [--debug] [-item-input <ITEM_NAME>=<ITEM_CONTENT>] <FILE_OR_DIR_PATH>


**Arguments**:

    * ``--debug`` or ``-d``:

        * **Description**: Enable debug-output.

    * ``--item-input`` or ``-i``:

        * **Description**: Key-value pairs to override the initial values inside of the file. This flag can be used multiple times for each item which should be overwritten.

        * **Restriction**: The value is internally a string-value. Even when you use *-i value=42* the *42* is internally handled as string-value and NOT as an int-value. (update with version 0.3.0)


    * ``<FILE_OR_DIR_PATH>``:

        * **Description**: Path to the initial sakura-file, which should be executed by the tool or to the parent directory, where the `root.sakura`-file is located. Path can be relative or absolute.

**Example**

Create a test file for example as a file named *test-file.sakura* with following content:

::

    ["test example file"]
    - test_output = "test"

    print("test-print")
    - output = test_output


To execute the test file without further options, it's called like this:

::

    SakuraTree /path/to/test-file/test-file.sakura


To execute the test file with *asdf* as initial content for the item *test_output*, it can be called like this:

::

    SakuraTree -i test_output=asdf /path/to/test-file/test-file.sakura
