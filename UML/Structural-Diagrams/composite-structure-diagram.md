# 🧠 What is a Composite Structure Diagram?

A **Composite Structure Diagram** shows:

* Internal structure of a class/component
* Parts (sub-objects)
* Ports (interaction points)
* Connectors (communication paths)

> 👉 Focus: **HOW a class/component is internally composed and interacts**

---

# 🎯 Purpose

* Model internal architecture
* Show object collaboration
* Define interaction points (ports)
* Design complex systems (microservices, MFEs)

---

# 🧩 Core Symbols

---

## 1️⃣ Structured Class

![Image](https://www.uml-diagrams.org/composite-structure-diagrams/composite-internal-structure-diagram-elements.png)

![Image](https://www.softwareideas.net/i/DirectImage/367/uml-composite-structure.png)

### ✅ Meaning:

* Main container (class/component)

---

## 2️⃣ Part (Internal Component)

![Image](https://sparxsystems.com/images/screenshots/uml2_tutorial/CP01.GIF)

![Image](https://www.uml-diagrams.org/composite-structure-diagrams/composite-internal-structure-diagram-elements.png)

![Image](https://www.visual-paradigm.com/VPGallery/img/diagrams/CompositeStructureDiagram/Composite-Structure-Diagram-Sample.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-component-diagram/02-component-diagram-overview.png)

### ✅ Meaning:

* Internal object inside class

---

## 3️⃣ Port

![Image](https://sparxsystems.com/images/screenshots/uml2_tutorial/CP01.GIF)

![Image](https://www.uml-diagrams.org/composite-structure-diagrams/composite-internal-structure-diagram-elements.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ADYajxj8Wv9-cwATbFfA6OQ.png)

### ✅ Meaning:

* Entry/exit point

---

## 4️⃣ Connector

![Image](https://www.uml-diagrams.org/composite-structure-diagrams/composite-internal-structure-diagram-elements.png)

![Image](https://www.visual-paradigm.com/VPGallery/img/diagrams/CompositeStructureDiagram/Composite-Structure-Diagram-Sample.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-composite-structure-diagram/03-class-diagram.png)

### ✅ Meaning:

* Communication between parts

---

## 5️⃣ Interface (Provided / Required)

* Same as component diagram
* Defines communication contract

---

# 🧩 Example Use Case (E-commerce Order Processing)

---

## 🧠 Scenario

> Order system internally uses:

* Payment Service
* Inventory Service
* Notification Service

---

## 🧩 Composite View

```
[ OrderProcessor ]
   ├── paymentService
   ├── inventoryService
   ├── notificationService

Ports:
   - createOrder()
   - processPayment()

Connections:
   Order → Payment → Inventory → Notification
```

---

# 💻 TypeScript Code Mapping

---

## 🧩 Interfaces (Ports)

```ts
export interface PaymentPort {
  processPayment(amount: number): boolean;
}

export interface InventoryPort {
  reserveStock(productId: string): boolean;
}

export interface NotificationPort {
  sendNotification(message: string): void;
}
```

---

## 🧩 Internal Parts

```ts
class PaymentService implements PaymentPort {
  processPayment(amount: number): boolean {
    console.log("Payment processed:", amount);
    return true;
  }
}

class InventoryService implements InventoryPort {
  reserveStock(productId: string): boolean {
    console.log("Stock reserved:", productId);
    return true;
  }
}

class NotificationService implements NotificationPort {
  sendNotification(message: string): void {
    console.log("Notification:", message);
  }
}
```

---

## 🧩 Structured Class

```ts
class OrderProcessor {
  constructor(
    private payment: PaymentPort,
    private inventory: InventoryPort,
    private notification: NotificationPort
  ) {}

  createOrder(productId: string, amount: number) {
    const stock = this.inventory.reserveStock(productId);
    if (!stock) return "Out of stock";

    const paid = this.payment.processPayment(amount);
    if (!paid) return "Payment failed";

    this.notification.sendNotification("Order placed");

    return "Order success";
  }
}
```

---

## 🧪 Usage

```ts
const orderProcessor = new OrderProcessor(
  new PaymentService(),
  new InventoryService(),
  new NotificationService()
);

orderProcessor.createOrder("p1", 500);
```

---

# 🧠 What This Represents

| UML Concept      | Code                        |
| ---------------- | --------------------------- |
| Structured Class | OrderProcessor              |
| Parts            | Services inside constructor |
| Ports            | Interfaces                  |
| Connectors       | Method calls                |

---

# 🔥 Real Architecture Mapping (IMPORTANT)

---

## 🧠 Angular

```
Component → Service → API
```

## 🧠 NestJS

```
Controller → Service → Other Services
```

---

# ⚠️ Common Mistakes

❌ Confusing with component diagram

❌ Not showing internal structure

❌ Missing ports

❌ Overcomplicating

---

# 🔥 Best Practices

* Use for **complex internal logic**
* Show only **important parts**
* Use interfaces as ports
* Keep diagram readable

---

# 🎯 Simple Memory Trick

👉

* Outside view → Component diagram
* Inside view → Composite diagram

---

# 🧪 Practice (VERY IMPORTANT)

Design composite diagram for:

👉 Food Delivery System

Include:

* OrderProcessor
* Payment
* Delivery
* Notification

---
