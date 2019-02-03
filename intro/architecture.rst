
.. image:: ../image/ezb-logo-large.png
   :align: center

########
Overview
########

The purpose of ezBastion is to allow you to provide your administrative tasks via REST requests. Once the nodes have been installed,
you will be able to import your system administrators's scripts and assign them an HTTPS URL. To finish, declare the users and 
delegate the apis.

In general, to administer a system, you need 4 elements:

- An administrator account.
- The knowledge of the product.
- Access rights and flow opening.
- Consoles or administrative clients.

Just one question: Do you have any actions that could be delegated, if there were not the above points?

############
Architecture
############

ezBastion architecture is split in three zones, public, infrastructure and business and six microservices.

.. image:: /image/EZBNetwork.jpg

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

Some time we need user/password inside a script, and clear password is evil !  Vault node, will store key/value inside an *AES* dedicated DB.

- key/value secure store
