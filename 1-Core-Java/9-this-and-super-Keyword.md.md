# 🔑 this and super Keyword in Java

> 💡 **`this`** and **`super`** are special reference keywords in Java.
>
> - **`this`** refers to the **current object**.
> - **`super`** refers to the **parent class object**.

---

# 🎯 Why Do We Need `this` and `super`?

Consider the following example:

```java
class Employee {

    String name;

    Employee(String name) {

        name = name;

    }

}
```

Here, both the local variable and instance variable have the same name.

❌ The instance variable is **not initialized**.

To solve this problem, Java provides the **`this` keyword**.

Similarly, when we want to access members of the parent class, Java provides the **`super` keyword**.

---

# 📚 Overview

| Keyword | Refers To | Used For |
|----------|-----------|----------|
| 🔹 `this` | Current Object | Access current class members |
| 🔸 `super` | Parent Object | Access parent class members |

---

# 🔹 `this` Keyword

## 📖 Definition

The `this` keyword refers to the **current object** of the class.

---

# 🛠️ Uses of `this`

```text
🔹 this Keyword
        │
 ┌──────┼────────┬────────┬────────┐
 ▼      ▼        ▼        ▼
Current Constructor Method Return Object
Object  Call      Call    Reference
```

---

# 1️⃣ Access Current Class Variables

```java
class Employee {

    String name;

    Employee(String name) {

        this.name = name;

    }

}
```

✅ `this.name` → Instance variable

✅ `name` → Local variable

---

# 2️⃣ Call Current Class Method

```java
class Employee {

    void display() {

        this.show();

    }

    void show() {

        System.out.println("Hello Java");

    }

}
```

---

# 3️⃣ Call Another Constructor

```java
class Employee {

    Employee() {

        this("John");

    }

    Employee(String name) {

        System.out.println(name);

    }

}
```

### Output

```text
John
```

---

# 4️⃣ Return Current Object

```java
class Employee {

    Employee getEmployee() {

        return this;

    }

}
```

---

# 🌍 Real-World Example

Imagine you introduce yourself.

> "I am John."

Here, **"I"** refers to yourself.

Similarly,

`this`

refers to the current object.

---

# 🔸 `super` Keyword

## 📖 Definition

The `super` keyword refers to the **parent class object**.

---

# 🛠️ Uses of `super`

```text
🔸 super Keyword
         │
 ┌───────┼─────────┬─────────┐
 ▼       ▼         ▼
Parent Constructor Parent
Variable Call      Method
```

---

# 1️⃣ Access Parent Class Variable

```java
class Animal {

    String color = "White";

}

class Dog extends Animal {

    String color = "Black";

    void printColor() {

        System.out.println(super.color);

    }

}
```

### Output

```text
White
```

---

# 2️⃣ Call Parent Class Method

```java
class Animal {

    void sound() {

        System.out.println("Animal Sound");

    }

}

class Dog extends Animal {

    void sound() {

        super.sound();

        System.out.println("Dog Bark");

    }

}
```

### Output

```text
Animal Sound
Dog Bark
```

---

# 3️⃣ Call Parent Constructor

```java
class Animal {

    Animal() {

        System.out.println("Animal Constructor");

    }

}

class Dog extends Animal {

    Dog() {

        super();

        System.out.println("Dog Constructor");

    }

}
```

### Output

```text
Animal Constructor
Dog Constructor
```

---

# 📊 Constructor Execution Flow

```text
new Dog()
    │
    ▼
super()
    │
    ▼
Parent Constructor
    │
    ▼
Child Constructor
```

---

# ⚖️ this vs super

| Feature | `this` | `super` |
|----------|---------|----------|
| Refers To | Current Object | Parent Object |
| Access Variables | ✅ Yes | ✅ Yes |
| Access Methods | ✅ Yes | ✅ Yes |
| Constructor Call | `this()` | `super()` |
| Used in Inheritance | ❌ Not Required | ✅ Yes |

---

# 🌍 Real-World Analogy

Imagine a family.

👨 Father → `super`

👦 Son → `this`

The son can:

- Access his own belongings → `this`
- Access his father's belongings → `super`

---

# 💻 Complete Example

```java
class Animal {

    String type = "Animal";

    Animal() {

        System.out.println("Animal Constructor");

    }

    void display() {

        System.out.println("Animal Method");

    }

}

class Dog extends Animal {

    String type = "Dog";

    Dog() {

        super();

    }

    void show() {

        System.out.println(this.type);

        System.out.println(super.type);

        this.display();

        super.display();

    }

}
```

---

# ❓ Interview Questions

## 1️⃣ What is the `this` keyword?

`this` refers to the current object of the class.

---

## 2️⃣ What is the `super` keyword?

`super` refers to the parent class object.

---

## 3️⃣ Can `this()` and `super()` be used together?

❌ No.

Both must be the **first statement** in a constructor, so only one can be used.

---

## 4️⃣ Can we use `this` inside a static method?

❌ No.

Static methods belong to the class, not to an object.

---

## 5️⃣ What happens if we don't write `super()`?

The compiler automatically inserts `super()` as the first statement in the constructor (if the parent has a no-argument constructor).

---

# 💡 Best Practices

✅ Use `this` to avoid variable shadowing.

✅ Use `super` only when accessing parent members.

✅ Prefer method overriding instead of directly calling parent methods unless necessary.

✅ Keep constructor chaining simple.

---

# 📝 Summary

| Keyword | Purpose |
|----------|----------|
| 🔹 `this` | Refers to the current object |
| 🔸 `super` | Refers to the parent object |
| `this()` | Calls another constructor in the same class |
| `super()` | Calls the parent class constructor |

---

# 🎯 Key Takeaway

> The **`this` keyword** is used to work with the **current object**, while the **`super` keyword** is used to access **parent class members**. Mastering these keywords is essential for understanding **constructors, inheritance, method overriding, and object-oriented programming** in Java.