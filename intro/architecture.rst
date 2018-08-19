architecture
============

.. image:: /image/under-construction.png


.. image:: /image/EZBNetwork.jpg

ezBastion architecture is split in three zones, public, infrastructure and business.

Public zone
^^^

This area is accessible by clients (users, services, computers) and must use corporate certificates. It is recommended to use multiple bastion (ezb_srv) and security token authority (ezb_sta) behind a load balancing system.

ezb_srv
===



ezb_sta
===

Infrastructure zone
^^^

This area is dedicated to ezBastion management.

ezb_pki
===

ezb_db
===

ezb_admin
===

business zone
^^^

The services running in this area are business dependent.

ezb_worker
===

ezb_vault
===
