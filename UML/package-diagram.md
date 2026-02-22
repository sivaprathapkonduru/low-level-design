# 🧠 What is a Package Diagram?

A **Package Diagram** is a UML diagram that shows:

* How classes/components are **grouped**
* Dependencies between **packages (modules)**
* High-level **code organization**

> 👉 Focus: **How your codebase is structured**

---

# 🎯 Purpose

* Organize large systems
* Show module boundaries
* Improve maintainability
* Define dependency direction
* Represent layered architecture

---

# 🧩 Basic Package Structure

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-package-diagram/02-simple-package-diagram-example.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-package-diagram/07-package-diagram-layered-application.png)

![Image](https://online.visual-paradigm.com/repository/images/65e92382-98d6-4066-bd1d-660475ee8ccb.png)

![Image](https://www.visual-paradigm.com/servlet/editor-content/guide/uml-unified-modeling-language/modeling-software-architecture-with-package/sites/7/2019/12/package-diagram-explained.png)

![](https://res.cloudinary.com/dnazyivn1/image/upload/v1771596182/Screenshot_2026-02-20_at_7.27.52_PM_ir9zvb.png)

![](https://res.cloudinary.com/dnazyivn1/image/upload/v1771596303/Screenshot_2026-02-20_at_7.34.21_PM_sz2r8o.png)

![](https://res.cloudinary.com/dnazyivn1/image/upload/v1771596393/Screenshot_2026-02-20_at_7.35.52_PM_kpj0z0.png)

---

## 🧠 Example

```
[ Controller ] → [ Service ] → [ Repository ] → [ Database ]
```

---

# 🧩 UML Symbols

---

## 1️⃣ Package

### ✅ Symbol:

* Folder-like shape 📁

### 📌 Meaning:

Group of related classes/modules

---

### 💡 Example:

```
📁 user
📁 order
📁 payment
```

---

## 2️⃣ Dependency

### ✅ Symbol:

* Dashed arrow (`---->`)

### 📌 Meaning:

One package depends on another

---

### 💡 Example:

```
Controller ----> Service
```

---

## 3️⃣ Nested Package

### ✅ Symbol:

* Package inside another package

### 📌 Meaning:

Hierarchy / submodules

---

---

# 🧩 Real Architecture (Your Stack 🔥)

---

## 🧠 Backend (NestJS)

```
📁 order
   ├── controller
   ├── service
   ├── repository
   ├── dto
   ├── entity
```

---

## 🧠 Frontend (Angular)

```
📁 app
   ├── core
   ├── shared
   ├── features
        ├── order
        ├── user
```

---

# 💻 Code Mapping (VERY IMPORTANT)

---

## 🧩 1️⃣ Package → Folder

```
src/order/
```

---

## 🧩 2️⃣ Inside Package

---

### Controller

```ts
// order.controller.ts
@Controller('orders')
export class OrderController {}
```

---

### Service

```ts
// order.service.ts
@Injectable()
export class OrderService {}
```

---

### Repository

```ts
// order.repository.ts
@Injectable()
export class OrderRepository {}
```

---

### Entity

```ts
// order.entity.ts
export class Order {
  id: string;
}
```

---

# 🔗 Package Dependency Example

---

## 🧠 Flow

```
📁 order.controller
      ↓
📁 order.service
      ↓
📁 order.repository
```

---

## 💻 Code

```ts
// controller → service
constructor(private orderService: OrderService) {}
```

```ts
// service → repository
constructor(private repo: OrderRepository) {}
```

---

# 🧩 Angular Package Example

---

## Structure

```
📁 order-feature
   ├── components
   ├── services
   ├── models
```

---

## Code

```ts
// order.service.ts
@Injectable({ providedIn: 'root' })
export class OrderService {}
```

---

# 🧠 Layered Architecture (IMPORTANT)

---

## Clean Architecture

```
📁 presentation (controllers)
📁 application (services)
📁 domain (entities)
📁 infrastructure (db/repo)
```

---

## Rule:

```
Outer → Inner only
```

✔ Controller → Service
✔ Service → Repository
❌ Repository → Controller

---

# ⚠️ Common Mistakes

❌ Circular dependencies
❌ Mixing layers
❌ No clear structure
❌ Too many packages

---

# 🔥 Best Practices

* Keep packages **cohesive**
* Follow **single responsibility**
* Avoid circular dependencies
* Use layered architecture

---

# 🎯 Simple Memory Trick

👉

* Package = Folder
* Arrow = Dependency
* Layers = Architecture

---

# 🧪 Practice

Design package diagram for:

👉 Food Delivery App

Include:

* Auth
* Order
* Payment
* Delivery

---
