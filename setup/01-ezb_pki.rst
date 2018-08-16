ezBastion PKI (ezb_pki)
======================


The PKI (Public Key Infrastructure) is the first node to be installed. It will be in charge to create and deploy the ECDSA pair key, used by all ezBastion's node to communicate.
The certificates are used to sign JWT too.


1. Download ezb_pki from `GitHub <https://github.com/ezBastion/ezb_pki/releases/latest>`_ .
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

2. Open a admin command prompte, like CMD or Powershell.
""""""""""""""""""""""""""""""""""""""""""""""""""""""""
3. Run ezb_pki.exe with **init** option.
""""""""""""""""""""""""""""""""""""""""
- name: This is the name used as Windows service and as certificates root name.
- fullname:The Windows service description.
- listen: The TCP/IP port used by ezb_pki to respond at nodes request. This port MUST BE reachable by all ezBastion's node.


4. Install Windows service and start it.
""""""""""""""""""""""""""""""""""""""""
.. code-block:: powershell

    ezb_pki install
    ezb_pki start

.. image:: /image/pki-setup.gif

security consideration
----------------------
- ezb_pki is an auto-enrolment system, if you do not add nodes, stop the service or don't install it and use debug mode instead.
- Protect cert folder.
- Backup the private/public key.








