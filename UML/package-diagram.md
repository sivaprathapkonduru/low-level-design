# 🧠 What is a Package Diagram?

A **Package Diagram** is a UML diagram that shows:

* How classes/components are **grouped**
* Dependencies between **packages (modules)**
* High-level **code organization**

> 👉 Focus: **How your codebase is structured**

A **Package Diagram** organizes system elements into **logical groups** and defines:

* Dependencies
* Access rules
* Visibility
* Architecture layers

> 👉 Focus: **Modularity + Dependency Control**

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

![](https://res.cloudinary.com/dnazyivn1/image/upload/v1771784953/Screenshot_2026-02-22_at_11.58.32_PM_ppom0t.png)

![](https://res.cloudinary.com/dnazyivn1/image/upload/v1771785311/Screenshot_2026-02-23_at_12.04.40_AM_ygpfgn.png)

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

# 🎯 Why Advanced Concepts Matter

* Prevent tight coupling
* Enforce clean architecture
* Control access between modules
* Improve scalability

---

# 🧩 1️⃣ Package Stereotypes

![Image](https://i.sstatic.net/vwFak.gif)

![Image](https://www.uml-diagrams.org/examples/package-diagrams-example-layers.png)

![Image](https://cdn-images.visual-paradigm.com/tutorials/howtocreatestereotypedmodelelement_screenshots/00-stereotyped-shapes.png)

![Image](https://www.visual-paradigm.com/servlet/editor-content/guide/uml-unified-modeling-language/modeling-software-architecture-with-package/sites/7/2019/12/package-diagram-explained.png)

---

## 🧠 What is a Stereotype?

> Adds **semantic meaning** to a package

---

## ✅ Common Stereotypes

| Stereotype       | Meaning          |
| ---------------- | ---------------- |
| `<<controller>>` | Handles requests |
| `<<service>>`    | Business logic   |
| `<<repository>>` | Data access      |
| `<<entity>>`     | Domain model     |
| `<<utility>>`    | Shared helpers   |

---

## 💻 Code Mapping (NestJS)

```ts
// <<controller>>
@Controller('orders')
export class OrderController {}
```

```ts
// <<service>>
@Injectable()
export class OrderService {}
```

```ts
// <<repository>>
@Injectable()
export class OrderRepository {}
```

---

# 🧩 2️⃣ Package Import vs Access

---

## 🧠 Import (<<import>>)

![Image](https://www.softwareideas.net/i/DirectImage/365/uml-package-diagram)

![Image](https://www.uml-diagrams.org/package-diagrams/package-diagram-elements.png)

---

### ✅ Meaning:

* Import all public elements
* Full visibility

---

### 💻 Code Mapping

```ts
import { OrderService } from '../order/order.service';
```

✔ Full access

---

---

## 🧠 Access (<<access>>)

![Image](https://www.softwareideas.net/i/DirectImage/365/uml-package-diagram)

![Image](https://www.visual-paradigm.com/servlet/editor-content/guide/uml-unified-modeling-language/modeling-software-architecture-with-package/sites/7/2019/12/package-diagram-explained.png)

![Image](https://www.uml-diagrams.org/package-diagrams/model-diagram-elements.png)

![Image](https://cdn-images.visual-paradigm.com/guide/uml/what-is-package-diagram/02-simple-package-diagram-example.png)

---

### ✅ Meaning:

* Limited / controlled access
* Only specific elements

---

### 💻 Code Mapping

```ts
// Access only via interface
import { IOrderService } from '../order/interfaces';
```

✔ Restricted access

---

# ⚔️ Import vs Access

| Feature    | Import       | Access           |
| ---------- | ------------ | ---------------- |
| Visibility | Full         | Limited          |
| Usage      | Direct usage | Controlled usage |
| Coupling   | Higher       | Lower            |

---

# 🧩 3️⃣ Access Modifiers (Visibility)

---

## 🧠 UML Symbols

| Symbol | Meaning   |
| ------ | --------- |
| `+`    | Public    |
| `-`    | Private   |
| `#`    | Protected |
| `~`    | Package   |

---

## 💻 TypeScript Mapping

```ts
class User {
  public name: string;     // +
  private password: string; // -
  protected role: string;  // #
}
```

---

## 🧠 Package-Level Visibility

```ts
// Not exported → package-private
class InternalService {}
```

```ts
// Exported → public
export class PublicService {}
```

---

# 🧩 4️⃣ Dependency Direction (VERY IMPORTANT)

![Image](https://i.sstatic.net/32gQH.jpg)

![Image](https://www.uml-diagrams.org/examples/package-diagrams-example-layers.png)

![Image](https://i.sstatic.net/3WOuu.jpg)

![Image](https://www.visual-paradigm.com/servlet/editor-content/guide/uml-unified-modeling-language/modeling-software-architecture-with-package/sites/7/2019/12/package-diagram-explained.png)

---

## 🧠 Rule:

```
Outer → Inner only
```

---

## Example:

```
Controller → Service → Repository → Entity
```

✔ Allowed
❌ Reverse dependency

---

# 🧩 5️⃣ Layered Package Architecture

---

## 🧠 Clean Architecture

```
📁 presentation <<controller>>
📁 application <<service>>
📁 domain <<entity>>
📁 infrastructure <<repository>>
```

---

## 💻 Example Structure

```id="pkg1"
src/
 ├── presentation/
 ├── application/
 ├── domain/
 ├── infrastructure/
```

---

# 🧩 6️⃣ Real Example (Your Stack 🔥)

---

## 🧠 Package Diagram (Logical)

```
📁 order <<module>>
   ├── <<controller>>
   ├── <<service>>
   ├── <<repository>>
   ├── <<entity>>
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

# ⚠️ Common Mistakes

❌ Circular dependencies

❌ Exposing everything (no encapsulation)

❌ Ignoring access modifiers

❌ Mixing layers

---

# 🔥 Best Practices

* Use **interfaces for access control**
* Keep packages **independent**
* Follow **dependency direction rule**
* Apply **stereotypes clearly**

---

# 🧠 Senior-Level Insight

> Advanced package diagrams enforce architectural boundaries by controlling visibility, dependencies, and access, ensuring scalable and maintainable systems.

---

# 🎯 Simple Memory Trick

👉

* `<< >>` = meaning
* import = full access
* access = limited
* arrows = dependency

---

# 🧪 Practice (VERY IMPORTANT)

Design:

👉 E-commerce package diagram with:

* User
* Order
* Payment

Include:

* stereotypes
* import/access
* access modifiers

---
