# 📦 Collections Framework in Java

> 💡 The **Java Collections Framework (JCF)** is a unified architecture that provides a set of interfaces, implementations, and algorithms to efficiently store, retrieve, manipulate, and process groups of objects.

---

# 🎯 Why Do We Need Collections?

Imagine developing an **E-Commerce Application**.

You need to manage:

- 👥 Customers
- 📦 Products
- 🛒 Orders
- 💳 Transactions

Using arrays has limitations:

- ❌ Fixed Size
- ❌ Difficult Insert/Delete Operations
- ❌ No Built-in Searching or Sorting

The **Collections Framework** solves these problems by providing dynamic and efficient data structures.

---

# 📚 What is the Collections Framework?

The Java Collections Framework consists of:

- 📌 Interfaces
- 📌 Classes
- 📌 Utility Algorithms

It helps developers manage collections of objects efficiently.

---

# 🏗️ Collection Framework Hierarchy

```text
                            Iterable
                                │
                                ▼
                           Collection
      ┌─────────────────────────┼─────────────────────────┐
      ▼                         ▼                         ▼
     List                      Set                      Queue
      │                         │                         │
      ▼                         ▼                         ▼
 ArrayList                  HashSet               PriorityQueue
 LinkedList             LinkedHashSet             ArrayDeque
 Vector                     TreeSet
 Stack

                             Map
                              │
      ┌───────────────┬───────────────┬─────────────────┐
      ▼               ▼               ▼                 ▼
   HashMap      LinkedHashMap      TreeMap        Hashtable
                                                ConcurrentHashMap
```

> 📌 **Map is not part of the Collection interface**, but it is an important part of the Java Collections Framework.

---

# 📊 Collection Interfaces

| Interface | Description |
|------------|-------------|
| 📋 List | Ordered collection, allows duplicates |
| 🧩 Set | Unique elements, no duplicates |
| 📬 Queue | FIFO (First In, First Out) |
| 🗂️ Map | Stores key-value pairs |

---

# 📋 List Interface

### Features

- Maintains insertion order
- Allows duplicate elements
- Allows multiple null values

### Implementations

- ArrayList
- LinkedList
- Vector
- Stack

---

### Example

```java
List<String> names = new ArrayList<>();

names.add("Java");
names.add("Spring");
names.add("Java");

System.out.println(names);
```

Output

```text
[Java, Spring, Java]
```

---

# 🧩 Set Interface

### Features

- Does NOT allow duplicates
- May or may not maintain insertion order (depends on implementation)

### Implementations

- HashSet
- LinkedHashSet
- TreeSet

---

### Example

```java
Set<String> languages = new HashSet<>();

languages.add("Java");
languages.add("Spring");
languages.add("Java");

System.out.println(languages);
```

Output

```text
[Java, Spring]
```

---

# 📬 Queue Interface

### Features

- FIFO (First In, First Out)
- Used for task scheduling and messaging

### Implementations

- PriorityQueue
- ArrayDeque

---

### Example

```java
Queue<Integer> queue = new LinkedList<>();

queue.offer(10);
queue.offer(20);

System.out.println(queue.poll());
```

Output

```text
10
```

---

# 🗂️ Map Interface

### Features

- Stores key-value pairs
- Keys are unique
- Values can be duplicated

### Implementations

- HashMap
- LinkedHashMap
- TreeMap
- Hashtable
- ConcurrentHashMap

---

### Example

```java
Map<Integer, String> map = new HashMap<>();

map.put(101, "John");
map.put(102, "Alice");

System.out.println(map);
```

Output

```text
{101=John, 102=Alice}
```

---

# 📊 Collection Comparison

| Collection | Order | Duplicates | Null Allowed |
|-------------|:-----:|:----------:|:------------:|
| List | ✅ | ✅ | ✅ |
| Set | Depends | ❌ | Depends |
| Queue | FIFO | ✅ | Depends |
| Map (Keys) | Depends | ❌ | Depends |

---

# ⚖️ Array vs Collection

| Array | Collection |
|--------|------------|
| Fixed Size | Dynamic Size |
| Stores primitives & objects | Stores objects only |
| No built-in algorithms | Rich API |
| Manual resizing | Automatic resizing |

---

# ⚡ Utility Class - Collections

The `Collections` class provides utility methods.

### Sorting

```java
Collections.sort(list);
```

---

### Reverse

```java
Collections.reverse(list);
```

---

### Shuffle

```java
Collections.shuffle(list);
```

---

### Binary Search

```java
Collections.binarySearch(list, "Java");
```

---

# 🔄 Iterator

Iterator is used to traverse collections.

```java
Iterator<String> iterator = list.iterator();

while(iterator.hasNext()) {

    System.out.println(iterator.next());

}
```

---

# 📊 Iterable → Collection → Map

```text
Iterable
    │
    ▼
Collection
    │
 ┌──┼──────────────┐
 ▼  ▼              ▼
List Set         Queue

Map (Separate Hierarchy)
```

---

# 🌍 Real-World Example

Imagine a Library.

📚 List → Books on a Shelf (duplicates allowed)

🎟️ Set → Unique Membership IDs

🧾 Queue → Students waiting to borrow books

🗂️ Map → Book ID → Book Details

---

# ❓ Interview Questions

## 1️⃣ What is the Java Collections Framework?

A framework that provides interfaces and classes to store and manipulate groups of objects efficiently.

---

## 2️⃣ Why do we use Collections instead of Arrays?

Collections are dynamic, provide built-in algorithms, and support efficient insertion, deletion, searching, and sorting.

---

## 3️⃣ Difference between Collection and Collections?

| Collection | Collections |
|-------------|-------------|
| Interface | Utility Class |
| Represents data structures | Provides helper methods |

---

## 4️⃣ Is Map part of the Collection interface?

❌ No.

Map is a separate hierarchy in the Java Collections Framework.

---

## 5️⃣ Which Collection allows duplicates?

✅ List

---

## 6️⃣ Which Collection does not allow duplicates?

✅ Set

---

## 7️⃣ Which Collection maintains insertion order?

- ArrayList
- LinkedList
- LinkedHashSet
- LinkedHashMap

---

## 8️⃣ Which Collection sorts elements automatically?

- TreeSet
- TreeMap

---

# 💡 Best Practices

✅ Use `ArrayList` for frequent read operations.

✅ Use `LinkedList` for frequent insertions and deletions.

✅ Use `HashSet` for uniqueness.

✅ Use `HashMap` for fast key-value lookups.

✅ Use `TreeMap` or `TreeSet` when sorted data is required.

---

# 📝 Summary

| Interface | Popular Implementations |
|------------|-------------------------|
| 📋 List | ArrayList, LinkedList, Vector, Stack |
| 🧩 Set | HashSet, LinkedHashSet, TreeSet |
| 📬 Queue | PriorityQueue, ArrayDeque |
| 🗂️ Map | HashMap, LinkedHashMap, TreeMap, Hashtable, ConcurrentHashMap |

---

# 🎯 Key Takeaway

> The **Java Collections Framework** provides powerful data structures and algorithms to efficiently manage groups of objects. Understanding the hierarchy, interfaces, implementations, and their use cases is essential for writing high-performance Java applications and excelling in Java backend interviews.