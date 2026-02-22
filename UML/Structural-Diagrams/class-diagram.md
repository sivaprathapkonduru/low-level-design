## 🧠 1. What is a Class Diagram?

- It is a static diagram

- Shows structure of the system

- Represents:

    - Classes

    - Attributes

    - Methods

    - Relationships

👉 It is the **BACKBONE of OOP and LLD**

## 🏗 2. Basic Structure of a Class

#### Diagram for shapes

![class diagram for shapes](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/18-uml-class-diagram-example-gui.png)

#### Diagram for pet adoption

![pet adopt image](https://substackcdn.com/image/fetch/%24s_%21lMAf%21%2Cf_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F72d3654b-44b5-4708-a634-527534bd0937_3772x3040.png)

### Format:

| ClassName |
| ---------- |
| `-` attributes <br> `+` **name: string**(public) <br> `-` **age: int**(private) <br> `#` **mobile: tel**(protected) <br> `~` **capitalizer: package**(local package)|
| `+` **methods**(**in** **id**: number, **out** ) |


### Operations Visibility (or) Access modifiers:

- `+` Public
- `-` Private
- `#` Protected
- `~` Local Package

### Parameter directionality:

| Kind |	Meaning |	Example |
| --------- | -------- | -------- |
| in	| **Input**: Passed to method, unchanged	| +borrowBook(**in** isbn: String)
| out	| **Output**: Modified by method, returned	| +generateTicket(**out** ticketId: String)
| inout |	**Both**: Input + modified output	| +updateSpot(**inout** spot: ParkingSpot)

## ex:-

### I. Library System (Your Day 1)

>
<pre> class LibraryService {
  +borrowBook(
    **in** memberId: string,      // Member scans card (input)
    **in** isbn: string,          // Book barcode (input)
    **out** ticketId: string      // Generated ticket (output)
  ): boolean
}</pre>
> 

### II. Parking Lot (FAANG Classic)
>
<pre> class ParkingLot {
  +parkVehicle(
    **in** licensePlate: string,  // Vehicle ID (input)
    **out** spotId: string,       // Assigned spot (output)
    **inout** vehicle: Vehicle    // Vehicle gets spot assigned (modified)
  ): boolean
}</pre>
>

### III. Payment Processing (Microservices)

<pre>class PaymentService {
  +processPayment(
    **in** orderId: string,       // Order details (input)
    **inout** payment: Payment    // Status updated: pending→success (modified)
  ): TransactionId
}</pre>

### IV. User Authentication
>
<pre>class AuthService {
  +login(
    **in** username: string,      // Credentials (input)
    **in** password: string,      // Credentials (input)
    **out** token: string,        // JWT token (output)
    **out** user: User            // User profile (output)
  ): boolean
}</pre>
>

### V. Database Operations
>
<pre>class UserRepository {
  +updateUser(
    **in** userId: string,        // Filter (input)
    **inout** user: User          // Full user object updated (input+output)
  ): void
}</pre>
>

### PlantUML Syntax
>
<pre>class LibraryService {
  +borrowBook(in memberId: string, in isbn: string, out ticketId: string): boolean
}</pre>

## 🧩 3. Class Diagram Elements (FULL CONTENT)
### 🔹 1. Class
Represents blueprint of objects

| User |
| ------ |
| `-` id: string <br> `#` name: string |
|`+` login() |

### 🔹 2. Object

👉 Instance of class

> user1: User

### 🔹 3. Attributes

👉 Properties of class

`-` name: string <br>
`-` price: number

### 🔹 4. Methods

👉 Behavior

`+` placeOrder()
`+` calculateTotal()

### 🔹 5. Relationships (MOST IMPORTANT)
## 🔗 Types of Relationships

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681758292817/626beabf-0a36-42c8-beff-d163c30de8a7.png)
![](https://miro.medium.com/v2/0*OcXwbrcD2oInENr6.jpg)

### 1️⃣ Association

![](https://media.geeksforgeeks.org/wp-content/uploads/20250828094904229784/file.webp)

👉 Simple connection

> User → Order


✔ Represented by line

✔ Can have multiplicity

#### Code:- 
<pre>
class Product {
  constructor(
    public id: string,
    public name: string,
    public price: number
  ) {}
}

class Menu {
  constructor(public products: Product[]) {}
}

class Restaurant {
  constructor(
    public id: string,
    public name: string,
    public menu: Menu // association
  ) {}
}
</pre>

### 2️⃣ Multiplicity (Cardinality)
#### Examples:

| Notation | Meaning | Example |
| --------- | -------- | ------- |
|1 | Exactly one | A Person has exactly one SSN. |
| `0..1` | Zero or one (Optional) | A User may or may not have a MiddleName. |
| `*` | Zero or many | A Customer can have many Orders. |
| `1..*` | One or many (At least one) | A Team must have at least one Player. |
| `n` | Specific number | A Car has exactly 4 Wheels. |
| `m..n` | A specific range | A Player in a game has 3 to 5 Lives.|

#### 1. One to one relationship (1:1)
#### 🧠 What is 1:1 Association?

One object is related to exactly one other object

**Examples:**

- User ↔ Profile

- Person ↔ Passport

- Student ↔ IDCard

**One item** is connected to **only one other item**,
and **that item is also connected to only one in return**.

It is represented using an arrow(⇢,⇠)(There can be many notations possible for the ER diagram).

**Example:**

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101160601/Untitleddrawing26-660x131.png)

In this ER diagram, both entities customer and driving license having an arrow which means the entity Customer is participating in the relation "has a" in a one-to-one fashion. It could be read as 'Each customer has exactly one driving license and every driving license is associated with exactly one customer.

**The set-theoretic perspective of the ER diagram is**

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101160618/Untitleddrawing27-300x208.png)

There may be customers who do not have a credit card, but every credit card is associated with exactly one customer. Therefore, the entity customer has total participation in a relation.

#### Code:- (User ↔ Profile)

👉 Pure association (both exist independently)

<pre>
class Profile {
  constructor(
    public bio: string,
    public avatar: string
  ) {}
}

class User {
  constructor(
    public id: string,
    public name: string,
    public profile: Profile // 1:1 association
  ) {}
}

// usage
const profile = new Profile("Developer", "avatar.png");
const user = new User("u1", "Siva", profile);
</pre>

✔ One user → one profile

✔ Profile can exist independently

#### Bidirectional 1:1 (Both know each other)
<pre>
class User {
  public profile!: Profile;

  constructor(public id: string) {}
}

class Profile {
  constructor(
    public bio: string,
    public user: User
  ) {}
}

// linking
const user = new User("u1");
const profile = new Profile("Developer", user);

user.profile = profile;
</pre>

✔ Both sides reference each other

✔ Used in ORM (TypeORM, Prisma)

#### Optional 1:1 (0..1)

👉 User MAY have profile
<pre>
class Profile {
  constructor(public bio: string) {}
}

class User {
  constructor(
    public id: string,
    public profile?: Profile // optional
  ) {}
}

const user = new User("u1"); // no profile yet
</pre>

✔ UML: 0..1

#### Strong Ownership (Composition 1:1)

👉 Profile cannot exist without User
<pre>
class Profile {
  constructor(public bio: string) {}
}

class User {
  public profile: Profile;

  constructor(public id: string, bio: string) {
    this.profile = new Profile(bio); // created inside
  }
}
</pre>

✔ Strong lifecycle dependency

✔ UML → Composition (filled diamond)

#### Real-World Example (Passport System)
<pre>
class Passport {
  constructor(
    public number: string,
    public country: string
  ) {}
}

class Person {
  constructor(
    public name: string,
    public passport: Passport // 1:1
  ) {}
}

// usage
const passport = new Passport("A12345", "India");
const person = new Person("Siva", passport);
</pre>
#### 2. One to many relationship (1:M)

#### 🧠 What is 1 : M?

One object is related to many objects

**Examples:**

- User → Orders

- Customer → Addresses

- Restaurant → MenuItems

**One item** is connected to **many items**,
but each of those **many items is connected to only that one**.

**Example:**

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101160634/Untitleddrawing31-660x255.png)

This relationship is one to many because "There are some employees who manage more than one team while there is only one manager to manage a team".

**The set-theoretic perspective of the ER diagram is:**

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101161342/Untitleddrawing28300x225-200x150.png)

#### Code:-
#### Basic Example (User → Orders)

👉 One User can have many Orders
<pre>
class Order {
  constructor(public id: string) {}
}

class User {
  public orders: Order[] = []; // 1:M

  constructor(public id: string, public name: string) {}

  addOrder(order: Order) {
    this.orders.push(order);
  }
}

// usage
const user = new User("u1", "Siva");

user.addOrder(new Order("o1"));
user.addOrder(new Order("o2"));
</pre>

✔ One user → many orders

✔ Orders exist independently

#### Bidirectional (1:M + M:1)

👉 Real-world systems usually use both sides
<pre>
class User {
  public orders: Order[] = [];

  constructor(public id: string) {}

  addOrder(order: Order) {
    this.orders.push(order);
    order.user = this; // link both sides
  }
}

class Order {
  public user!: User;

  constructor(public id: string) {}
}
</pre>

✔ User knows orders

✔ Order knows user

#### Optional (0..*)

👉 User may have zero or many orders
<pre>
class User {
  public orders: Order[] = []; // 0..*
}
</pre>

✔ Default case in most systems

#### Strong Ownership (Composition 1:M)

👉 OrderItems belong to Order
<pre>
class OrderItem {
  constructor(public name: string) {}
}

class Order {
  private items: OrderItem[] = [];

  addItem(name: string) {
    const item = new OrderItem(name); // created inside
    this.items.push(item);
  }
}
</pre>

✔ Items cannot exist without Order

✔ Composition + 1:M

#### Real Example (E-commerce)
<pre>
class Product {
  constructor(public name: string, public price: number) {}
}

class OrderItem {
  constructor(
    public product: Product,
    public quantity: number
  ) {}
}

class Order {
  public items: OrderItem[] = []; // 1:M

  addItem(product: Product, quantity: number) {
    this.items.push(new OrderItem(product, quantity));
  }
}</pre>

#### Direction matters:
| Direction |	Meaning |
| ----- | ----- |
| 1 → M |	Parent holds array |
| M → 1 |	Child holds reference |
| Both |	Bidirectional |

#### 3. Many to one relationship (M:1)
#### 🧠 What is M : 1?

Many objects are related to one object

**Examples:**

- Many Orders → One User

- Many Employees → One Department

- Many Products → One Category

**Many items** from one group are connected to **just one item in another group**.

**Example:**

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101161358/Untitleddrawing32-660x144.png)

This is a **one-to-many** relationship, but the difference comes from who must participate .The set-theoretic perspective of the ER diagram is:

- A customer can have many credit cards, but some customers might not have any. So, customer participation is partial.
- Every credit card must be linked to one customer. So, credit card participation is total.
- Also, a credit card belongs to only one customer — it cannot be shared by multiple customers.

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101161414/Untitleddrawing29-300x221.png)

#### Code:-
#### Basic Example (Order → User)

👉 Many Orders belong to ONE User

<pre>class User {
  constructor(public id: string, public name: string) {}
}

class Order {
  constructor(
    public id: string,
    public user: User // M:1
  ) {}
}

// usage
const user = new User("u1", "Siva");

const order1 = new Order("o1", user);
const order2 = new Order("o2", user);
</pre>

✔ Many orders → same user

✔ Order holds reference

#### Bidirectional (Best Practice)

👉 Combine with 1:M

<pre>class User {
  public orders: Order[] = [];

  constructor(public id: string) {}

  addOrder(order: Order) {
    this.orders.push(order);
    order.user = this;
  }
}

class Order {
  public user!: User;

  constructor(public id: string) {}
}
</pre>

✔ User → orders (1:M)

✔ Order → user (M:1)

👉 This is how real systems work

#### Optional (0..1)

👉 Order MAY have user (rare but possible)

<pre>class Order {
  constructor(
    public id: string,
    public user?: User // optional
  ) {}
}
</pre>

✔ UML: 0..1

#### Real Example (Company)
<pre>class Department {
  constructor(public name: string) {}
}

class Employee {
  constructor(
    public name: string,
    public department: Department // M:1
  ) {}
}

// usage
const dept = new Department("Engineering");

const emp1 = new Employee("A", dept);
const emp2 = new Employee("B", dept);
</pre>

✔ Many employees → one department

#### Real Example (E-commerce — your domain)
<pre>class User {
  constructor(public id: string) {}
}

class Order {
  constructor(
    public id: string,
    public user: User // M:1
  ) {}
}
</pre>

### 4. Many to many relationship (M:N)
#### 🧠 What is M : N?

>Many objects relate to many objects

**Examples:**

- Students ↔ Courses

- Orders ↔ Products

- Users ↔ Roles

**One entity** in the first set can be related to **many entities** in the second set,
and **One entity** in the second set can also be related to **many entities** in the first set.

**Example:**

A customer can buy any number of products and a product can be bought by many customers. 

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101161515/Untitleddrawing34-660x260-(1).png)

The set-theoretic perspective of the ER diagram is:

![](https://media.geeksforgeeks.org/wp-content/uploads/20231101161533/Untitleddrawing30-300x223-(1).png)

Any of the four cardinalities of a binary relationship can have both sides partial, both total, and one partial, and one total participation, depending on the constraints specified by user requirements.

#### Code:- 
#### ❌ WRONG WAY (Beginner Mistake)
<pre>class Student {
  courses: Course[] = [];
}

class Course {
  students: Student[] = [];
}
</pre>

👉 Looks correct but ❌ NOT scalable

👉 You cannot store extra data (marks, enrollment date)

#### ✅ CORRECT WAY (Senior Approach)

> 👉 Use JOIN CLASS (Association Class)

##### Example (Student ↔ Course)
<pre>class Student {
  constructor(public id: string, public name: string) {}
}

class Course {
  constructor(public id: string, public title: string) {}
}</pre>

##### // 🔥 JOIN CLASS
<pre>class Enrollment {
  constructor(
    public student: Student,
    public course: Course,
    public enrolledAt: Date,
    public marks?: number
  ) {}
}
</pre>

✔ This represents M:N properly

✔ You can store extra attributes

#### Real Example (E-commerce — Order ↔ Product)
<pre>class Product {
  constructor(
    public id: string,
    public name: string,
    public price: number
  ) {}
}

class Order {
  public items: OrderItem[] = [];

  constructor(public id: string) {}

  addProduct(product: Product, quantity: number) {
    this.items.push(new OrderItem(this, product, quantity));
  }
}</pre>

##### // 🔥 JOIN ENTITY
<pre>class OrderItem {
  constructor(
    public order: Order,
    public product: Product,
    public quantity: number
  ) {}

  getTotal(): number {
    return this.product.price * this.quantity;
  }
}
</pre>

✔ Order ↔ Product = M:N

✔ OrderItem resolves it

#### 🧠 Why JOIN CLASS is IMPORTANT

Because in real systems you need:

| Scenario |	Example |
| ------- | ------ |
| Extra data |	quantity, price |
| Tracking |	timestamps |
| Business logic |	discounts |

> 👉 Direct M:N cannot handle this ❌

#### Real Example (User ↔ Role)
<pre>class User {
  constructor(public id: string) {}
}

class Role {
  constructor(public name: string) {}
}

class UserRole {
  constructor(
    public user: User,
    public role: Role,
    public assignedAt: Date
  ) {}
}</pre>

##### 🧠 DB Mapping (VERY IMPORTANT)
<pre>User
Role
UserRole (JOIN TABLE)</pre>

##### 👉 Same as:

<pre>order_items
enrollments
user_roles</pre>

#### ⚠️ Common Mistakes

❌ Direct array-to-array mapping

❌ No join entity

❌ Ignoring extra attributes

❌ Confusing with 1:M

#### 🧠 Memory Trick

> 👉 M:N = Needs third class ALWAYS

### 3️⃣ Aggregation (Weak HAS-A)

![](https://media.geeksforgeeks.org/wp-content/uploads/20190930035513/Aggregation.jpeg)

👉 Whole–part (independent)

> Team → Player

✔ Hollow diamond
#### Code:- (Restaurant has Products indirectly)
<pre>
class FoodPlatform {
  constructor(public restaurants: Restaurant[]) {}
}
</pre>
✔ Restaurants exist independently → aggregation

### 4️⃣ Composition (Strong HAS-A)

![](https://media.geeksforgeeks.org/wp-content/uploads/20190930035511/Aggregation-1.jpeg)

👉 Strong ownership

> Order → OrderItem


✔ Filled diamond <br>
✔ Child dies with parent
#### Code:-
<pre>
class OrderItem {
  constructor(
    public product: Product,
    public quantity: number
  ) {}

  getTotal(): number {
    return this.product.price * this.quantity;
  }
}

class Order {
  private items: OrderItem[] = []; // composition
  public status: OrderStatus = OrderStatus.CREATED;

  constructor(
    public id: string,
    public customer: Customer
  ) {}

  addItem(product: Product, quantity: number) {
    const item = new OrderItem(product, quantity);
    this.items.push(item);
  }

  getTotalAmount(): number {
    return this.items.reduce((sum, item) => sum + item.getTotal(), 0);
  }
}
</pre>

### 5️⃣ Inheritance (Generalization) 
![](https://media.geeksforgeeks.org/wp-content/uploads/20240308165524/Class-Diagram-example.webp)

👉 IS-A relationship

> Admin → User

✔ Triangle arrow

#### code:- 

<pre>
class User {
  constructor(
    public id: string,
    public name: string,
    public email: string
  ) {}

  login() {
    console.log(`${this.name} logged in`);
  }
}

class Customer extends User {
  placeOrder(order: Order) {
    console.log(`${this.name} placed order ${order.id}`);
  }
}

class DeliveryPartner extends User {
  deliverOrder(order: Order) {
    console.log(`Delivering order ${order.id}`);
  }
}
</pre>

### 6️⃣ Dependency

![](https://miro.medium.com/v2/0*OcXwbrcD2oInENr6.jpg)

👉 Uses temporarily

> OrderService → PaymentService

✔ Dashed arrow
#### Code:- (Service uses Payment)
<pre>
class PaymentService {
  processPayment(
    amount: number,
    method: PaymentMethod
  ): PaymentStatus {
    return method.pay(amount);
  }
}

class OrderService {
  constructor(private paymentService: PaymentService) {}

  checkout(order: Order, method: PaymentMethod) {
    const amount = order.getTotalAmount();
    const status = this.paymentService.processPayment(amount, method);

    if (status === PaymentStatus.SUCCESS) {
      order.status = OrderStatus.CONFIRMED;
    }
  }
}
</pre>

### 7️⃣ Realization

![](https://media.geeksforgeeks.org/wp-content/uploads/20250829165046859312/realization.webp)

👉 Interface implementation

> Payment → PaymentMethod

✔ Dashed + triangle

#### Code:- 
<pre>
interface PaymentMethod {
  pay(amount: number): PaymentStatus;
}

class UPIPayment implements PaymentMethod {
  pay(amount: number): PaymentStatus {
    console.log("Paid via UPI:", amount);
    return PaymentStatus.SUCCESS;
  }
}

class CardPayment implements PaymentMethod {
  pay(amount: number): PaymentStatus {
    console.log("Paid via Card:", amount);
    return PaymentStatus.SUCCESS;
  }
}

</pre>

## 🧠 5. Advanced Concepts (from your PDF)
### 🔹 Association Class 

👉 Relationship with attributes

<pre>Example:

Student --- Enrollment --- Course</pre>

### 🔹 Qualified Association

👉 Reduce many-to-many

### 🔹 Enumeration 

![](https://www.softwareideas.net/i/DirectImage/1685/an-enumeration-associated-with-a-class-uml-class-diagram-)

<pre>enum OrderStatus {
  CREATED, PAID, SHIPPED
}</pre>

Code:-
<pre>
enum OrderStatus {
  CREATED = "CREATED",
  CONFIRMED = "CONFIRMED",
  PREPARING = "PREPARING",
  OUT_FOR_DELIVERY = "OUT_FOR_DELIVERY",
  DELIVERED = "DELIVERED"
}

enum PaymentStatus {
  PENDING = "PENDING",
  SUCCESS = "SUCCESS",
  FAILED = "FAILED"
}
</pre>

### 🔹 Abstract Class 

<pre><< abstract >>
Payment</pre>

### 🔹 Package

👉 Group of classes

### 🔹 Ordering / Sequence / Bag 

- Ordered collection

- Unordered collection

- Duplicates allowed

## 🧠 FINAL MAPPING (VERY IMPORTANT)
| UML Concept	| TypeScript |
| ---- | ---- |
| Class	| class |
| Attribute |	properties |
| Method |	functions |
| Inheritance |	extends |
| Realization |	implements |
| Association |	object reference |
| Aggregation |	injected reference |
| Composition |	created inside class |
| Dependency |	method parameter / service |

## 🏢 6. Real Example (E-commerce — Full Understanding)
<pre>
User
 ├── Cart
 │    └── CartItem
 │         └── Product
 └── Order
      └── OrderItem
           └── Product
      └── Payment

</pre>

#### Relationships:
<pre>
User → Order (1:N)

Order → OrderItem (Composition)

OrderItem → Product (Association)

Payment → PaymentMethod (Realization)
</pre>

## 🎯 7. When to Use Class Diagram

From your PDF + real world:

<pre>
✔ System design (LLD)
✔ Database design mapping
✔ API modeling
✔ Microservices contracts
</pre>

## ⚠️ 8. Common Mistakes (VERY IMPORTANT)

<pre>
❌ Too many fields in one class
❌ Missing relationships
❌ Using inheritance everywhere
❌ Mixing DB schema with UML
❌ No methods (only data)
</pre>

## 🧪 9. Interview-Level Answer (memorize this)

>Class diagram is a static UML diagram that represents the structure of a system using classes, their attributes, methods, and relationships such as association, inheritance, aggregation, and composition. It is mainly used for low-level design and object-oriented modeling.

## 🚀 10. Your Next Step (based on your level)

#### Now you should:

👉 Draw a complete class diagram for:

#### 🔥 Food Delivery System

Include:

- User
- Restaurant
- Menu
- Order
- Payment
- Delivery
