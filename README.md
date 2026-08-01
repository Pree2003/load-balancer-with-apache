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


<img width="410" height="43" alt="image" src="https://github.com/user-attachments/assets/8e8ce291-410b-4d72-9ea7-6578217458e6" />

I used the command sudo systemctl status apache2

<img width="553" height="117" alt="image" src="https://github.com/user-attachments/assets/8c7c37fb-db4e-40b2-97d0-a08345e81828" />

I ran configtest and ran the system but it showed me errors 

<img width="554" height="251" alt="image" src="https://github.com/user-attachments/assets/479c11ee-411b-497a-b80f-c735036d85b8" />

My next step was to run  sudo bash -c 'cat << "EOF" > /etc/apache2/sites-available/000-default.conf to overwrite the file. 

<img width="554" height="430" alt="image" src="https://github.com/user-attachments/assets/1ee0b394-f32a-47f5-8d15-bb5699107622" />

After that I ran sudo apache2ctl configtest to test the syntax and it finally returned Syntax OK the I finally restarted apache system then finally checked if it the system is running then it showed it is running and active.

<img width="426" height="278" alt="image" src="https://github.com/user-attachments/assets/687df8d9-6111-4d51-b3e5-f9844eb4fa22" />

I finally opened public address of my load balancer then It finally wrote Hello from Web Server 1 to show that it is finally working. 

<img width="502" height="298" alt="image" src="https://github.com/user-attachments/assets/131cbd49-3ec6-4094-8507-8d837be8a17a" />

<img width="554" height="429" alt="image" src="https://github.com/user-attachments/assets/8c70b964-e9c4-49ed-bc88-5d8451b72c2a" />

<img width="554" height="436" alt="image" src="https://github.com/user-attachments/assets/49f6fffb-b0fe-486c-bd91-8b6a6e181c91" />

Load Balancer routed traffic only to Web Server 1; Web Server 2 failed with 403 Forbidden.SELinux blocked Apache on Web Server 2, and lbmethod=bytraffic cached initial backend failures.SELinux modules via audit2allow, switched load balancing to lbmethod=byrequests, and enabled lbmethod_byrequests. Traffic now balances 50/50.

<img width="554" height="107" alt="image" src="https://github.com/user-attachments/assets/292c816d-2ba6-4463-9a24-bea50df0bdab" />

<img width="553" height="104" alt="image" src="https://github.com/user-attachments/assets/125be222-7f3d-4a1b-be57-f95c938b0d9a" />

I ran sudo tail -f /var/log/httpd/access_log on both Web Server 1 and Web Server 2 to monitor live traffic streams and verify that the Apache load balancer is successfully distributing requests across both nodes.


<img width="398" height="379" alt="image" src="https://github.com/user-attachments/assets/5d223ac7-c3fa-47de-9132-fff6a56e6c7c" />

<img width="432" height="205" alt="image" src="https://github.com/user-attachments/assets/25fcf994-9cd3-47a8-8cfc-7bda0012a5c5" />

<img width="379" height="296" alt="image" src="https://github.com/user-attachments/assets/050697e1-cbeb-4432-91d3-4247b9fab52d" />









