.. index:: Install Inventory Analyzer

Install the Inventory Analyzer Service
======================================

Use SSH to connect to the appliance using the user ``nextron`` and the password you
specified during the installation. Now you can run the following command: 

.. code-block:: console

   nextron@inventory:~$ sudo nextronInstaller -inventory
   
This will install the Inventory Analyzer

CHANGE PICTURE HERE

.. figure:: ../images/setup_nextronInstaller.png
   :alt: running the nextronInstaller

After installation is complete type ``sudo systemctl status asgard2``. 

The output should look something like this (note the status
``Active: active (running)``:

.. code-block:: console

   nextron@inventory:~$ sudo systemctl status asgard-inventory.service 
   [sudo] password for nextron: 
   ● asgard-inventory.service - ASGARD Inventory
        Loaded: loaded (/lib/systemd/system/asgard-inventory.service; enabled; vendor preset: enabled)
        Active: active (running) since Fri 2023-03-03 21:26:40 CET; 45s ago
       Process: 701 ExecStartPre=/etc/asgard-inventory/pre_run_asgard_inventory.sh (code=exited, status=0/SUCCESS)
      Main PID: 718 (bash)
         Tasks: 9 (limit: 4633)
        Memory: 22.3M
           CPU: 140ms
        CGroup: /system.slice/asgard-inventory.service
                ├─718 /bin/bash /etc/asgard-inventory/run_asgard_inventory.sh
                └─719 asgard-inventory

   Mar 03 21:26:40 inventory systemd[1]: Starting ASGARD Inventory...
   Mar 03 21:26:40 inventory systemd[1]: Started ASGARD Inventory.

The installation is now completed, you are ready to log into the web-based GUI via:

:samp:`https://<your-FQDN>:8443`

.. index:: Changing IP-Address

Changing the IP-Address
=======================

Your servers IP-Address can be changed in ``/etc/network/interfaces``. The IP is
configured with the address variable.

.. code-block:: console

   nextron@inventory:~$ sudoedit /etc/network/interfaces

.. code-block:: none

   allow-hotplug ens32
   iface ens32 inet static
   address 192.0.2.7
   netmask 255.255.255.0
   gateway 192.0.2.254

The new IP can be applied with the command ``sudo systemctl restart networking``.

.. warning:: 
   It might be the case where the name of the network adaptor (in this example: ``ens32``)
   is different. Please consider this when changing the values and leave the interface name
   how it is currently set in the configuration.

.. index:: Verify DNS Settings

Verifying DNS Settings
----------------------

To verify if your Inventory Analyzer is using the correct DNS Server, you
can inspect the file ``/etc/resolv.conf`` and look for the ``nameserver`` parameter.
Multiple parameters could be set here.

.. code-block:: console

   nextron@inventory:~$ cat /etc/resolv.conf 
   search example.org
   nameserver 172.16.200.2

If you see errors in this configuration, you can change it with the following command:

.. code-block:: console

   nextron@inventory:~$ sudoedit /etc/resolv.conf
