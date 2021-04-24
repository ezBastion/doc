Setup mode
==========

Simple architecture
-------------------

Install all services on the same machine with a unique setup. Ideal for proof of concept. 
Download the "setup_win64.zip" package here https://github.com/ezBastion/ezBastion/releases/latest, unzip the setup file and follow 
the "next, next, next, finish" install. You need a windows server with 200Mo free space and 5 minutes.


Expert architecture
-------------------

For stronger architecture, you can use as much server as you need. Use load balancing for microservices except workers that use their own system.
Download latest binaries from https://github.com/ezBastion/ezBastion/releases/latest asset and follow the dedicated microservice documentation.
You can use your own web servers, ezBastion just need a web server ready for static files like nginX, IIS or Apache.

Setup prerequisite
==================

ezBastion try to be lighter as possible, the setup is fast and can be fully automatised. You need at least:

- Any edition of Windows servers 64b.
- ~20Mo free space by service.
- 30Mo memory by service.
- Admin right to install service.
- 30 minutes.

Network
-------

Each ezBastion microservices are independent, you can put them on the same server (like for a POC) or split installation on different server for heavy-duty. 
You must choose a TCP port by service and open dedicated routes/port.

Your api customers need:
- public    -> ezb_sta
- public    -> ezb_srv

Your api administrators need:
- ezb_admin -> ezb_db
- ezb_admin -> ezb_sta
- ezb_admin -> ezb_srv

microservices communication:
- ezb_sta   -> ezb_pki
- ezb_sta   -> ezb_db
- ezb_srv   -> ezb_pki
- ezb_srv   -> ezb_sta
- ezb_srv   -> ezb_db
- ezb_srv   -> ezb_wks
- ezb_wks   -> ezb_pki
- ezb_db    -> ezb_pki


SSL/TLS
-------

Internal ezBastion communication use rest over tls 1.2 with ECDSA certificate. For external access, you must provide your own certificates for ezb_srv and ezb_sta.

