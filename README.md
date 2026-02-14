# Travel Memory

`.env` file to work with the backend after creating a database in mongodb: 

```
MONGO_URI='mongodb+srv://rahul_3077:>password<@rahulmongodb.zh7l1fq.mongodb.net/'
PORT=3001
```

Data format to be added: 

```json
{
    "tripName": "Incredible India",
    "startDateOfJourney": "19-03-2022",
    "endDateOfJourney": "27-03-2022",
    "nameOfHotels":"Hotel Namaste, Backpackers Club",
    "placesVisited":"Delhi, Kolkata, Chennai, Mumbai",
    "totalCost": 800000,
    "tripType": "leisure",
    "experience": "Lorem Ipsum, Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum,Lorem Ipsum, ",
    "image": "https://t3.ftcdn.net/jpg/03/04/85/26/360_F_304852693_nSOn9KvUgafgvZ6wM0CNaULYUa7xXBkA.jpg",
    "shortDescription":"India is a wonderful country with rich culture and good people.",
    "featured": true
}
```


For frontend, you need to create `.env` file and put the following content (remember to change it based on your requirements):
```bash
REACT_APP_BACKEND_URL=http://localhost:3001
```
# Travel Memory
## Deployment Architecture Diagram

The Deployment architecture of the Travel Memory application is designed to ensure high avaliability, scalability, security, and efficient traffic management. The architecture follows a multi - layered apprroach where each component plays a critical role in delivering a seamless user experience.
<img width="1044" height="990" alt="image" src="https://github.com/user-attachments/assets/e5c832aa-6d1f-4522-857f-6e866ba6a6b6" />

# 1. User Layer:
The process begins when users access the application through a custom domain using their web browsers. This domain is managed by Cloudflare, which provides faster DNS resolution, enhanced security, and protection against potential cyber threats such as Distributed Denial - of - Services (DDoS) attracks.

# 2. DNS and Security Layer (Cloudflare):
Cloudfare acts as an intermediary between users and the hosting infrastructure. It routes incoming requests to the appropriate server while improving performance through caching and secure HTTPS connections. This layer ensures that the application remains accessible and protected. its helps in:
* Faster DNS resolution
* Basic security protection
* HTTPS suppot
  
# 3. Load Balanace Layer:
An Application Load Balancer (ALB) is used to distribute incoming traffic across multiple EC2 instances. Instead of overwhelming a single server, the load balancer intelligently routes requests to healthy instances using health checks. This improves fault tolerance and ensures minimal downtime even if one instance fails. why we use it:
* Prevents one server from getting overloaded
* Improves performance
* Increase availability

# 4. Compute Layer (Amazon EC2 Insatances):
Multiple Amazon EC2 instances host the Travel Memory application. Each instance contains boths the frontend and backend components required to run the platform. 
- Running multiple instances provides:
  * High avaliability
  * Better Performance during peak traffic
  * Improved reliability
  * Horizontal scalability
if traffic increases, additional instances can be launched without affecting the application's stability.

# 5. Reverse Proxy Layer (Nginx):
Nginx is configured as a reverse proxy server within each EC2 instance. It acts as a gateway that receives client requests and forwards them to the Node.js backend running on port 3000.
- Key benefits include:
  * Enhanced security by hiding internal ports
  * Improved request handling
  * Faster static content delivery
  * Better resource utilization
  
# 6. Application Layer (Node.js + Express _ React):
The backend of the Travel Memory application is powered by Node.js and Express, which handles API requests, business logic, and communication with the database. The React frontend provides an interactivee and responsive user interface.
The frontend communicates with the backend via REST APIs, ensuring smooth data exchange and real - time updates.

# 7. Database Layer (MangoDB):
MangoDB server as the primary database for storing travel memories, user infromation, and application data. its flexible schema and high peroformance make it ideal for modern cloud - based applications.
- Using a cloud - hosted database such as MangoDB Atlas further improves:
  * Data redundancy
  * Automated backups
  * Scalability
  * Security

## Architectue Flow Summary:
The Complete request flow is as follows:
User → Cloudflare → Application Load Balancer → EC2 Instances → Nginx → Node.js Backend → MangoDB Databases
- This Structured architecture ensures that the Travel Memory application remains scalable, resilient, and production - ready while following modern cloud deployment best practices.

# EC2 Instance Deployment:
<img width="1290" height="484" alt="Screenshot 2026-02-13 at 9 28 15 PM" src="https://github.com/user-attachments/assets/89f936d9-f904-4cf6-ad81-1424f6d326b7" />

# Security Group:
<img width="1294" height="647" alt="Screenshot 2026-02-13 at 9 33 14 PM" src="https://github.com/user-attachments/assets/490e38ac-45b6-4050-8fd0-7f67e232f990" />

# Target Groups:
<img width="1512" height="982" alt="Screenshot 2026-02-13 at 9 35 01 PM" src="https://github.com/user-attachments/assets/6aea12e9-86fe-4357-9071-86b74f7f212f" />

# Load Balancers:
<img width="1512" height="982" alt="Screenshot 2026-02-14 at 1 22 39 PM" src="https://github.com/user-attachments/assets/46edf5e7-5af7-45d1-8220-e2dcc8cbaf58" />

# VPC Dashboard:
<img width="1512" height="982" alt="Screenshot 2026-02-13 at 9 44 42 PM" src="https://github.com/user-attachments/assets/a3e3ddd0-c2b6-4f50-a9aa-d88adc4f2f7c" />

# Internet Gateway:
<img width="1512" height="982" alt="Screenshot 2026-02-13 at 9 44 31 PM" src="https://github.com/user-attachments/assets/5eda7adb-d96e-4474-9dcf-c457777c8d05" />

# Backend Server Running on Port: 15.207.117.196:3001/hello:
<img width="1292" height="879" alt="Screenshot 2026-02-08 at 10 01 04 PM" src="https://github.com/user-attachments/assets/b48b8262-ae02-4c25-8d4e-a09d73fdeb5a" />

# After deploy server:
<img width="1292" height="884" alt="Screenshot 2026-02-08 at 10 01 00 PM" src="https://github.com/user-attachments/assets/1bce25c7-1241-46b5-8650-1ac477394529" />

# npm:
<img width="1255" height="226" alt="Screenshot 2026-02-08 at 10 01 04 PM" src="https://github.com/user-attachments/assets/687cae4f-864f-4899-adfd-4069efd0790c" />

# Reverse Proxy:
<img width="1292" height="375" alt="Screenshot 2026-02-08 at 10 48 44 PM" src="https://github.com/user-attachments/assets/a9ce08b4-4101-4f97-8dfa-44ba434edf2f" />

# Cloudfare:
<img width="1512" height="982" alt="Screenshot 2026-02-14 at 1 38 42 PM" src="https://github.com/user-attachments/assets/dd26e918-245a-4274-a73c-14d55254b7db" />
