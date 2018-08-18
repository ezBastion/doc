6/ admin console
====================

The ezBastion console is dedicated to API administrator. With this web console you can declare some account, api and link them together.
 A dashboard provide ezBastion statistic. ezb_admin is a pure javascript application, running 100% on the administrator browser (HTML5 mandatyory).
  

1. Http server
"""""

Any OS, any http server without module. Just prepare a server for static file.

2. Download
""""

download ezb_admin from `GitHub <https://github.com/ezBastion/ezb_admin/releases/latest>`_  into your web server root folder.

3. Edit config.json
"""""""""""""""""""
- ezb_db: The ezb_db address with JWT/token port.
- ezb_srv: The ezb_srv front address and port.

*Don't forget the trailing end slash.*

.. code-block:: json

    {
        "ezb_db":"https://ezb_db.fqdn:8443/",
        "ezb_srv":"http://esb_srv.fqdn:5100/"
    }

4. Connect
====

With your preferred HTML5 browser, login with admin/ezBastion default account and start converting your scripts into API.

.. image:: /image/ezb_admin_login.jpg