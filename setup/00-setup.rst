Setup mode
==========

Simple architecture
-------------------

Install all services on the same machine with a unique setup. Ideal the small configuration or proof of concept. 
Download the "ezbastion_allinone.zip" package here https://github.com/ezBastion/doc/releases/latest, unzip the ezbastion.exe file and follow 
the "next, next, next, finish" install. You need a windows server with 100Mo free space, a web service (IIS/nginX..) and 5 minutes.


Expert architecture
-------------------

For stronger architecture, you can use as much server as you need. Use load balancing for microservices except workers that use their own system.
 Download latest binary https://www.ezbastion.com/download and follow the documentation below to install and configure all microservices.

Setup prerequisite
==================

ezBastion try to be lighter as possible, the setup is fast and can be full automatised. You need at least:

- Any edition of Windows servers 64b.
- 20Mo free space by service.
- 30Mo memory by service.
- Admin right to install service.
- Internet access to download sources.
- 30 minutes.
- A web server ready for static files like nginX, IIS or Apache

Network
-------

Each ezBastion microservices are independent, you can put them on the same server (like for a POC) or split installation on different server for heavy-duty. 
You must choose a TCP port by service and open dedicated routes/port.

- public    -> ezb_sta
- public    -> ezb_srv
- ezb_admin -> ezb_db
- ezb_admin -> ezb_sta
- ezb_admin -> ezb_srv
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

