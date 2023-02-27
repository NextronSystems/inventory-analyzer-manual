Requirements
============

Hardware Requirements
---------------------

ASGARDs hardware requirements depend on the number of connected
endpoints and also on the intended use. For example, you should
consider using bigger hard disks if you are planning to use Bifrost
or ASGARD's evidence collection feature extensively.

.. list-table::
   :header-rows: 1
   :widths: 30, 70

   * - Connected Endpoints
     - Minimum  Hardware Requirements
   * - up to 500 [1]_
     - System memory: 4 GB, Hard disk: 500 GB, CPU Cores: 2
   * - up to 10,000 [1]_
     - System memory: 8 GB, Hard disk: 1TB, CPU Cores: 4
   * - up to 25,000 [1]_
     - System memory: 16 GB, Hard disk: 1TB SSD (min 100 MB/s), CPU Cores: 4

.. [1]
  THOR and AURORA count as individual endpoints in this calculation.
  AURORA is more demanding than THOR. This results in a maximum of 200/4000/10000
  endpoints if THOR **and** AURORA are installed on each endpoint.

Agent Requirements
------------------

The ASGARD Agent, which is installed on endpoints, uses up to 10MB of RAM.
THOR uses up to 300 MB of RAM additionally when scanning is in progress. 

The agent will use up to 50 MB of hard disk. Together with THOR and its
temporary files it uses a maximum of 200 MB in total. 

Please note, that some response actions, such as collecting triage packs
or collecting system RAM, require additional disk space.

There are no requirements pertaining to the CPU as scans can be scheduled
in a way that THOR reduces its own process priority and limits its CPU
usage to a configurable percentage.

Supported operating systems are the ones
`supported by THOR <https://thor-manual.nextron-systems.com/en/latest/usage/requirements.html#supported>`__.
Not supported are the operating systems with limited or special THOR support.

Network Requirements
--------------------

The ASGARD system requires the following open ports (incoming).

From ASGARD Agent to ASGARD Server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 60, 40

   * - Description
     - Ports
   * - Agent / Server communication
     - 443/tcp
   * - Syslog Forwarder (optional)
     - 514/tcp, 514/udp

From Management Workstation to ASGARD Server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 60, 40

   * - Description
     - Ports
   * - Administrative web interface
     - 8443/tcp
   * - Command line administration
     - 22/tcp

From ASGARD to SIEM
^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 50, 50

   * - Description
     - Ports
   * - Syslog forwarder
     - 514/tcp, 514/udp

From ASGARD to Analysis Cockpit
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 70, 30

   * - Description
     - Ports
   * - Asset Synchronization, Log- and Sample forwarding
     - 7443/tcp
   * - Syslog forwarder (optional)
     - 514/tcp, 514/udp

From ASGARD and MASTER ASGARD to the Internet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ASGARD systems are configured to retrieve updates from the
following remote systems via HTTPS on port 443/tcp:

.. list-table:: 
   :header-rows: 1
   :widths: 50, 50

   * - Product
     - Remote Systems
   * - ASGARD packages
     - update3.nextron-systems.com
   * - THOR updates
     - update1.nextron-systems.com
   * - THOR updates
     - update2.nextron-systems.com

All proxy systems should be configured to allow access to these URLs
without TLS/SSL interception. (ASGARD uses client-side SSL certificates
for authentication). It is possible to configure a proxy server, username
and password during the setup process of the ASGARD platform. Only
BASIC authentication is supported (no NTLM authentication support).

From MASTER ASGARD to ASGARD
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 70, 30

   * - Direction
     - Port
   * - From MASTER ASGARD v2 to ASGARD v2
     - 5443/tcp
   * - From MASTER ASGARD v2 to ASGARD v1
     - 9443/tcp

You cannot manage ASGARD v2 systems from a MASTER ASGARD v1.

From Management Workstation to MASTER ASGARD
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: 
   :header-rows: 1
   :widths: 70,30

   * - Description
     - Port
   * - Administrative web interface
     - 8443/tcp
   * - Command line administration
     - 22/tcp

Time Synchronization
^^^^^^^^^^^^^^^^^^^^

ASGARD tries to reach the public Debian time servers by default.

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

The NTP server configuration can be changed.

DNS
^^^

ASGARD needs to be able to resolve internal and external IP addresses.

.. warning:: 
  Please make sure that you install your ASGARD with a ``domain name``
  (see :ref:`setup/network:Network Configuration`). If you do not set the
  Domain Name and install the ASGARD package, your clients won't be able
  to connect to your ASGARD.

  All components you install should have a proper domain name configured
  to avoid issues further during the configuration.
