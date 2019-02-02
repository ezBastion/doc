############
architecture
############

.. image:: /image/under-construction.png


.. image:: /image/EZBNetwork.jpg

ezBastion architecture is split in three zones, public, infrastructure and business.

***********
Public zone
***********

This area is accessible by clients (users, services, computers) and must use corporate certificates. It is recommended to use multiple bastion (ezb_srv) and security token authority (ezb_sta) behind a load balancing system.

ezb_sta
=======

Secure Token Authority (sta) provide Windows domain authentication.

- Authentication
- Token (jwt) issuer

ezb_srv
=======

This node, called *Bastion*, is the front part of ezBastion architecture. It receive all clients requests and serves as api gateway.

- Authorization
- Cache (l1)
- Logging
- Load balancing workers

*******************
Infrastructure zone
*******************

This area is dedicated to ezBastion management team. 

ezb_pki
=======

This node provide ECDSA certificates, used by all ezBastion’s node to communicate. 

- Certificates

ezb_db
======

The database is used to store ezBastion configuration and clients access rules.

- ezBastion configuration
- API configuration
- Access log

ezb_admin
=========

All managment and configutaion, are made from a centralized web console.

- Web console

*************
business zone
*************

The services running in this area are business dependent. You can provide API to different business line, using dedicated workers.

ezb_worker
==========

The workers are the infrastructure backend. There are in charge to execute business tasks and return result to the bastion.

- Task execution


ezb_vault
=========

