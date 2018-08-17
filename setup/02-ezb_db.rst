ezBastion DB (ezb_db)
=====================
This service manages communications to the database. It has two listeners, one for the admin console and one for the bastion (ezb_srv). 
The admin console listerner use JWT authentication while bastion's one use PKI. You must declare the first (default) STA service and copy his public certificat, in the **cert** folder.

Windows
-------

1. Download ezb_db from `GitHub <https://github.com/ezBastion/ezb_db/releases/latest>`_ .
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

2. Open a admin command prompte, like CMD or Powershell.
""""""""""""""""""""""""""""""""""""""""""""""""""""""""
3. Run ezb_db.exe with **init** option.
""""""""""""""""""""""""""""""""""""""""

- ezb_pki: tpc address and port of ezb_pki.
- SAN: (Subject Alternative Name) Valid FQDN comma separated list for this certificate. 

4. Edit config.json
"""""""""""""""""""
- Set service name and description.
- Change if need, JWT & PKI port numbers.
- Add the first STA address.

.. code-block:: json

    {
        "listenjwt": ":8443",
        "listenpki": ":8444",
        "privatekey": "cert/ezb_db.key",
        "publiccert": "cert/ezb_db.crt",
        "cacert": "cert/ca.crt",
        "db": "sqlite",
        "sqlite": {
            "dbpath": "db/ezb_db.db"
        },
        "servicename": "ezb_db",
        "servicefullname": "ezBastion Database",
        "loglevel": "warning",
        "ezb_pki": "ezb_pki.fqdn:5000",
        "san": [
            "mydbserver",
            "mydbserver.fqdn"
        ],
        "default_sta": "https://ezb_sta.fqdn:5001/token"
    }


5. Install Windows service and start it.
""""""""""""""""""""""""""""""""""""""""
.. code-block:: powershell

    ezb_db install
    ezb_db start