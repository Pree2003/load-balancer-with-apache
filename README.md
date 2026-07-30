# load-balancer-with-apache
Built a scalable web architecture on AWS deploying Apache as a Layer 7 Load Balancer. Configured traffic distribution across RHEL8 web servers backed by a MySQL database and NFS for centralized storage.

<img width="554" height="120" alt="image" src="https://github.com/user-attachments/assets/f81eeafb-d166-4584-9b33-a1a122ebd5bb" />

## Key Architecture Highlights
- Load Balancer:Configured Apache (Layer 7) to distribute incoming traffic across two RHEL8 web servers.
- Backend Services:Integrated a central NFS server for shared web file storage and a dedicated MySQL database server.
- Service Integration:Successfully re-indexed and restarted backend instances to sync with updated load balancer rules.

 <img width="554" height="52" alt="image" src="https://github.com/user-attachments/assets/85fd7a77-3b2e-4047-b871-f132bb451c83" />

 All 4 instances are running 

<img width="554" height="164" alt="image" src="https://github.com/user-attachments/assets/c4f9e982-b80f-4c1c-b9f3-c905be5685f5" />

I had to stop 1 server so I can add have project-8-apache-lb as another instance because of the vpu limit.

<img width="554" height="58" alt="image" src="https://github.com/user-attachments/assets/78aeaa22-f840-46cf-b9fe-b8533fe3955a" />

Created another instance called  have project-8-apache-lb

<img width="554" height="475" alt="image" src="https://github.com/user-attachments/assets/acb997cb-7645-4124-99b6-4041e7f1977f" />

I logged into my have project-8-apache-lb server 

<img width="553" height="230" alt="image" src="https://github.com/user-attachments/assets/ada985b1-1ce9-4b32-9763-3486b1ef072a" />

I edited inbound rules and opened port 80 on my project-8-apache-lb server instance

INSTALLING APACHE

<img width="554" height="400" alt="image" src="https://github.com/user-attachments/assets/66e5f81e-a8d3-4657-a648-8dbf3490b816" />

 I used the commando sudo apt update to update the packages offered by ubuntu server
 
<img width="554" height="326" alt="image" src="https://github.com/user-attachments/assets/a3067296-a873-411a-b48d-ef7c3cf46ca7" />

<img width="554" height="326" alt="image" src="https://github.com/user-attachments/assets/d5b30b75-38e8-466d-9ee0-fd22da632547" />

<img width="553" height="253" alt="image" src="https://github.com/user-attachments/assets/a1ad14b3-9a06-443a-82f7-47cb4a10ce48" />

ENABLING MODULES

<img width="445" height="568" alt="image" src="https://github.com/user-attachments/assets/5117263d-b079-427e-a3af-d96dfcc2f2d4" />

I enabled modules using the following commands:

sudo a2enmod rewrite
,sudo a2enmod proxy
,sudo a2enmod proxy_balancer
,sudo a2enmod proxy_http
and sudo a2enmod headers
sudo a2enmod lb_method_bytraffic

RESTARTING APACHE2

<img width="413" height="40" alt="image" src="https://github.com/user-attachments/assets/797d5d8c-eb11-4431-b2af-782a5ee14955" />

I used sudo systemctl restart apache2 to restart apache2 services

MAKING SURE APACHE2 IS UP AND RUNNING

<img width="554" height="245" alt="image" src="https://github.com/user-attachments/assets/1c2a330c-da4b-4aed-aa72-17f937f1e7cb" />

I used the command sudo systemctl status apache2

CONFIGURING LOAD BALANCING

<img width="554" height="407" alt="image" src="https://github.com/user-attachments/assets/bc3bebb7-c3cd-44e6-afbe-57062b372cc3" />




