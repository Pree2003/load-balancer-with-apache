# load-balancer-with-apache
Built a scalable web architecture on AWS deploying Apache as a Layer 7 Load Balancer. Configured traffic distribution across RHEL8 web servers backed by a MySQL database and NFS for centralized storage.

<img width="554" height="120" alt="image" src="https://github.com/user-attachments/assets/f81eeafb-d166-4584-9b33-a1a122ebd5bb" />

## Key Architecture Highlights
- Load Balancer:Configured Apache (Layer 7) to distribute incoming traffic across two RHEL8 web servers.
- Backend Services:Integrated a central NFS server for shared web file storage and a dedicated MySQL database server.
- Service Integration:Successfully re-indexed and restarted backend instances to sync with updated load balancer rules.

 <img width="554" height="52" alt="image" src="https://github.com/user-attachments/assets/85fd7a77-3b2e-4047-b871-f132bb451c83" />

 All 4 instances are running 

 
 
