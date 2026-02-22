# 🧠 What is an Object Diagram?

An Object Diagram is a UML diagram that shows instances of classes (objects) and their relationships at a specific point in time.

> Object Diagram = Snapshot of real objects at runtime

👉 While Class Diagram = blueprint

👉 Object Diagram = actual instance data

#### 🎯 Purpose:-

- Visualize real data (runtime state)

- Validate class diagram design

- Understand object relationships

- Debug system behavior

- Represent test scenarios

### 🆚 Class Diagram vs Object Diagram
| Feature	| Class Diagram	| Object Diagram |
| ----  | ---- | ---- |
| Level	Design | (Blueprint)	| Runtime (Instance) |
| Shows |	Classes |	Objects |
| Data |	No real values |	Real values |
| Time |	Static |	Snapshot at a specific time |

> Object diagrams are instance-level representations of class diagrams

### 🧱 Structure of Object Diagram
<pre>
+----------------------+
| objectName:ClassName |
+----------------------+
| attribute = value    |
| attribute = value    |
+----------------------+
</pre>

## 🎯 WHY we need Object Diagram (VERY IMPORTANT)

### 1️⃣ To Visualize REAL DATA

![](https://cdn-images.visual-paradigm.com/guide/uml/what-is-object-diagram/03-class-diagram-to-object-diagram.png)

![](https://cs111.wellesley.edu/archive/cs111_fall97/public_html/lectures/ObjectDiagrams/object-diagrams11.gif)

#### Example:

##### Class Diagram:

> User → Order


##### Object Diagram:

> User: {name: "Siva"} <br> Order: {id: "o1"}

✔ Shows actual values

✔ Helps understand real execution

### 2️⃣ To VALIDATE Class Diagram Design

👉 Before coding, you check:

- Does relationship make sense?
    ##### ✅ Example (Correct)
        User → Order

    ✔ A user places orders → makes sense

    ❌ Example (Wrong)

        User → Engine

    ❌ No logical connection

- Are cardinalities correct?

    👉 “How many objects can be related?”

    **Common Types:**
        
        | Type |       Meaning   |
        | ---- | --------------- |
        | 1:1  |    One to one   |
        | 1:M  |	One to many  |
        | M:N  |	Many to many |

    ✅ Example (Correct)

    > User 1 → * Orders


    ✔ One user can have many orders

    ❌ Example (Wrong)
    > User 1 → 1 Order

    ❌ Too restrictive

- Are objects connected properly?

    👉 “At runtime, are objects actually linked correctly?”

    ✅ Correct Object Diagram

            const user = new User("u1", "Siva");

            const order1 = new Order("o1", 100);
            const order2 = new Order("o2", 200);

            user.addOrder(order1);
            user.addOrder(order2);


    > ✔ user → [order1, order2]

    ❌ Wrong Case

        const user = new User("u1", "Siva");
        const order = new Order("o1", 100);

    // forgot to link ❌

    👉 No connection → design fails

## 🧩 Elements of Object Diagram
### 1️⃣ Object (Instance)

- Represents real instance of a class

- Format:

    > user1: User

### 2️⃣ Attributes with Values

- Shows actual runtime values

        name = "Siva"
        id = "u1"

### 3️⃣ Link (Connection)

- Represents relationship between objects

- Instance of association

## 🧪 Example (User → Order)

#### Class Diagram
        class User {
        id: string;
        name: string;
        orders: Order[];
        }

        class Order {
        id: string;
        amount: number;
        }

#### Object Diagram
        user1: User
        id = "u1"
        name = "Siva"

        order1: Order
        id = "o1"
        amount = 100

        order2: Order
        id = "o2"
        amount = 200

        Links:
        user1 → order1
        user1 → order2

### 🧠 Key Characteristics

- Shows real instances

- Captures system state at a moment

- Displays actual values

- Represents links (relationships)

> It acts like a “screenshot of system memory”

### 🔁 How to Create Object Diagram

- Start from Class Diagram

- Create instances (objects)

- Assign real values

- Connect objects using links

- Validate relationships

### ✅ Validation Checklist (VERY IMPORTANT)

Before finalizing:

- ✔ Does relationship make sense?

- ✔ Are cardinalities correct?

- ✔ Are objects connected properly?

### 🧠 Example Scenarios
1️⃣ Single User with Multiple Orders
user1 → order1, order2

2️⃣ Multiple Users
user1 → order1
user2 → order2

3️⃣ Edge Case (No Orders)
user1 → []

### ⚠️ When to Use
| Scenario |	Use Object Diagram |
|-- | --- |
| Debugging |	✅ Yes |
| Complex relationships |	✅ Yes |
| Interviews |	⭐ Very useful |
| Simple CRUD |	❌ Not needed |

### 🚫 Common Mistakes 

- ❌ Adding classes instead of objects

- ❌ Not assigning values

- ❌ Missing links

- ❌ Overloading with too many objects

## Class Diagram Reference:-
[Class Diagram Reference](https://github.com/sivaprathapkonduru/low-level-design/blob/main/UML/class-diagram.md)
