.. _dependencies:
Software and data required for the course
=========================================

.. important::
   * **The course instructions assume you are using a Linux environment**

   * If you’re using a Mac or Windows computer, you might find it easier to set up a Linux Virtual Machine using software like `Virtual Box <https://www.virtualbox.org/>`_. (Instructions below.)

   * However, all of the software used should also be installable on Mac or Windows computers.


Assumed file system structure
-----------------------------

All of the practical sessions are written to refer to various pieces of data in a root directory called ``/course``.
If you're using a Virtual Machine, you can just make this directory (``sudo mkdir /course``) and put the various pieces of data there.
If you're using your own computer, and put the data elsewhere like somewhere in your home folder, you’ll need to modify the course instructions appropriately.


Setting up a Linux virtual machine for the course
-------------------------------------------------

- Follow the `Ubuntu instructions for creating an Ubuntu VM <https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview>`_.
- You’ll need to allocate at least 8GB of memory to the VM to run every step of the course.


Installing software for the course
----------------------------------

Docker
~~~~~~
Docker allows you to run "containers": reproducible builds of certain tools. `Install Docker Desktop <https://www.docker.com/>`_ (or alternatives like Podman).

Anaconda
~~~~~~~~
Conda allows you to create "environments": sets of tools and libraries that depend on each other. `Install Anaconda distribution <https://www.anaconda.com/products/distribution>`_.

Sirius
~~~~~~
Sirius is a tool for analysting metabolite data. `Install Sirius 4 <https://bio.informatik.uni-jena.de/software/sirius/>`_.

MZmine
~~~~~~
MZmine is a tool for processing mass-spectrometery data. `Install MZmine 3 <http://mzmine.github.io/>`_.

Gemma
~~~~~
Gemma is a tool for working with genome-wide association studies. `Install Gemma 0.98.3 <https://github.com/genetics-statistics/GEMMA/releases>`_.

Bedtools
~~~~~~~~
Bedtools is a set of tools for genomic analysis. `Install Bedtools 2.30.0 <https://github.com/arq5x/bedtools2/releases>`_.

Dependencies
~~~~~~~~~~~~
``cd /course`` (assuming you are using a Virtual Machine, see notes above)

This fetches the course notes, some code notebooks, and various dependencies and datasets:
``git clone https://github.com/ebi-metagenomics/holofood-course.git docs``

This creates Conda environments with the dependencies required for the practical sessions:
``cd docs/sessions/Metabolomics/``

``conda create -f Metabolomics.yml``

``cd docs/sessions/metagenomics/notebooks/``

``conda create --name jupyter -c conda-forge jupyterlab``

``conda acivate jupyter``

``pip install -r requirements.txt``

``conda create --name r --channel conda-forge "r-base>=4.0.3" r-devtools``

``conda activate r``

``conda install -c conda-forge r-reshape2 r-ggplot2``


Copying data for the course
---------------------------

For the MAG generation practical
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Download all of the data from `this EBI-hosted FTP site <http://ftp.ebi.ac.uk/pub/databases/metagenomics/mgnify_courses/holofood_2022/>`_.

Unzip any of the ``.tar.gz`` files, using e.g. ``tar -xzf eukaryotes.tar.gz``.


For the multi-kingdom metagenomics practical
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    wget http://ftp.ebi.ac.uk/pub/databases/metagenomics/mgnify_courses/biata_2021/virify_tutorial.tar.gz
    or
    rsync -av --partial --progress rsync://ftp.ebi.ac.uk/pub/databases/metagenomics/mgnify_courses/biata_2021/virify_tutorial.tar.gz .

Once downloaded, extract the files from the tarball:

.. code-block:: bash

    tar -xzvf virify_tutorial.tar.gz
    
Now change into the **virify_tutorial** directory and setup the environment by running the following commands in your current terminal session:

.. code-block:: bash

    cd virify_tutorial
    docker load --input docker/virify.tar
    docker run --rm -it -v $(pwd)/data:/opt/data virify
    mkdir obs_results

