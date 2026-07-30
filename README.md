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


 
 
