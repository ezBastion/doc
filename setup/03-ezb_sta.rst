3/ STA (ezb_sta)
======================

The STA (Secure Token Authority) is the second node to install. It create JWT token after account authentication.  The JWT was signed with ECDSA key provided by ezb_pki, you must
copy ezb_sta public key in all other nodes cert folder. 


Windows
-------

**1. Download ezb_sta from** `GitHub <https://github.com/ezBastion/ezb_sta/releases/latest>`_ 
**2. Download latest 9.X node.js with npm from** `official node.js site <https://nodejs.org/en/download/>`_ 
**3. Install nodes.js**
**4. Unzip ezb_sta package into the final Windows service folder**
**5. Open a admin command prompte, like CMD or Powershell.**
**6. From ezb_sta folder, install module with npm**

.. code-block:: posh

    PS E:\ezbastion\ezb_sta> npm install

.. image:: /image/sta-npm.gif


**7. Use ezb_sta.exe to generate config.json and certificat key pair**

.. image:: /image/sta-setup.gif


**8. Edit config.json**

- externalkey: private PEM certificat filename, used for https access to this STA.
- externalcert: public PEM certificat filename, used for https access to this STA.

.. code-block:: json

    {
        "externalkey": "",
        "externalcert": "",
        "privatekey": "ezb_sta.key",
        "publiccert": "ezb_sta.crt",
        "cacert": "ca.crt",
        "issuer": "ezb_sta",
        "audience": "ezBastion",
        "jwtttl": 1200,
        "ezbdb": "https://ezb_db.fqdn:8444/",
        "port": 5001
    }

**publiccert** must be the same than issuer name.

**9. Deploy certificat**

Copy **publiccert** into ezb_db and ezb_srv cert folder.

**10. Install windows service**

.. code-block:: posh

    PS E:\ezbastion\ezb_sta> node installService.js


