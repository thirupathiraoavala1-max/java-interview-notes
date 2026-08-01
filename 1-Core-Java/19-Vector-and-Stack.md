# 📚 Vector and Stack in Java

> 💡 **Vector** is a synchronized, dynamic array implementation of the **List** interface, while **Stack** is a subclass of Vector that follows the **LIFO (Last In, First Out)** principle.

---

# 🎯 Why Do We Need Vector & Stack?

Imagine a browser.

Every time you visit a page:

```
Google
   ↓
YouTube
   ↓
GitHub
   ↓
LinkedIn
```

When you click **Back**, the browser returns to the last visited page first.

This follows the **LIFO (Last In, First Out)** principle.

---

# 📚 What is Vector?

Vector is a dynamic array introduced in **Java 1.0**.

Unlike ArrayList, Vector is **thread-safe** because all its methods are synchronized.

---

# 🏗 Class Hierarchy

```text
                 Iterable
                     │
                     ▼
                Collection
                     │
                     ▼
                    List
                     │
                     ▼
                  Vector
                     │
                     ▼
                   Stack
```

---

# ✨ Features of Vector

- ✅ Dynamic Array
- ✅ Thread Safe
- ✅ Maintains Insertion Order
- ✅ Allows Duplicates
- ✅ Allows Multiple null Values
- ❌ Slower than ArrayList

---

# 🧠 Internal Working

Internally Vector stores elements in an array.

```text
Vector

+------+------+------+------+
|Java |Spring|Kafka |Docker |
+------+------+------+------+
```

When capacity is full,

Vector increases its size automatically.

---

# 📈 Capacity Growth

Default Capacity

```text
10
```

If capacityIncrement is not specified

```text
New Capacity = Old Capacity × 2
```

Example

```text
10 → 20 → 40 → 80
```

If capacityIncrement is specified

```java
Vector<Integer> vector = new Vector<>(10, 5);
```

Growth

```text
10 → 15 → 20 → 25
```

---

# 💻 Creating Vector

```java
Vector<String> vector = new Vector<>();
```

---

# 📥 Adding Elements

```java
vector.add("Java");
vector.add("Spring");
vector.add("Kafka");

System.out.println(vector);
```

Output

```text
[Java, Spring, Kafka]
```

---

# 📖 Reading Elements

```java
System.out.println(vector.get(1));
```

Output

```text
Spring
```

---

# ✏ Updating Elements

```java
vector.set(1, "Spring Boot");
```

Output

```text
[Java, Spring Boot, Kafka]
```

---

# ❌ Removing Elements

```java
vector.remove("Kafka");
```

Output

```text
[Java, Spring Boot]
```

---

# 🔒 Why is Vector Thread Safe?

All major methods are synchronized.

```java
public synchronized boolean add(E e)
```

Only one thread can modify the Vector at a time.

---

# 📚 What is Stack?

Stack is a subclass of Vector.

It follows the **LIFO (Last In, First Out)** principle.

```text
Last Inserted
      │
      ▼
+---------+
| GitHub  |
+---------+
| YouTube |
+---------+
| Google  |
+---------+

First Removed
```

---

# ✨ Features of Stack

- ✅ LIFO
- ✅ Thread Safe
- ✅ Dynamic Size
- ✅ Extends Vector

---

# 💻 Creating Stack

```java
Stack<String> stack = new Stack<>();
```

---

# 📥 push()

Adds an element to the top.

```java
stack.push("Java");
stack.push("Spring");
stack.push("Kafka");

System.out.println(stack);
```

Output

```text
[Java, Spring, Kafka]
```

---

# 📤 pop()

Removes the top element.

```java
System.out.println(stack.pop());
```

Output

```text
Kafka
```

---

# 👀 peek()

Returns the top element without removing it.

```java
System.out.println(stack.peek());
```

Output

```text
Spring
```

---

# 🔍 search()

Returns the position of an element.

```java
System.out.println(stack.search("Java"));
```

Output

```text
2
```

---

# 📊 Common Stack Methods

| Method | Description |
|---------|-------------|
| push() | Add element |
| pop() | Remove top element |
| peek() | View top element |
| empty() | Checks whether stack is empty |
| search() | Searches an element |

---

# ⚖ ArrayList vs Vector

| Feature | ArrayList | Vector |
|----------|-----------|--------|
| Thread Safe | ❌ No | ✅ Yes |
| Performance | Faster | Slower |
| Synchronization | No | Yes |
| Growth | 1.5x | 2x |

---

# ⚖ Stack vs Queue

| Stack | Queue |
|--------|-------|
| LIFO | FIFO |
| push() | offer() |
| pop() | poll() |
| peek() | peek() |

---

# 📊 Time Complexity

| Operation | Complexity |
|------------|------------|
| add() | O(1) |
| get() | O(1) |
| set() | O(1) |
| remove() | O(n) |
| push() | O(1) |
| pop() | O(1) |
| peek() | O(1) |

---

# 🌍 Real-World Examples

## 📚 Stack

- Browser Back Button
- Undo/Redo
- Function Call Stack
- Expression Evaluation

---

## 📦 Vector

- Legacy Applications
- Thread-safe Collections
- Shared Data Structures

---

# ⚠ Limitations

Vector

- Slower due to synchronization.
- Legacy class.
- Rarely used in modern applications.

Stack

- Legacy class.
- `Deque` is preferred for stack operations.

---

# 💡 Best Practices

✅ Use **ArrayList** instead of Vector unless thread safety is required.

✅ Use **ArrayDeque** instead of Stack in modern Java.

```java
Deque<Integer> stack = new ArrayDeque<>();
```

✅ Avoid unnecessary synchronization.

---

# ❓ Interview Questions

## 1️⃣ What is Vector?

A synchronized dynamic array implementation of the List interface.

---

## 2️⃣ Is Vector thread-safe?

✅ Yes.

All major methods are synchronized.

---

## 3️⃣ Difference between ArrayList and Vector?

- ArrayList is faster.
- Vector is synchronized.

---

## 4️⃣ What is Stack?

A LIFO data structure implemented as a subclass of Vector.

---

## 5️⃣ Difference between push() and add()?

- `push()` adds an element to the top of the stack.
- `add()` inserts an element into the collection.

---

## 6️⃣ Difference between pop() and peek()?

- `pop()` removes and returns the top element.
- `peek()` only returns the top element.

---

## 7️⃣ Is Stack thread-safe?

✅ Yes.

Because it extends Vector.

---

## 8️⃣ Why is Stack considered a legacy class?

Because modern Java recommends using **Deque (ArrayDeque)** for stack operations due to better performance.

---

## 9️⃣ What is the default capacity of Vector?

✅ 10

---

## 🔟 When should you use Vector?

Only when you need a thread-safe dynamic array in legacy applications.

---

# 📝 Summary

| Feature | Vector | Stack |
|----------|--------|-------|
| Data Structure | Dynamic Array | LIFO Stack |
| Thread Safe | ✅ Yes | ✅ Yes |
| Ordered | ✅ Yes | ✅ Yes |
| Duplicates | ✅ Yes | ✅ Yes |
| Null Values | ✅ Yes | ✅ Yes |
| Legacy Class | ✅ Yes | ✅ Yes |
| Modern Alternative | CopyOnWriteArrayList | ArrayDeque |

---

# 🎯 Key Takeaway

> **Vector** is a synchronized version of **ArrayList**, making it suitable for legacy thread-safe applications. **Stack**, built on top of Vector, implements the **LIFO** principle and is commonly used for operations like **undo/redo**, **browser history**, and **function call management**. In modern Java, prefer **ArrayDeque** for stack operations because it offers better performance and cleaner design.