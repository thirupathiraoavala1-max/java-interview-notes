# 📋 ArrayList in Java

> 💡 **ArrayList** is a resizable array implementation of the **List** interface in the Java Collections Framework. It maintains insertion order, allows duplicate elements, and provides fast random access.

---

# 🎯 Why Do We Need ArrayList?

Imagine an E-Commerce application.

Users continuously add products to their cart.

```text
🛒 Cart

+ Laptop
+ Mouse
+ Keyboard
+ Mobile
```

The number of products is unknown.

❌ Arrays have fixed size.

✅ ArrayList grows automatically.

---

# 📚 What is ArrayList?

ArrayList is a dynamic array.

It automatically increases its capacity whenever required.

```java
List<String> list = new ArrayList<>();
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
                  List
                    │
                    ▼
               ArrayList
```

---

# ✨ Features

- ✅ Dynamic Size
- ✅ Maintains Insertion Order
- ✅ Allows Duplicate Elements
- ✅ Allows Multiple null Values
- ✅ Fast Random Access
- ❌ Slow Insert/Delete in Middle

---

# 🧠 Internal Working

Internally ArrayList uses

```java
Object[]
```

When capacity becomes full,

it creates a larger array and copies existing elements.

---

# 📦 Internal Structure

```text
ArrayList

Index

0 → Java
1 → Spring
2 → Kafka
3 → Docker
4 → AWS
```

---

# 📈 Growth of ArrayList

Default Capacity

```text
10
```

When full

```text
Old Capacity = 10

New Capacity = 10 + (10/2)

              = 15
```

Formula

```text
New Capacity = Old Capacity + (Old Capacity / 2)
```

Approximately **1.5x growth**.

---

# 💻 Creating ArrayList

```java
List<String> list = new ArrayList<>();
```

---

# 📥 Adding Elements

```java
list.add("Java");
list.add("Spring");
list.add("Kafka");
```

Output

```text
[Java, Spring, Kafka]
```

---

# 📖 Reading Elements

```java
System.out.println(list.get(1));
```

Output

```text
Spring
```

---

# ✏ Updating Elements

```java
list.set(1, "Spring Boot");
```

Output

```text
[Java, Spring Boot, Kafka]
```

---

# ❌ Removing Elements

```java
list.remove("Kafka");
```

Output

```text
[Java, Spring Boot]
```

---

# 🔍 Searching Elements

```java
list.contains("Java");
```

Output

```text
true
```

---

# 🔄 Iterating ArrayList

### Using Enhanced For Loop

```java
for(String language : list){

    System.out.println(language);

}
```

---

### Using Iterator

```java
Iterator<String> iterator = list.iterator();

while(iterator.hasNext()){

    System.out.println(iterator.next());

}
```

---

### Using Stream API

```java
list.stream()

    .forEach(System.out::println);
```

---

# 📊 Time Complexity

| Operation | Complexity |
|------------|------------|
| add() (End) | O(1) |
| add(Index) | O(n) |
| get() | O(1) |
| set() | O(1) |
| contains() | O(n) |
| remove() | O(n) |
| size() | O(1) |

---

# 📌 Common Methods

| Method | Description |
|----------|-------------|
| add() | Adds element |
| add(index,obj) | Adds at index |
| get() | Returns element |
| set() | Updates element |
| remove() | Removes element |
| contains() | Searches element |
| clear() | Removes all elements |
| size() | Returns size |
| isEmpty() | Checks empty |
| indexOf() | Returns index |

---

# 🌍 Real-World Example

Imagine a movie playlist.

```text
🎬 Playlist

1. Avengers
2. Batman
3. Iron Man
4. Spider-Man
```

Movies are added in order.

Duplicates are allowed.

Perfect use case for **ArrayList**.

---

# ⚖ Array vs ArrayList

| Array | ArrayList |
|---------|-----------|
| Fixed Size | Dynamic Size |
| Stores primitives & objects | Stores objects only |
| No built-in methods | Rich API |
| Manual resizing | Automatic resizing |

---

# ⚖ ArrayList vs LinkedList

| ArrayList | LinkedList |
|------------|------------|
| Dynamic Array | Doubly Linked List |
| Fast Random Access | Slow Random Access |
| Slow Insert/Delete | Fast Insert/Delete |
| Less Memory | More Memory |

---

# 📊 Memory Representation

```text
Heap Memory

+-------+-------+-------+-------+
| Java  |Spring |Kafka  |Docker |
+-------+-------+-------+-------+
     0       1      2       3
```

---

# ⚠ Limitations

- Insertions in middle are expensive.
- Deletions require shifting elements.
- Not synchronized.
- Not suitable for frequent modifications.

---

# 💡 Best Practices

✅ Use ArrayList when read operations are more frequent.

✅ Specify initial capacity if size is known.

```java
new ArrayList<>(100);
```

✅ Prefer `List` reference.

```java
List<String> list = new ArrayList<>();
```

✅ Use Generics.

```java
List<Employee> employees = new ArrayList<>();
```

---

# ❓ Interview Questions

## 1️⃣ What is ArrayList?

A resizable array implementation of the List interface.

---

## 2️⃣ Does ArrayList allow duplicates?

✅ Yes.

---

## 3️⃣ Does ArrayList maintain insertion order?

✅ Yes.

---

## 4️⃣ Can ArrayList store null values?

✅ Yes.

It allows multiple null values.

---

## 5️⃣ What is the default capacity?

✅ **10** (when the first element is added in modern JDKs).

---

## 6️⃣ How does ArrayList grow?

Approximately **1.5 times** its current capacity.

---

## 7️⃣ Why is get() O(1)?

Because elements are stored in contiguous memory and can be accessed using their index.

---

## 8️⃣ Why is insertion in the middle O(n)?

Because all subsequent elements must be shifted.

---

## 9️⃣ Is ArrayList thread-safe?

❌ No.

Use:

- `Collections.synchronizedList()`
- `CopyOnWriteArrayList`

when thread safety is required.

---

## 🔟 When should you use ArrayList?

When:

- Read operations are frequent.
- Insertions/removals mostly happen at the end.
- Random access is important.

---

# 📝 Summary

| Feature | ArrayList |
|----------|-----------|
| Data Structure | Dynamic Array |
| Ordered | ✅ Yes |
| Duplicates | ✅ Yes |
| Null Values | ✅ Yes |
| Thread Safe | ❌ No |
| Random Access | ⭐ Excellent |
| Insert/Delete Middle | ❌ Slow |

---

# 🎯 Key Takeaway

> **ArrayList** is the best choice when your application requires **fast random access**, maintains **insertion order**, and primarily performs **read operations**. It is one of the most commonly used collection classes in Java and a favorite topic in Java backend interviews.