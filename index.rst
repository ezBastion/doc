
.. image:: image/ezb-logo-large.png
   :align: center


The purpose of ezBastion is to allow you to provide your administrative tasks via REST requests. Once the nodes have been installed,
you will be able to import your system administrators's scripts and assign them an HTTPS URL. To finish, declare the users and 
delegate the apis.

In general, to administer a system, you need 4 elements:

- An administrator account.
- The knowledge of the product.
- Access rights and flow opening.
- Consoles or administrative clients.

Just one question: Do you have any actions that could be delegated, if there were not the above points?

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Introduction

   intro/architecture
   intro/licensing

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Install

   setup/00-setup

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: microservice   

   setup/01-ezb_pki
   setup/02-ezb_db
   setup/03-ezb_sta
   setup/04-ezb_srv
   setup/05-ezb_wks
   setup/06-admin_console



.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: How to

   howto/first_api
   howto/active_directory
   howto/collection
   howto/polling
   
