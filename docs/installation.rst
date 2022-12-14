.. highlight:: shell

============
Installation
============

 There are two installation types, a productive (binary) installation and a development (source) installation which is editable.

Preparation
-----------
To install my first blueprint test you need a miniconda installation. You can either setup your miniconda installation manually or use the script `setup_miniconda.sh`, which will download and install the latest version of miniconda.


Installation of dependencies
----------------------------
Dependencies are handled by the conda package manager. The goal of this step is to set up a conda environment according to the requirements of my first blueprint test. Note that the development installation has some additional dependencies as it includes linters and other development tools. The dependencies are handled in requirement files. Free installations are based on the `requirements/requirements.yml` and `requirements/dev-requirements.yml` files, where the first-level dependencies of the package are listed. Pinned installations are based on exported environments and stored in the files `requirements/environment.yml` and `requirements/dev-environment.yml`. In total, four possible installation options are possible pinned/unpinned x dev/prod. These options are covered in the script `setup_env.sh`. The optional flags `-d` and `-p` stand for dev and pinned installation respectively. E.g. for a dev installation type:

.. code-block:: console

    $ bash setup_env.sh -d

You can control the environment name with the flag `-n` and the python version with `-v`. As defaults the script will use my-first-blueprint-test and Python 3.10.


Installation of my first blueprint test
-----------------------------------------------

Again, there are two options for installation, binary production installations and development (source) installations which are editable. Go to the root folder of my-first-blueprint-test. Then type

.. code-block:: console

    $ conda activate my-first-blueprint-test
    $ pip install .

For a production installation and

.. code-block:: console

    $ conda activate my-first-blueprint-test
    $ pip install . --editable

for a development installation.


Maintenance of the environment (for developers)
-----------------------------------------------

If you need to add new first-level dependencies to your package, make sure to include them in `requirements/requirements.yml` or `requirements/dev-requirements.yml` in case they are used for development only. Note that pip requirements can be added to these files in the `pip:` section of the document. After a (free!) installation, this will change the full dependency tree and you need to export the environment(s). This is currently not handled automatically, so you need to export both (dev and prod) environments by hand by activating the environment and then running

.. code-block:: console

    $ conda env export my-first-blueprint-test requirements/environment.yml

or

.. code-block:: console

    $ conda env export dev-my-first-blueprint-test requirements/dev-environment.yml

Note that this requires you to distinguish the name of the dev environment.


Interaction with Jenkins
------------------------

All four possible installation options (prod/dev) x (free/pinned) are tested by jenkins on regular builds and upon merging pull requests to the master branch.
