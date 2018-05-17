ezBastion STA (ezb_sta)
======================

The STA (Secure Token Authority) is the second node to install. It create JWT token after account authentication.  The JWT was signed with ECDSA key provided by ezb_pki, you must
copy ezb_sta public key in all other nodes cert folder. 



Prerequisite
------------

- Any edition of Windows servers 64b.
- 20Mo free space.
- 30Mo memory.
- Admin right to install service.
- Internet access to download node.js modules
- 5 minutes.


setup
-----

1. Download ezb_sta from `GitHub <https://github.com/ezBastion/ezb_sta/releases/latest>`_ 
2. Download latest node.js with npm from `official node.js site <https://nodejs.org/en/download/>`_ 
3. Install nodes.js
4. Unzip ezb_sta package into the final Windows service folder
5. Open a admin command prompte, like CMD or Powershell.
6. From ezb_sta folder, install module with npm

.. code-block:: posh

    PS E:\ezbastion\ezb_sta> npm install

.. image:: /image/sta-npm.gif


7. Use sta-setup.exe to generate config.json and certificat key pair

.. image:: /image/sta-setup.gif


8. Install windows service

.. code-block:: posh

    PS E:\ezbastion\ezb_sta> node installService.js


