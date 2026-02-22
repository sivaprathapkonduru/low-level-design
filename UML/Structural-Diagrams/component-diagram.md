# 🧠 What is a Component Diagram?

A **Component Diagram** represents the **high-level architecture of a system**, showing:

- Components (modules/services)

- Interfaces

- Dependencies

- Communication flow

> 👉 Focus: HOW system parts interact (not internal logic)

## 🎯 When to Use

- System Design (LLD + HLD)

- Microservices architecture

- Angular MFE architecture

- API Gateway systems

## 🧩 High-Level Architecture (E-commerce)

![](https://miro.medium.com/v2/1*Tya5S_Z9Vk0Dt3_3lVqZdA.png)

![](https://www.softwareideas.net/i/DirectImage/1714/e-commerce-microservices-architecture-uml-deployment-diagram-)

![](https://substackcdn.com/image/fetch/f_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fa0b90044-5a6a-4df3-b743-4aab38fa4d92_1723x944.png)

![](https://www.uml-diagrams.org/component-diagrams/component-diagram-overview.png)

![](https://www.researchgate.net/profile/M-Rizwan-Qureshi/publication/221663613/figure/fig9/AS:668343640010778@1536356949999/UML-Component-Diagram-of-the-System-Detail-description-of-the-components-Architecture.ppm)

#### 🧠 Components
<pre>
Frontend - (Angular)
API Gateway (Kong/Ngnix)
Microservices: 
  - User Service(NodeJS)
  - Order Service(NodeJS)
  - Product Service(Python-Django)
  - Payment Service(Java-SpringBoot)
Infra:
  - PostgreSQL(SQL)
  - MongoDB(NoSQL)
  - Redis(NoSQL-Memory Cache)
  - RabbitMQ / Kafka (Message Queuing/broker/MQTT)
</pre>

### 🔗 Component Relationships
<pre>
[ Angular App ]
        ↓
[ API Gateway (Kong) ]
        ↓
[ Order Service ] ---> [ User Service ]
        ↓
[ PostgreSQL ]
</pre>

### 🧩 Angular Component Diagram (MFE)
##### 🧠 Structure
<pre>
[ Shell App ]
   ↓
[ Auth MFE ]   [ Product MFE ]   [ Order MFE ]
        ↓
[ Shared Library ]
        ↓
[ API Service Layer ]
</pre>


### 💻 Angular Code Example

        // order.service.ts (Angular)
        @Injectable({ providedIn: 'root' })
        export class OrderService {
        constructor(private http: HttpClient) {}

        createOrder(data: any) {
            return this.http.post('/api/orders', data);
        }
        }

### 🧠 Component Mapping

| Component |	Role |
| ---- | ---- |
| MFE	| Feature module |
| Service |	API communication |
| Shared Lib |	Reusable code|

## 🧩 Backend Component Diagram (NestJS)
#### 🧠 Structure

> [ Controller ] → [ Service ] → [ Repository ] → [ Database ]

### 💻 NestJS Code Example
<pre>
// order.controller.ts
@Controller('orders')
export class OrderController {
  constructor(private orderService: OrderService) {}

  @Post()
  create(@Body() dto: any) {
    return this.orderService.createOrder(dto);
  }
}
</pre>
<pre>
// order.service.ts
@Injectable()
export class OrderService {
  constructor(private repo: OrderRepository) {}

  createOrder(data: any) {
    return this.repo.save(data);
  }
}
</pre>
<pre>
// order.repository.ts
@Injectable()
export class OrderRepository {
  save(data: any) {
    // DB logic
    return data;
  }
}
</pre>

### 🔥 Microservices Interaction
#### 🧠 Example Flow
> Order Service → User Service → Payment Service

### 💻 Code (Service-to-Service)

<pre>
@Injectable()
export class OrderService {
  constructor(private http: HttpService) {}

  async createOrder(userId: string) {
    const user = await this.http.get(`user-service/${userId}`).toPromise();

    // process order
    return { status: 'created', user };
  }
}
</pre>

### 🧩 With Message Queue (Advanced 🔥)
        Order Service → Kafka → Payment Service → Notification Service

### 💻 Example
<pre>
// producer
this.kafka.emit('order_created', order);
</pre>
<pre>
// consumer
@EventPattern('order_created')
handleOrderCreated(order: any) {
  console.log('Processing payment...');
}
</pre>

### 🧠 Database Component Mapping

| Service |	DB |
| ---- | ---- |
| User Service |	MongoDB |
| Order Service |	PostgreSQL |
| Cache |	Redis |
| Messaging |	Kafka / RabbitMQ |

### ⚠️ Common Mistakes

❌ Mixing class diagram with component diagram

❌ Showing internal methods

❌ Not separating frontend/backend

❌ Tight coupling between services

### 🔥 Best Practices

- Keep a high-level view

- Use API Gateway

- Use async communication (Kafka)

- Apply loose coupling

### 🧪 Practice (VERY IMPORTANT)

#### Design:

> 👉 Food Delivery System

#### Include:

- Auth Service

- Order Service

- Restaurant Service

- Delivery Service

- Payment Service

### 🎯 Simple Memory Trick

👉

- Class Diagram → Code structure

- Component Diagram → System structure

---

# 📄 Component Diagram – Symbols & Explanation

---

## 🧠 Overview

A Component Diagram uses **standard UML symbols** to represent:

* Components
* Interfaces
* Dependencies
* Ports
* Packages

---

# 🧩 1️⃣ Component

![Image](https://www.researchgate.net/publication/319493332/figure/fig5/AS%3A613973342834695%401523394060515/UML-component-diagram-notation-elements.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-component-diagram/02-component-diagram-overview.png)

![Image](https://www.ionos.com/digitalguide/fileadmin/_processed_/4/b/csm_EN-uml-component-diagram-1_3b80b7bfe6.webp)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-component-diagram/what-is-component-diagram.png)

### ✅ Symbol:

* Rectangle with **two small tabs** on the side

### 📌 Meaning:

Represents a **module or service**

### 💡 Examples:

* Angular Module
* Order Service
* API Gateway

---

### 💻 Code Mapping

```ts
// Order Service (Component)
@Injectable()
export class OrderService {}
```

---

# 🧩 2️⃣ Interface (Provided)

![Image](https://i.sstatic.net/ohJpv.png)

![Image](https://ducmanhphan.github.io/img/UML/interfaces/provided-%26%26-required-interfaces.png)

### ✅ Symbol:

* Small **circle (⚪)** → called *lollipop*

### 📌 Meaning:

What a component **provides to others**

---

### 💡 Example:

```
OrderService → createOrder()
```

---

# 🧩 3️⃣ Interface (Required)

![Image](https://i.sstatic.net/ohJpv.png)

![Image](https://i.sstatic.net/SCBTA.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-component-diagram/02-component-diagram-overview.png)

![Image](https://i.sstatic.net/o9e7J.png)

### ✅ Symbol:

* **Half-circle (socket)**

### 📌 Meaning:

What a component **needs from others**

---

### 💡 Example:

```
OrderService needs UserService
```

---

# 🧩 4️⃣ Dependency

![Image](https://www.uml-diagrams.org/dependency/dependency-overview.png)

![Image](https://i.sstatic.net/8epCX.png)

![Image](https://i.sstatic.net/YCegU.png)

![Image](https://i.sstatic.net/sLFw1.png)

### ✅ Symbol:

* Dashed arrow (`---->`)

### 📌 Meaning:

One component **uses another**

---

### 💡 Example:

```
Order Service ----> User Service
```

---

### 💻 Code Mapping

```ts
constructor(private userService: UserService) {}
```

---

# 🧩 5️⃣ Port

![Image](https://www.researchgate.net/publication/319493332/figure/fig5/AS%3A613973342834695%401523394060515/UML-component-diagram-notation-elements.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-component-diagram/02-component-diagram-overview.png)

![Image](https://www.uml-diagrams.org/component-diagrams/component-diagram-overview.png)

### ✅ Symbol:

* Small **square on component boundary**

### 📌 Meaning:

Entry/exit point of a component

---

### 💡 Example:

* API endpoint
* HTTP port

---

# 🧩 6️⃣ Package

![Image](https://images.ctfassets.net/w6r2i5d8q73s/1cOEhH3EmjyVRMnGpF0HFC/b5b170e2e2f820308cb5ad1ffdcab597/uml-package-diagram_hero_xxl_sub-use-case_img_EN?fm=webp\&q=75)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-package-diagram/02-simple-package-diagram-example.png)

![Image](https://www.uml-diagrams.org/package-diagrams/package-diagram-elements.png)

### ✅ Symbol:

* Folder-like shape 📁

### 📌 Meaning:

Groups related components

---

### 💡 Example:

* Microservices group
* Angular modules

---

# 🧩 7️⃣ Assembly Connector

![Image](https://i.sstatic.net/o9e7J.png)

![Image](https://www.uml-diagrams.org/component-diagrams/component-diagram-overview.png)

![Image](https://i.sstatic.net/ohJpv.png)

### ✅ Symbol:

* Circle (provided) connected to socket (required)

### 📌 Meaning:

Connects two components via interfaces

---

### 💡 Example:

```
Order Service ○───◖ User Service
```

---

# 🧠 Summary Table

| Symbol             | Meaning              |
| ------------------ | -------------------- |
| Component          | Module / Service     |
| Lollipop (⚪)       | Provided interface   |
| Socket (◖)         | Required interface   |
| Dashed Arrow       | Dependency           |
| Port (◻)           | Entry/Exit point     |
| Package (📁)       | Grouping             |
| Assembly Connector | Interface connection |

---

# 🎯 Simple Memory Trick

👉

* Box → Component
* Circle → Gives
* Socket → Needs
* Arrow → Uses

---
