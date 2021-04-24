Worker (ezb_wks)
===================

This service is in charge of executing your scripts. It must be started with an account with the appropriate rights.
You must install as much *workers* as you have service account to use.

Windows
-------

1. Download ezb_wks from `GitHub <https://github.com/ezBastion/ezb_worker/releases/latest>`_ .
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

2. Open a admin command prompte, like CMD or Powershell.
""""""""""""""""""""""""""""""""""""""""""""""""""""""""

3. Run ezb_wks.exe with **init** option.
""""""""""""""""""""""""""""""""""""""""

- ezb_pki: tpc address and port of ezb_pki.
- SAN: (Subject Alternative Name) Valid FQDN comma separated list for this certificate. 

4. Edit config.json
"""""""""""""""""""
- Set service name and description.
- Change if need, listener address and port [1]_.

.. code-block:: json

    {
        "listen": ":5003",
        "scriptpath": "E:\\ezbastion\\ezb_worker/script",
        "jobpath": "E:\\ezbastion\\ezb_worker/job",
        "loglevel": "info",
        "privatekey": "cert/ezb_wks.key",
        "publiccert": "cert/ezb_wks.crt",
        "cacert": "cert/ca.crt",
        "servicename": "ezb_wks",
        "servicefullname": "ezBastion worker",
        "ezb_pki": "ezb_pki.fqdn:5000",
        "san": [
            "mydbserver",
            "mydbserver.fqdn"
        ],
        "limitwarning": 20,
        "limitmax": 50
    }


5. Install Windows service and start it.
""""""""""""""""""""""""""""""""""""""""
.. code-block:: powershell

    ezb_wks install
    ezb_wks start



.. [1] *:port* for all interfaces, *1.2.3.4:port* for IPv4, *0.0.0.0:port* for all IPv4 interfaces, *address.fqdn:port* for DNS resolution.
