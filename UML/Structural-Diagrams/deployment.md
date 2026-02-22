# 🧠 What is a Deployment Diagram?

A **Deployment Diagram** is a UML diagram that shows:

* Physical infrastructure (servers, devices)
* Software deployment (apps, services)
* Network communication

> 👉 Focus: **WHERE your system runs**

---

# 🎯 Purpose

* Visualize infrastructure
* Show deployment topology
* Understand communication between nodes
* Plan scalability & production setup

---

# 🧩 High-Level Deployment Architecture

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2A_DKUnMCqHOs18zMBs4VDIQ.png)

![Image](https://www.uml-diagrams.org/examples/deployment-example-hardware-load-balancing.png)

![Image](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2019/10/11/Anand-entrypoint-1.png)

![Image](https://hpe-developer-portal.s3.amazonaws.com/uploads/media/2020/11/clusters-1605078500093.png)

---

## 🧠 Nodes (Physical Units)

```
Client (Browser)
CDN / Load Balancer
API Gateway (Kong)
Microservices (Docker/K8s)
Databases
Cache (Redis)
Message Queue (Kafka)
```

---

# 🔗 Deployment Flow

```
[ Browser ]
     ↓
[ CDN / Nginx ]
     ↓
[ API Gateway (Kong) ]
     ↓
[ Order Service ] ---> [ User Service ]
     ↓
[ PostgreSQL ]
     ↓
[ Redis / Kafka ]
```

---

# 🧩 UML Symbols

---

## 1️⃣ Node (Server / Device)

### 📌 Symbol:

* 3D box

### 💡 Example:

* EC2 instance
* Docker container
* Kubernetes pod

---

## 2️⃣ Artifact

### 📌 Symbol:

* File icon 📄

### 💡 Example:

* Angular build (`dist/`)
* NestJS app (`.js`)

---

## 3️⃣ Communication Path

### 📌 Symbol:

* Solid line

### 💡 Meaning:

* Network communication

---

## 4️⃣ Execution Environment

### 📌 Example:

* Node.js runtime
* Docker container

---

# 🧩 Real Deployment (Your Stack 🔥)

---

## 🌐 Frontend (Angular)

```
Node: Browser
Artifact: Angular App (dist/)
Deployed on: Nginx / CDN
```

---

## 💻 Backend (NestJS)

```
Node: Docker Container
Artifact: NestJS App
Runtime: Node.js
```

---

## 🗄️ Database

```
Node: PostgreSQL Server
Artifact: DB schema
```

---

## ⚡ Cache

```
Node: Redis
Purpose: Fast access
```

---

## 📩 Messaging

```
Node: Kafka / RabbitMQ
Purpose: Async communication
```

---

# 💻 Code Mapping (VERY IMPORTANT)

---

## 🧩 Angular Build (Artifact)

```bash
ng build --prod
```

👉 Generates:

```
dist/
```

✔ Deployed to Nginx

---

## 🧩 NestJS App (Artifact)

```bash
npm run build
node dist/main.js
```

✔ Runs inside Docker

---

## 🧩 Docker (Execution Environment)

```dockerfile
FROM node:18

WORKDIR /app
COPY . .

RUN npm install
RUN npm run build

CMD ["node", "dist/main.js"]
```

---

## 🧩 Kubernetes (Deployment)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: order-service
spec:
  replicas: 3
  template:
    spec:
      containers:
        - name: order
          image: order-service:latest
          ports:
            - containerPort: 3000
```

---

# 🔥 Full Deployment Example

```
[ User Browser ]
      ↓
[ Nginx (Angular dist) ]
      ↓
[ Kong API Gateway ]
      ↓
[ Order Service (Docker/K8s) ]
      ↓
[ PostgreSQL DB ]

Optional:
→ Redis (cache)
→ Kafka (events)
```

---

# ⚠️ Common Mistakes

❌ Mixing with component diagram
❌ Showing code-level details
❌ Ignoring infrastructure
❌ Not separating nodes

---

# 🔥 Best Practices

* Show **real infrastructure**
* Separate frontend/backend
* Use **containers (Docker)**
* Add **scaling (replicas)**

---

# 🧠 Senior-Level Insight

> Deployment diagrams represent the physical distribution of software artifacts across infrastructure, helping engineers design scalable, fault-tolerant systems.

---

# 🎯 Simple Memory Trick

👉

* Component Diagram → **What runs**
* Deployment Diagram → **Where it runs**

---

# 🧪 Practice

Design deployment for:

👉 Food Delivery App

Include:

* Mobile App
* API Gateway
* Order Service
* Payment Service
* Redis
* Kafka

---

# 📄 Deployment Diagram – Symbols & Explanation

---

## 🧠 Overview

Deployment diagrams use UML symbols to represent:

* Physical infrastructure
* Software artifacts
* Runtime environments
* Network communication

---

# 🧩 1️⃣ Node (Device / Server)

![Image](https://www.softwareideas.net/i/DirectImage/368/uml-deployment-diagram)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-deployment-diagram/02-deployment-diagram-notations.png)

![Image](https://www.uml-diagrams.org/deployment-diagrams/deployment-diagram-overview-specification.png)

![Image](https://i.sstatic.net/CqokR.png)

### ✅ Symbol:

* 3D box (cube-like)

### 📌 Meaning:

Represents a **physical or virtual machine**

---

### 💡 Examples:

* EC2 instance
* Kubernetes Pod
* Docker Container
* Local server

---

### 💻 Mapping

```text
Node: EC2 Server
```

---

# 🧩 2️⃣ Artifact

![Image](https://www.uml-diagrams.org/deployment-diagrams/deployment-artifact-overview.png)

![Image](https://www.visual-paradigm.com/VPGallery/img/diagrams/Deployment/Deployment-Diagram-Sample.png)

![Image](https://www.uml-diagrams.org/deployment-diagrams/deployment-artifact-composition.png)

### ✅ Symbol:

* Rectangle with folded corner 📄

### 📌 Meaning:

Represents **deployable code**

---

### 💡 Examples:

* Angular build (`dist/`)
* NestJS compiled code (`.js`)
* JAR / Docker image

---

### 💻 Mapping

```bash
dist/main.js
```

---

# 🧩 3️⃣ Execution Environment

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AYZY-jklQo6SdOCUzVZ138g.png)

![Image](https://www.uml-diagrams.org/deployment-diagrams/deployment-target-overview.png)

![Image](https://www.researchgate.net/publication/332436164/figure/fig1/AS%3A748137048199168%401555381180305/UML-diagram-of-the-container-based-application-deployment-metamodel.ppm)

![Image](https://www.visual-paradigm.com/VPGallery/img/diagrams/Deployment/Deployment-Diagram-Sample.png)

### ✅ Symbol:

* Node inside another node

### 📌 Meaning:

Represents runtime environment

---

### 💡 Examples:

* Node.js runtime
* JVM
* Docker container

---

### 💻 Mapping

```text
Docker → Node.js → App
```

---

# 🧩 4️⃣ Communication Path

![Image](https://www.uml-diagrams.org/deployment-diagrams/deployment-diagram-overview-specification.png)

![Image](https://images.wondershare.com/edrawmax/articles2024/deployment-diagram-examples/deployment-diagram-for-client-server-architecture.jpg)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-deployment-diagram/02-deployment-diagram-notations.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-deployment-diagram/05-deployment-diagram-tcpip-example.png)

### ✅ Symbol:

* Solid line

### 📌 Meaning:

Represents **network communication**

---

### 💡 Examples:

* HTTP
* TCP
* gRPC

---

### 💻 Mapping

```text
Frontend → Backend (HTTP)
```

---

# 🧩 5️⃣ Component inside Node

![Image](https://www.uml-diagrams.org/deployment-diagrams/deployment-diagram-overview-specification.png)

![Image](https://www.softwareideas.net/i/DirectImage/368/uml-deployment-diagram)

![Image](https://images.wondershare.com/edrawmax/templates/deployment-diagram-for-client-server.png)

### ✅ Symbol:

* Component inside node

### 📌 Meaning:

Shows **which service runs on which node**

---

### 💡 Example:

```
Node: Docker
  └── Order Service
```

---

# 🧩 6️⃣ Database Node

![Image](https://www.conceptdraw.com/How-To-Guide/picture/Design-elements-UML-deployment-diagrams.png)

![Image](https://www.uml-diagrams.org/deployment-diagrams/deployment-diagram-overview-specification.png)

![Image](https://conceptdraw.com/a1670c3/p1/preview/640/pict--uml-deployment-diagram-symbols-design-elements---uml-deployment-diagrams.png--diagram-flowchart-example.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-deployment-diagram/05-deployment-diagram-tcpip-example.png)

### ✅ Symbol:

* Cylinder shape

### 📌 Meaning:

Represents database

---

### 💡 Examples:

* PostgreSQL
* MongoDB

---

---

# 🧩 7️⃣ Device Node (Client)

![Image](https://d1tzxux72fvryy.cloudfront.net/M89e80bbafdbff1e29f4aa4d3a01f7c671704190190820/preview/M89e80bbafdbff1e29f4aa4d3a01f7c671704190190820.png)

![Image](https://i.sstatic.net/VQwpm.png)

![Image](https://www.researchgate.net/publication/225548717/figure/fig7/AS%3A302680036659206%401449175952787/UML-Deployment-Diagram-for-Map-Client.png)

![Image](https://www.conceptdraw.com/How-To-Guide/picture/Design-elements-UML-deployment-diagrams.png)

### ✅ Symbol:

* Device (mobile/laptop icon)

### 📌 Meaning:

Represents **end user system**

---

### 💡 Examples:

* Browser
* Mobile App

---

---

# 🧠 Summary Table

| Symbol                | Meaning                   |
| --------------------- | ------------------------- |
| Node                  | Server / Machine          |
| Artifact              | Deployable code           |
| Execution Environment | Runtime (Docker, Node.js) |
| Communication Path    | Network connection        |
| Component in Node     | Running service           |
| Database (Cylinder)   | DB                        |
| Device Node           | Client                    |

---

# 🎯 Simple Memory Trick

👉

* Box → Server
* File → Code
* Small box inside → Runtime
* Line → Communication
* Cylinder → Database

```
Code → Component → Node → Deployment
```

**Youtube Link:-** (https://www.youtube.com/watch?v=WnMQ8HlmeXc&t=5960s)
