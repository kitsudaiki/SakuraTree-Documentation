``ssh``
-------


``cmd``
~~~~~~~

Run a shell command over SSH.

**Example**:

::

    ssh("run an ssh-command")
    -> cmd:
        - user = "ubuntu"
        - address = "127.0.0.1"
        - port = "22"
        - ssh_key = "~/id_rsa"
        - command = "cat /proc/cpuinfo"

**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - user
      - string-value
      - User name for access on the remote system.

    * - address
      - string-value
      - IP address of the remote system.

    * - ssh_key
      - string-value
      - (OPTIONAL) path to the SSH key which should be used (DEFAULT: equals the defaults of the SSH command)

    * - port
      - string-value or int-value
      - (OPTIONAL) port at which the SSH daemon is listening on the remote system (DEFAULT: 22)

    * - command
      - string-value
      - Command which should be executed on the remote system.


**Output**:

    - string-value with the stdout content of the called tool

**Restrictions**

    * stderr content of the called tool is discarded



.. raw:: latex

    \newpage
    
    
``scp``
~~~~~~~

Run a Secure Copy (SCP) command to copy files to another host.


**Example**:

::

    ssh("copy via scp-command")
    -> scp:
        - user = "ubuntu"
        - address = "127.0.0.1"
        - port = "22"
        - ssh_key = "~/id_rsa"
        - source_path = "/tmp/test-file"
        - target_path = "/tmp/"

**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - user
      - string-value
      - User name for access on the remote system.

    * - address
      - string-value
      - IP address of the remote system.

    * - ssh_key
      - string-value
      - (OPTIONAL) path to the SSH key which should be used (DEFAULT: equals the defaults of the SSH command)

    * - port
      - string-value or int-value
      - (OPTIONAL) port at which the SSH daemon is listening on the remote system (DEFAULT: 22)

    * - source_path
      - string-value
      - path to the file or directory on the local system

    * - target_path
      - string-value
      - path to the file or directory on the target system


**Output**:

    no output


.. raw:: latex

    \newpage
    