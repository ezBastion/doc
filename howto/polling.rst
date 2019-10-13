
########
Polling
########

What WikipediA say about "polling"

<< *Polling, or polled operation, in computer science, refers to actively sampling the status of an external device by a client program as a synchronous activity. Polling is most often used in terms of input/output (I/O), and is also referred to as polled I/O or software-driven I/O.* >>

Well ... Let's take an example.

You use a Powershell script for provisioning your's VDI and this script takes 15 minutes. We will use polling to avoid any client timeout. 
If API polling option is checked, ezBastion will return task status link instead of waiting task end. The client will call this link to have the progress of the task and finally get the result.

.. image:: /image/Polling-flow.png




Require:

- ezb_admin v0.1.3
- ezb_db v0.1.4
- ezb_srv v0.1.4
- ezb_wks v0.1.4
