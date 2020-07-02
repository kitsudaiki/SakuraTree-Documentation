``template``
------------

The template group provides the functionality to generate text files based on a Jinja2 template, which has to exist in the "templates" directory beside the sakura-file. This blossom-group is special as it contains only one blossom-type. The reason for this is primary the possebility of the visual separation of values.


``create_file``
~~~~~~~~~~~~~~~

Generate a text file from a Jinja2 template. For the conversion the library *libKitsunemimiJinja2* is used. It provides basic Jinja2 functions like replacements and simple if-conditions and for-loops.

**Example**:

::

    template("create a template")
    -> create_file:
        - source_path = "test_template.j2"
        - dest_path = "/tmp/test-file"
        - owner = "ubuntu"
        - permission = 644
        - variables = { 
                        - checker = 42
                        - name = "test-template" 
                      }


Template-input:

::

    this is
    {% if checker is 42 %}
    a
    {{ name }}
    {% endif %}


Result:

::

    this is
    
    a
    test-template



**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - source_path
      - string-value
      - Path to the already existing INI file.

    * - dest_path
      - string-value
      - group to insert the new value into. If the group doesn't exist, it will be created.

    * - owner
      - string-value
      - owner of the new created file

    * - permission
      - int-value
      - permission for the new created file

    * - variables
      - item map
      - item which should be inserted into the template.


**Output**:

    no output



``create_string``
~~~~~~~~~~~~~~~~~

Generate a string from a Jinja2 template. For the conversion the library *libKitsunemimiJinja2* is used. It provides basic Jinja2 functions like replacements and simple if-conditions and for-loops. The converted string can be stored into a variable to be used by another blossom. This is usedful, for example when the content of the template should be only append to an existing file and should not replace the file. 

**Example**:

::

    - converted_output = ""

    template("create a template")
    -> create_file:
        - source_path = "test_template.j2"
        - variables = { 
                        - checker = 42
                        - name = "test-template" 
                      }
        - blossom_output >> converted_output


Template-input:

::

    this is
    {% if checker is 42 %}
    a
    {{ name }}
    {% endif %}


Result:

::

    this is
    
    a
    test-template



**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - source_path
      - string-value
      - Path to the already existing INI file.

    * - variables
      - item map
      - item which should be inserted into the template.


**Output**:

    string-value with the converted and filled content of the template file


.. raw:: latex

    \newpage
    

Template Structure
^^^^^^^^^^^^^^^^^^

The following constructs are allowed inside Jinja2 template:

**replacements**

Syntax:

::

    {{ <JSON_PATH> }}

Example:

:: 

    this is a {{ item.sub_item }}
    

**if-conditions**

Syntax:

::

    {% if <JSON_PATH> is <COMPARE_VALUE> %} ... {% else %} ... {% endif %}

Example:

:: 

	this is 
	{% if item2.sub_item2 is 42 %}
	 a 
	{% else %}
	 no 
	{% endif %} test-string");


**for-loops**

Syntax:

::

    {% for <TEMP_VAR> in <JSON_PATH> %} ... {{ <TEMP_VAR>.<JSON_PATH> }} ... {% endfor %}

Example:

::

    this is
    {% for single_value in loop_item %}
     a 
    {{ single_value.x }}
    {% endfor %}


.. raw:: latex

    \newpage
    
