ezBastion PKI (ezb_db)
======================


The PKI (Public Key Infrastructure) is the first node to be installed. It will be in charge to create and deploy the ECDSA pair key, used by all ezBastion's node to communicate.
The certificates are use to sign JWT too.

Prerequisite
------------

- Any edition of Windows servers 64b.
- 10Mo free space.
- 10Mo memory.
- Admin right to install service.


setup
-----

1. Download ezb_pki from `GitHub <https://github.com/ezBastion/ezb_pki/releases/latest>`_ .

2. Open a admin command prompte, like CMD or Powershell.

3. Run ezb_pki.exe with **init** option.

name:
"""""
This is the name used as Windows service and as certificat root name.

fullname:
""""""""
The Windows service description.

listen:
""""""
The TCP/IP port used by ezb_pki to respond at nodes request. This port MUST BE reachebled by all ezBastion's node.


4. Install Windows service and start it.

.. code-block:: Powershell
    ezb_pki install
    ezb_pki start

.. image:: /image/pki-setup.gif








