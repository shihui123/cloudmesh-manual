Installation
============


Cloudmesh is easy to install. Dependent on your preferences you can choose an
install from

* pip if you are a Cloudmesh user
* source install if you are a developer
* an instalation in containers

Please read the installation section in this manual completely, and understand
the items explained before you install. Do not just paste and copy text in
your terminal and execute it as it could have unexpected consequences.
This also helps to decide which instalation method is best suited for you.


Installation of cloudmesh with Docker
-------------------------------------

The easiest way to install cloudmesh is to use docker containers. This
instalation can be conducted on all OSes on which docker and python 3.8.2 is
installed. Cloudmesh can also be installed with a specialized `cloudmesh-cmsd`
command that is distributed as source and on PyPi.

See  :doc:`../cmsd` for more information.

In the next sections we discuss the native install of cludmesh on

* Linux
* Windows
* maxOS

We start with some elementary requirements that are typically already fulfilled
if you are a developer on that platform.

Prerequisites
-------------

.. note::

          Before you install make sure that you have an up to date version of
          python installed. We recommend you use 3.8.2 or newer. Python can be
          downloaded and installed from https://www.python.org/downloads/. On
          Windows you may also need to install the C++ commandline build tools
          as some cryptographic libraries need to be recompiled in 3.8.2. This
          only applies if you like to use cloudmesh-encrypt.

          Likely the code will work with earlier versions starting from 3.7.4.
          We know that Python 3.6 has bugs and should not be used. Although
          cloudmesh previously was supported in Python 2.7 and newer, we have
          removed Python 2 as supported platform.

.. note::

          We recommend that you use  Python `venv` to isolate the system Python
          form the user python. For simplicity we assime and document on how to
          set up a virtual environment in the home directory under the
          directory `ENV3`.



Prerequisites for macOS
^^^^^^^^^^^^^^^^^^^^^^^

Installation of XCode
"""""""""""""""""""""

You want a number of useful tools on your macOS. They are not installed by
default, but are available via Xcode. First you need to install xcode from

* https://apps.apple.com/us/app/xcode/id497799835

Next you need to install macOS xcode command line tools

.. code-block:: bash

   xcode-select --install

Next you want to install a python version. You can either chose the installation
from python.org or from homebrew.

Python Installation from python.org
"""""""""""""""""""""""""""""""""""

The easiest installation of Python for cloudmesh is to use the installation from
https://www.python.org/downloads. Please, visit the page and follow the
instructions. After this install you have `python3` available from the
command line.

.. code-block:: bash

   python3 -m venv ~/ENV3
   source ~/ENV3/bin/activate


Prerequisites for Ubuntu 19.10
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Python 3.8.2 is not yet installed in Ubuntu 19.10. The instalation is simple
and can be conducted with the following steps.

Additionally, Cloudmesh requires OpenSSL and Curl installed in the system.
Please download Python from:

* https://www.python.org/downloads

place the code in a directory and change to that directory. Than say


.. code-block:: bash

   sudo apt -y update
   sudo apt -y install openssl curl
   # sudo apt -y install libreadline-gplv2-dev libncursesw5-dev
   # sudo apt -y libssl-dev
   # sudo apt -y libsqlite3-dev tk-dev
   # sudo apt -y libgdbm-dev libc6-dev libbz2-dev libffi-dev zlib1g-dev
   tar -xvf Python-3.8.2.tgz
   cd Python-3.8.2
   ./configure
   make
   sudo make altinstall
   python3.8 --version
   python3 --version
   # Should be 3.8.2
   python3 -m venv ~/ENV3
   source ~/ENV3/bin/activate


Prerequisites for Ubuntu 18.04
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We first need to make sure that the correct version of the Python3 is
installed. The default version of Python on Ubuntu 18.04 is 3.6. You can get
the new version with

.. code-block:: bash

   sudo apt-get -y update
   sudo apt-get -y install openssl curl
   sudo apt-get install software-properties-common
   sudo add-apt-repository ppa:deadsnakes/ppa
   sudo apt-get install python3.8 python3-dev python3.8-dev
   python3.8 -m venv --without-pip ~/ENV3
   source ~/ENV3/bin/activate
   curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
   python get-pip.py
   rm get-pip.py


Prerequisites for Windows 10
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

On Windows 10 you can install cloudmesh by either using

* a Windows native installation,
* a Linux Subsystem installation,
* a Docker instalation,

approach. We recommend that you use the Professional or the
Educational version of Windows, as the Home edition is very limited.
Alternatively, you can also use the docker version of cloudmesh.
We explain the various methods.


Windows native Installation Approach
""""""""""""""""""""""""""""""""""""

* Ensure that Python 3.8.2 (or higher) has been installed. Python 3.8 can be
  installed on Windows 10 using:

  * https://www.python.org/downloads/

  Make sure
  you download the 64 bit version. Unfortunately, the default version is teh 32
  bit version.
* Create a `venv`. See section on prerequisites for venv provides more details.
* Some Python librarier may need to be compiled. In order for you to complete
  your Python instalation you want to install th *VC C++ command line Build Tools*.
  This is mostly needed for cryptography libraries.
  You can find them at:

  * https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019

  Once you run the installer
  you need to check on the choices as shown in the next image.

  .. figure:: images/VSprintscreen.PNG
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: select the commandline (CLI) build tools


* You will also have to add the following path to the PATH variable::

     C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Tools\MSVC\14.24.28314\bin\Hostx64\x64\

  If you have a newer version, please update the Path accordingly. The next two
  images show screenshots on what you need to change. You will naturally have a
  different username.

  .. figure:: images/EnvironmentVariables.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: add the build tool path to the PATH variable

  .. figure:: images/windowsbuildtoolspath.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: add the build tool path to the PATH variable



Windows Container Approach
""""""""""""""""""""""""""

The user container for cloudmesh shell is called cmsd (cloudmesh shell docker).
It can be installed with pip as follows

.. code-block:: bash

    pip install cloudmesh-cmsd

Please note that in order for you do develop cloudmesh you need to do this
within the container However we do recommend that Windows developer use the
Windows native cloudmesh approach. However regular user will have a very
transparent acces to cloudmesh as most commands ar just passed along to the
container.

The manual page for cmsd is located at :doc:`../cmsd`




Linux Subsystem Installation Approach
"""""""""""""""""""""""""""""""""""""

.. warning:: MongoDB reports that mongo is not yet working on Linux
	         Subsystem. As cloudmesh uses mongo, please do not yet use
	         the Linux Subsystem install.

To activate the Linux Subsystem, please follow the instructions at

* https://docs.microsoft.com/en-us/windows/wsl/install-win10

A suitable distribution would be

* https://www.microsoft.com/en-us/p/ubuntu-1804-lts/9n9tngvndl3q?activetab=pivot:overviewtab

However, as it uses an older version of python, you will be required to update it.

Prerequisites for venv (ENV3)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _Use a venv:

VirtualEnv (or ``venv``) allows the creation of an isolated Python environment.
Using a venv is highly recommended to ensure cloudmesh and cloudmesh-related
installations do not interfere with a system-level installation of python.

.. warning:: Not using a `venv` could have catastrophic consequences and
  result in the destruction of operating system tools which rely on
  Python.

Once `venv` has been created and activated, packages installed with venv will
be installed in this virtual environment and not in the global Python site packages.
This mitigates risks of global package installations.

For our purposes we assume that you use the venv directory::

    ~/ENV3

.. note:: In a Linux subsystem, `~/` is the default location, assumed
   to be the home directory.  In a windows system, this location is
   assumed to be under `C:\Users\USERNAME`.

venv Setup on Linux and macOS
"""""""""""""""""""""""""""""

For the `venv` setup on Linux or macOs, run the following:

.. code-block:: bash

   python3 -m venv  ~/ENV3
   source ~/ENV3/bin/activate

You can add at the end of your `.bashrc` (ubuntu) or `.bash_profile`
(macOS) file the line so the environment is always loaded.

.. code-block:: bash

   source ~/ENV3/bin/activate

venv Setup on Windows
"""""""""""""""""""""

On Windows, you run the following command from your home directory at
`C:\Users\USERNAME`:

.. code-block:: bash

  python -m venv ENV3
  source ENV3\Scripts\activate
  python -m pip install --upgrade pip

Next, create a Windows system variable named `ENV3` and update the
variable value to `C:\Users\USERNAME\ENV3\Scripts\activate`.

.. figure:: images/ENV3variable.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: Setting the ENV3 variable


Then add the `ENV3` variable name to the Path variable.

.. figure:: images/ENV3addedtoPath.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: Add the variable to the path


Lastly, to simplify the `venv` activation call, create a new `ENV3.bat`
file under the default directory, and add the following content to the
file.

.. code-block:: bash

  C:\Users\USERNAME\ENV3\Scripts\activate.bat

.. note:: The same can be done in Windows Powershell by creating a `ENV3.ps1` to
          reference the activation command.

**Test the venv activation**

We recommend  that you test the venv activation. In a command prompt, type
`ENV3` while under the home directory; or if the bat file was not created,
simply reference the system variable %ENV3%.

Example using bat file activation:

.. code-block:: bash

   C:\Users\USERNAME> ENV3

   ...

   (ENV3) C:\Users\USERNAME>


Example using Windows environment variable:

.. code-block:: bash

   C:\Users\USERNAME> %ENV3%

   (ENV3) C:\Users\USERNAME>

In both cases you will see the command prompt starting with `(ENV3)`.

**Validate Python and Pip Version in venv**

Check if you have the right version of python and pip installed with

.. code-block:: bash

   python --version
   pip --version

Now you are ready to install cloudmesh.

Installation of Cloudmesh (End User)
------------------------------------

.. note:: The end user installation steps assume you intend to use
   cloudmesh only as a user.  If you intend to utilize cloudmesh as a
   developer, you must skip ahead to the next section which
   lists the installation steps required for a source install.

The recommended installation approach for cloudmesh is handled through
pip.  Cloudmesh is distributed in different modules, so as an end
user, you only need to install the modules you desire.

Prior to beginning, be sure to activate your venv, e.g.``ENV3``. Then,
depending on your needs, you can install the cloudmesh `cloud` or
`storage` bundle with:

.. code-block:: bash

   pip install cloudmesh-cloud

or

.. code-block:: bash

   pip install cloudmesh-storage # not yet supported

Please note that the storage bundle also includes
`cloudmesh-cloud`. Additional packages include but are not yet
released:

.. code-block:: bash

   pip install cloudmesh-flow    # not yet supported
   pip install cloudmesh-emr     # not yet supported
   pip install cloudmesh-batch   # not yet supported
   pip install cloudmesh-openapi # not yet supported


Once installed, test the cloudmesh command and at the same time create
a configuration file. This is done by invoking the ``cms`` command the first
time. Thus, just type the command


.. code-block:: bash

   cms help

in your terminal. It will create a directory `~/.cloudmesh`
in which you can find the configuration file::

    ~/.cloudmesh/cloudmesh.yaml


Anaconda and Conda
^^^^^^^^^^^^^^^^^^

Cloudmesh can be installed in anaconda with pip. Please follow our pip
instructions, but make sure you create your own virtualenv with conda and assure
you use python 3.8.2 or newer.

Installation of Cloudmesh (Source Install for Developers)
---------------------------------------------------------

If you are a developer, we have develloped a simple ``cloudmesh-installer``
It conveniently downloads the needed repositories, installs them, and
can also be used to updates them. More documentation about the installer can be
found at

*  <https://github.com/cloudmesh/cloudmesh-installer>

First make sure you have a python ``venv`` created, as described in
the prerequisites for venv section (see `Use a venv`_). Activate the
venv (`ENV3`).

Navigate to for example the home directory, Then create an empty
directory labeled ``cm``, and change into the `cm` directory.

.. code-block:: bash

   mkdir cm
   cd cm

Before beginning the installation, be sure to confirm `pip` is up to date
and install the `cloudmesh-installer`.

.. code-block:: bash

   pip install pip -U
   pip install cloudmesh-installer

After `cloudmesh-installer` has been installed  (while still under the `cm`
directory), run the following command to list the available cloudmesh
`bundles`:

.. code-block:: bash

   cloudmesh-installer list

Once you have decided which bundle to install you can proceed. If you only want
to use compute resources the bundle name ``openstack`` will be what you want.
If in addition you also like to work on storage, the bundle name ``storage``
needs to be used.

Let, us assume you chose `opensatck`, than you can install cloudmesh with

.. code-block:: bash

   cloudmesh-installer get openstack

It will take a while for the install to complete. On newer machines it
takes 1 minute, on older machines, it may take significantly
longer. Please watch your system resource information if the install
takes a long time. Make sure to terminate other resource hungry
programs.  After the installation is complete, you can then test if
you have successfully installed it by issuing the following command:

.. code-block:: bash

    cms help

Not only will you see a list of commands, a directory `~/.cloudmesh` with some
of cloudmesh's default configuration files will be installed. You will need to
modify these files at some point.


Cloudmesh Updates
^^^^^^^^^^^^^^^^^

To update the source from GitHub, simply use the `cloudmesh-installer` command
while making sure to specify the desired bundle name, let us assume you use
``cloud``

.. code-block:: bash

    cloudmesh-installer git pull cloud

If you see any conflicts make sure to resolve them.

Please note that in an update it could also be possible that the format of the
`cloudmesh.yaml` file may have changed. Thus we always recommend that you also
update the yaml file to the newest format. You can check the yaml file with

.. code-block:: bash

    cms config check


As developer sometimes it may be best to make a backup of the `cm` and
`~\.cloudmesh` directory or individual repositories in the cm
directory. Then copy your changes into the newest code. Make sure to
remove all python artifacts in the backup directory the command

.. code-block:: bash

    cd cm
    cloudmesh-installer clean --dir=. --force


Reinstallation
^^^^^^^^^^^^^^

In case you need to reinstall cloudmesh and you have used previously the
`cloudmesh-installer`, you can do it as follows (We assume you have used venv
and the `cloudmesh-installer` in the directory cm as documented previously):

.. code-block:: bash

    cd cm # the directory where your source locates
    cloudmesh-installer clean --dir=. --force
    cloudmesh-installer clean --ENV=~/ENV3 --force
    python3 -m venv ~/ENV3
    pip install pip -U
    pip install cloudmesh-installer
    cloudmesh-installer get openstack
    cms help


.cloudmesh directory
--------------------

All cloudmesh related configuration information is stored in the
`.cloudmesh` directory.  In case you want to start fresh, simply
delete that directory and its subdirectories. However, if you need
information from it make sure you make a backup.

Please note that in this file you have sensitive information and it
should never be backed up into GitHub, box, icloud, or other such services.
Keep it on your computer or back it up on an secure encrypted external hard
drive or storage media only you have access to.


Installation of MongoDB
-----------------------

Once you have installed cloudmesh it is easy to install MongoDB with
the build in MongoDB installer.


MongoDB Installation Steps
^^^^^^^^^^^^^^^^^^^^^^^^^^

The following steps document the MongoDB server configuration and
installation steps from the standpoint of a fresh install. We
recommend utilizing our build script for a seamless installation
experience.  However, If you already have a pre-existing installation
of MongoDB, please feel free to skip ahead once you've reviewed the
configuration steps and confirmed you have an admin user with a strong
password created. Please also note that some commands we use during
the development wipe out the database completely including all
collections. So make a backup. 

If you would like to remove an existing MongoDB installation, please
skip to the next subsection in order to reference the uninstall steps
for MongoDB; then revert back to this section to kick off a fresh
install.

You should also note to *not* expose mongo on the internet in order
to keep your information within mongo private.

Prior to starting the MongoDB installation, you will need to install and
configure the ``cloudmesh.yaml`` file if you have not already done so.
To install it, run the following command:

.. code-block:: bash

   cms help

Then, be sure to edit the cloudmesh.yaml configuration file (which is created
under ``~/.cloudmesh`` directory) and update the parameters values used in the
mongo install. You can use a text editor, such as:

.. code-block:: bash

   emacs ~/.cloudmesh/cloudmesh.yaml

and change the password of the mongo entry to something of your choosing.
Note, be sure to use a very strong password credential::

   MONGO_PASSWORD: TBD

In case you do not have mongod installed, you can do so for macOS and Ubuntu
18.xx by setting the following variable::

   MONGO_AUTOINSTALL: True

Alternatively you can set these cloudmesh.yaml parameter values from the
command line  without using an editor by running the following:

.. code-block:: bash

   cms config set cloudmesh.data.mongo.MONGO_AUTOINSTALL=True
   cms config set cloudmesh.data.mongo.MONGO_PASSWORD=YOURPASSWORD

Another item to note is the default location of the MongoDB installation.
In a Linux/MacOS environment, the default installation path will be under
``~/local/mongo/bin``. In a Windows environment, the default path is under
``C:\Users\USERNAME\.cloudmesh\mongo``. If you would like to change these
paths, be sure to update these in the `cloudmesh.yaml` file.

Once configuration of the `cloudmesh.yaml` file has been completed,  run the
following command (assuming you have the user in the c drive), where USERNAME
is the username you installe d cloudmesh in:

.. code-block:: bash

  C:/Users/USERNAME\ENV3\Scripts\activate
  cms admin mongo install

.. note:: In a Windows installation, we are only required to install
          MongoDB commands, *not* MongoDB Service. By default, the
          silent installer will attempt to install and start the
          MongoDB System Service. When prompted that the Service
          failed to start, simply select ``Ignore``.

.. figure:: images/MongoInstall_Windows_Ignore.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: Mongo Windows install. Make sure to press ignore

After the installation completes, in a Linux/MacOS environment, confirm the
MongoDB installation path was added to the ``.bash_*`` file. This should have
already been done automatically if the ``cms admin mongo install`` command
was used to kick off the installation.

In a Windows environment, however, the default path is not automatically added
to the Path variable, so you will need to add this manually:

.. figure:: images/MongoInstall_Windows_Path.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: Mongo Windows path configuration

Now that MongoDB has been installed, we initialize it with the following
command:

.. code-block:: bash

    cms init

In case you like to stop or start is you can say:

.. code-block:: bash

   cms stop
   cms start

Please remember that for cloudmesh to work properly you need to start
mongo. In case you need a different port you can configure that in the yaml
file.

Uninstall of MongoDB on Windows 10
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This section documents  steps required to uninstall MongoDB from a prior instalation

Note that there are two distinct uninstallation steps to consider. If you have
installed MongoDB using the cloudmesh installer
(i.e. ``cms admin mongo install``), Mongo is not installed with a service by
default, and can be simply uninstalled by removing the install directories
under ``~\.cloudmesh`` (reference the MONGO_PATH, MONGO_LOG, and MONGO_HOME
variables within the cloudmesh.yaml file for specifics).

If, however, you have a pre-existing installation of MongoDB, or
have MongoDB Server Service installed through an alternative installation method
outside of cloudmesh, proceed through the following steps if you wish to
completely uninstall MongoDB.


To uninstall, please terminate the running MongoDB service (if
applicable), *then* delete it. To stop the service, open Task Manager
and confirm the status = `Stopped`. If it is not stoppe, please do
so. To delete it, run the following as an administrator from the
command line:

.. code-block:: bash

   sc.exe delete MongoDB

Next, delete the Mongo installation directories. Please reference the
cloudmesh.yaml file for the MONGO_HOME, MONGO_PATH, and MONGO_LOG path values if
``cms admin mongo install`` was attempted at some point.



.. figure:: images/MongoInstall_Windows_InstallPathYAML.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: Mongo install path

Finally, execute the mongodb `msiexe` installer to check if there are
any remaining components that need to be uninstalled. Once launched,
click on the `Remove` button. Note that this installer can be
downloaded locally using the URL found under the MONGO_DOWNLOAD
variable in the cloudmesh.yaml file.


.. figure:: images/MongoInstall_Windows_msiexec.png
     :width: 200px
     :align: center
     :height: 100px
     :alt: alternate text
     :figclass: align-center

     Figure: Mongo installation


.. note:: If Compass was installed, this can simply be removed by
          navigating to the Windows 'Add Remove Programs'.

You have now successfully removed MongoDB, and are ready to reinstall
a fresh instance.


Prerequisites for ssh key
-------------------------

In order for you to use cloudmesh you will need an ssh key. This can be
created from the command line with

.. code-block:: bash

    ssh-keygen

Please make sure to use a passphrase with your key. Anyone telling you to use
a passwordless key is giving you a wrong advice.

Next you want to add a keyname that you use in your clouds to the cloudmesh
yaml file. You can do this by completing the profile or form the command line
with:

.. code-block:: bash

    cms config set cloudmesh.profile.user=YOURUSERNAME
    cms set key user=YOURUSERNAME

The `cms init` includes this automatically.
If ssh is not activated on windows please follwo the Microsoft instructions.

