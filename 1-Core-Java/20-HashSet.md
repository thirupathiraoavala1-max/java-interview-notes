# 🌳 HashSet in Java

> 💡 **HashSet** is an implementation of the **Set** interface that stores **unique elements** using a **HashMap** internally. It does **not maintain insertion order** and provides **constant-time performance** for basic operations.

---

# 🎯 Why Do We Need HashSet?

Imagine an online course registration system.

Students register using their email IDs.

```text
john@gmail.com
alice@gmail.com
john@gmail.com ❌ Duplicate
```

The system should store each email only once.

✅ HashSet automatically removes duplicates.

---

# 📚 What is HashSet?

HashSet is a collection that:

- Stores unique elements
- Does not maintain insertion order
- Allows one null value
- Uses HashMap internally

```java
Set<String> set = new HashSet<>();
```

---

# 🏗 Class Hierarchy

```text
                Iterable
                    │
                    ▼
               Collection
                    │
                    ▼
                   Set
                    │
                    ▼
                 HashSet
```

---

# ✨ Features

- ✅ Unique Elements
- ✅ Fast Search
- ✅ Fast Insertion
- ✅ Allows One null
- ❌ No Insertion Order
- ❌ Not Thread Safe

---

# 🧠 Internal Working

HashSet internally uses a **HashMap**.

Whenever we write

```java
set.add("Java");
```

Internally Java performs

```java
map.put("Java", PRESENT);
```

where

```java
private static final Object PRESENT = new Object();
```

Only the **key** matters.

The value is always a dummy object.

---

# 🏗 Internal Architecture

```text
              HashSet
                  │
                  ▼
             HashMap
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
      Key              Dummy Value
    "Java"             PRESENT
   "Spring"            PRESENT
    "Kafka"            PRESENT
```

---

# 💻 Creating HashSet

```java
Set<String> set = new HashSet<>();
```

---

# 📥 Adding Elements

```java
set.add("Java");
set.add("Spring");
set.add("Kafka");
```

Output

```text
[Java, Spring, Kafka]
```

*(Order may vary.)*

---

# ❌ Duplicate Elements

```java
set.add("Java");
set.add("Java");
set.add("Java");
```

Output

```text
[Java]
```

Duplicates are ignored.

---

# ❌ Null Values

```java
set.add(null);
set.add(null);

System.out.println(set);
```

Output

```text
[null]
```

Only **one null** is allowed.

---

# 🔍 Searching

```java
System.out.println(set.contains("Spring"));
```

Output

```text
true
```

---

# ❌ Removing

```java
set.remove("Kafka");
```

---

# 🔄 Iterating

### Enhanced For Loop

```java
for(String language : set){

    System.out.println(language);

}
```

---

### Iterator

```java
Iterator<String> iterator = set.iterator();

while(iterator.hasNext()){

    System.out.println(iterator.next());

}
```

---

# 📊 Time Complexity

| Operation | Complexity |
|------------|------------|
| add() | O(1) |
| remove() | O(1) |
| contains() | O(1) |
| size() | O(1) |
| iteration | O(n) |

> ⚠️ Worst case can become **O(n)** if many hash collisions occur.

---

# 📌 Common Methods

| Method | Description |
|----------|-------------|
| add() | Adds an element |
| remove() | Removes an element |
| contains() | Searches an element |
| size() | Returns size |
| clear() | Removes all elements |
| isEmpty() | Checks if empty |

---

# ⚖ HashSet vs ArrayList

| HashSet | ArrayList |
|----------|-----------|
| No Duplicates | Allows Duplicates |
| Unordered | Ordered |
| O(1) Search | O(n) Search |
| Backed by HashMap | Dynamic Array |

---

# ⚖ HashSet vs LinkedHashSet

| HashSet | LinkedHashSet |
|----------|---------------|
| No Order | Maintains Insertion Order |
| Faster | Slightly Slower |
| Less Memory | More Memory |

---

# ⚖ HashSet vs TreeSet

| HashSet | TreeSet |
|----------|---------|
| Unordered | Sorted |
| O(1) | O(log n) |
| Allows one null | Does not allow null |

---

# 🌍 Real-World Examples

Use HashSet for:

- ✅ Unique Email IDs
- ✅ Employee IDs
- ✅ Usernames
- ✅ Product Codes
- ✅ Tags
- ✅ Permission Lists

---

# 📊 Memory Representation

```text
HashSet

        │
        ▼

+----------------------+
|      HashMap         |
+----------------------+
| Java   → PRESENT     |
| Spring → PRESENT     |
| Kafka  → PRESENT     |
+----------------------+
```

---

# ⚠ Limitations

- Does not maintain insertion order.
- Cannot access elements using an index.
- Not synchronized.
- Iteration order is unpredictable.

---

# 💡 Best Practices

✅ Use HashSet when uniqueness is required.

✅ Override `equals()` and `hashCode()` for custom objects.

✅ Prefer LinkedHashSet if insertion order matters.

✅ Prefer TreeSet if sorted order is required.

---

# ❓ Interview Questions

## 1️⃣ What is HashSet?

A Set implementation backed by a HashMap that stores unique elements.

---

## 2️⃣ Does HashSet allow duplicates?

❌ No.

---

## 3️⃣ Does HashSet maintain insertion order?

❌ No.

---

## 4️⃣ Does HashSet allow null?

✅ Yes.

Only one null element.

---

## 5️⃣ Is HashSet synchronized?

❌ No.

---

## 6️⃣ How does HashSet remove duplicates?

Using `hashCode()` and `equals()` methods.

---

## 7️⃣ Why is HashSet fast?

Because it uses hashing, enabling average-case O(1) operations.

---

## 8️⃣ What is stored as the value in the internal HashMap?

A dummy object named:

```java
PRESENT
```

---

## 9️⃣ Can HashSet store custom objects?

✅ Yes.

But you should override `equals()` and `hashCode()`.

---

## 🔟 When should you use HashSet?

When:

- Duplicate elements are not allowed.
- Fast search is required.
- Order is not important.

---

# 💻 Example with Custom Object

```java
class Employee {

    int id;

    Employee(int id){

        this.id = id;

    }

    @Override
    public boolean equals(Object obj){

        if(this == obj)
            return true;

        if(!(obj instanceof Employee))
            return false;

        Employee emp = (Employee)obj;

        return id == emp.id;

    }

    @Override
    public int hashCode(){

        return Integer.hashCode(id);

    }

}
```

---

# 📝 Summary

| Feature | HashSet |
|----------|---------|
| Data Structure | Hash Table |
| Ordered | ❌ No |
| Duplicates | ❌ No |
| Null Allowed | ✅ One |
| Thread Safe | ❌ No |
| Search | ⭐ O(1) |
| Internal DS | HashMap |

---

# 🎯 Key Takeaway

> **HashSet** is the best choice when you need **fast lookups** and **unique elements**. It achieves high performance by using a **HashMap** internally, making `add()`, `remove()`, and `contains()` operations efficient. Understanding its relationship with `HashMap`, along with `hashCode()` and `equals()`, is essential for Java backend interviews.