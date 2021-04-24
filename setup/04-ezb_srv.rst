Front server (ezb_srv)
====================

this is the service that is responsible for routing and validating authorizations. It receive the requests and give them to the workers.
It is advisable to have at least two servers behind a load balancer. You must copy all public certificat from STA services to cert folder.


Windows
-------

1. Download ezb_srv from `GitHub <https://github.com/ezBastion/ezb_bastion/releases/latest>`_ .
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

2. Open a admin command prompte, like CMD or Powershell.
""""""""""""""""""""""""""""""""""""""""""""""""""""""""

3. Run ezb_srv.exe with **init** option.
""""""""""""""""""""""""""""""""""""""""

- ezb_pki: tpc address and port of ezb_pki.
- SAN: (Subject Alternative Name) Valid FQDN comma separated list for this certificate. 

4. Edit config.json
"""""""""""""""""""
- Set service name and description.
- Change if need, listener address and port [1]_.
- Add the first STA address.
- Set *cacheL1* duration in second [2]_.

.. code-block:: json

    {
        "listen": "0.0.0.0:5002",
        "ezb_db": "https://ezb_db.fqdn:8444/",
        "loglevel": "info",
        "cacheL1": 60,
        "privatekey": "cert/ezb_srv.key",
        "publiccert": "cert/ezb_srv.crt",
        "cacert": "cert/ca.crt",
        "servicename": "ezb_srv",
        "servicefullname": "ezBastion front",
        "ezb_pki": "ezb_pki.fqdn:5000",
        "san": [
            "mydbserver",
            "mydbserver.fqdn"
        ]
    }


5. Install Windows service and start it.
""""""""""""""""""""""""""""""""""""""""
.. code-block:: powershell

    ezb_srv install
    ezb_srv start

.. [1] *:port* for all interfaces, *1.2.3.4:port* for IPv4, *0.0.0.0:port* for all IPv4 interfaces, *address.fqdn:port* for DNS resolution.
.. [2] The *cacheL1* is the retention time for information comming from the database.