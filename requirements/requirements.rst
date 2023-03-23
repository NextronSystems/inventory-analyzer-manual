.. index:: Requirements

Requirements
============

Hardware Requirements
---------------------

The Inventory Analyzers hardware requirements [...]]

.. list-table::
   :header-rows: 1
   :widths: 30, 70

   * - Connected Endpoints
     - Minimum  Hardware Requirements
   * - TBA
     - System memory: TBA, Hard disk: TBA, CPU Cores: TBA

NMAP Agent Requirements
-----------------------

Our NMAP Agent is running only on current debian based distributions.

The NMAP Agent needs ``nmap`` installed. You can either do this before
installing the agent, or let ``apt`` resolve the dependency.

.. index:: Network Requirements

Network Requirements
--------------------

The Inventory Analyzer requires the following open firewall ports.

From Management Workstation to Inventory Analyzer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 60, 40

   * - Description
     - Ports
   * - Administrative web interface
     - 8443/tcp
   * - Command line administration
     - 22/tcp

From Inventory Analyzer to NMAP Agent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 50, 50

   * - Description
     - Ports
   * - Task distribution
     - 4545/tcp

From Inventory Analyzer to the Internet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Inventory Analyzer is configured to retrieve updates from the
following remote systems via HTTPS on port 443/tcp:

.. list-table:: 
   :header-rows: 1
   :widths: 50, 50

   * - Product
     - Remote Systems
   * - ASGARD packages
     - update3.nextron-systems.com

.. hint:: 
  All proxy systems should be configured to allow access to these URLs
  without TLS/SSL interception. (We use client-side SSL certificates
  for authentication). It is possible to configure a proxy server, username
  and password during the setup process of the underlying platform. Only
  BASIC authentication is supported (no NTLM authentication support).

.. index:: NTP

Time Synchronization
^^^^^^^^^^^^^^^^^^^^

The application tries to reach the public Debian time servers by default.

.. list-table:: 
   :header-rows: 1
   :widths: 60, 40

   * - Server
     - Port
   * - 0.debian.pool.ntp.org
     - 123/udp
   * - 1.debian.pool.ntp.org
     - 123/udp
   * - 2.debian.pool.ntp.org
     - 123/udp

.. hint:: 
  The NTP server configuration can be changed.

.. index:: DNS

DNS
^^^

The application needs to be able to resolve internal and external IP addresses.

.. warning:: 
  Please make sure that you install your Inventory Analyzer with a
  ``domain name`` (see :ref:`setup/network:Network Configuration`).
  If you do not set the Domain Name and install the Inventory Analyzer,
  you might encounter certain problems with future integrations.

  All components you install should have a proper domain name configured
  to avoid issues further during the configuration.
