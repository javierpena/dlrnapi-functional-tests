dlrnapi-functional-tests
------------------------
This is an Ansible role to run a set of functional tests for the DLRN_ API.

.. _DLRN: https://github.com/softwarefactory-project/DLRN


Role variables
~~~~~~~~~~~~~~

For default values, see `defaults/main.yml`_

* ``working_dir``: work directory. Everything will be installed there.
* ``dlrnapi_auth``: the string used for dlrnapi authentication. The hashed password is included in `tasks/run.yml`_ .
* ``dlrnapi_url``: URL where the DLRN API will listen to.
* ``imported_repo``: URL of a DLRN-generated repository that will be imported as part of the tests.
* ``imported_commit_hash``: commit hash of the commit used in ``imported_repo``.
* ``imported_distro_hash``: distro hash of the commit used in ``imported_repo``.

.. _defaults/main.yml: https://github.com/javierpena/dlrnapi-functional-tests/blob/master/defaults/main.yml
.. _tasks/run.yml: https://github.com/javierpena/dlrnapi-functional-tests/blob/master/tasks/run.yml

Included tasks
~~~~~~~~~~~~~~

* ``prepare``: install all requirements.
* ``run``: run the tests.
* ``post``: gather logs in an artifacts directory (``{{ working_dir }}/artifacts``).

Example playbook
~~~~~~~~~~~~~~~~

.. code-block:: yaml

    - name: Run DLRN CI tests
      hosts: localhost
      roles:
        - role: dlrnapi-functional-tests
