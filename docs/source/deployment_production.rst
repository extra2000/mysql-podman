Production Deployment
=====================

Example how to deploy MySQL for production environment.

Clone repositories
------------------

Execute the following command to clone ``mysql-podman`` repository into your ``~/extra2000`` directory:

.. code-block:: bash

    mkdir ~/extra2000
    cd ~/extra2000
    git clone --recursive https://github.com/extra2000/mysql-podman.git

Then, ``cd`` into project root directory:

.. code-block:: bash

    cd mysql-podman

Deploy MySQL
------------

From the project root directory, ``cd`` into ``deployment/production/mysql``:

.. code-block:: bash

    cd deployment/production/mysql

Create config files and fix permission:

.. code-block:: bash

    cp -v configmaps/mysql.yaml{.example,}
    cp -v configs/custom.cnf{.example,}
    chmod og+r ./configs/custom.cnf

Allow config files to be mounted into container:

.. code-block:: bash

    chcon -R -v -t container_file_t configs

Create pod file:

.. code-block:: bash

    cp -v mysql-pod.yaml{.example,}

.. note::

    In the pod file, you may want to append image tag name with ``-aarch64`` if you are using Raspberry Pi. For example, ``docker.io/mysql/mysql-server:8.0-aarch64``

Load SELinux security policy:

.. code-block:: bash

    sudo semodule -i selinux/mysql_podman.cil /usr/share/udica/templates/base_container.cil

Verify that the SELinux module exists:

.. code-block:: bash

    sudo semodule --list | grep -e "mysql_podman"

Deploy mysql:

.. code-block:: bash

    podman play kube --configmap configmaps/mysql.yaml --seccomp-profile-root ./seccomp mysql-pod.yaml

Test mysql. Make sure the following command success:

.. code-block:: bash

    podman run -it --rm --network=host docker.io/mysql:8.0 mysql -uroot -p --host 127.0.0.1 --port 3306

Create systemd files to run at startup:

.. code-block:: bash

    mkdir -pv ~/.config/systemd/user
    cd ~/.config/systemd/user
    podman generate systemd --files --name mysql-pod
    systemctl --user enable pod-mysql-pod.service container-mysql-pod-srv01.service
