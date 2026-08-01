# 🔗 LinkedHashSet in Java

> 💡 **LinkedHashSet** is an implementation of the **Set** interface that stores **unique elements** while maintaining **insertion order**. It is backed by a **LinkedHashMap**, combining the fast lookup of a hash table with the ordering of a linked list.

---

# 🎯 Why Do We Need LinkedHashSet?

Imagine an online shopping application.

Recently searched products:

```text
Laptop
Mouse
Keyboard
Monitor
```

Requirements:

- ✅ No duplicate products
- ✅ Preserve the search order

HashSet removes duplicates but **doesn't preserve order**.

LinkedHashSet solves this problem.

---

# 📚 What is LinkedHashSet?

LinkedHashSet is an ordered version of HashSet.

It:

- Stores unique elements
- Maintains insertion order
- Allows one null value
- Uses LinkedHashMap internally

```java
Set<String> set = new LinkedHashSet<>();
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
                   │
                   ▼
            LinkedHashSet
```

---

# ✨ Features

- ✅ Maintains Insertion Order
- ✅ No Duplicate Elements
- ✅ Allows One null
- ✅ Fast Lookup
- ❌ Not Sorted
- ❌ Not Thread Safe

---

# 🧠 Internal Working

LinkedHashSet internally uses **LinkedHashMap**.

Each entry stores:

- Key
- Hash
- Previous Node
- Next Node

This doubly linked list preserves insertion order.

---

# 🏗 Internal Architecture

```text
LinkedHashSet
      │
      ▼
LinkedHashMap
      │
      ▼

Head

Java ⇄ Spring ⇄ Kafka ⇄ Docker

Tail
```

---

# 💻 Creating LinkedHashSet

```java
Set<String> set = new LinkedHashSet<>();
```

---

# 📥 Adding Elements

```java
set.add("Java");
set.add("Spring");
set.add("Kafka");
set.add("Docker");

System.out.println(set);
```

Output

```text
[Java, Spring, Kafka, Docker]
```

Order is preserved.

---

# ❌ Duplicate Elements

```java
set.add("Java");
set.add("Java");
set.add("Spring");

System.out.println(set);
```

Output

```text
[Java, Spring]
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

Only one null value is allowed.

---

# 🔍 Searching

```java
System.out.println(set.contains("Kafka"));
```

Output

```text
true
```

---

# ❌ Removing

```java
set.remove("Spring");
```

Output

```text
[Java, Kafka, Docker]
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
| iteration | O(n) |

---

# 📌 Common Methods

| Method | Description |
|---------|-------------|
| add() | Adds an element |
| remove() | Removes an element |
| contains() | Checks existence |
| size() | Returns size |
| clear() | Removes all elements |
| iterator() | Iterates elements |

---

# ⚖ HashSet vs LinkedHashSet

| Feature | HashSet | LinkedHashSet |
|----------|----------|---------------|
| Order | ❌ No | ✅ Yes |
| Duplicates | ❌ No | ❌ No |
| Null | One | One |
| Internal DS | HashMap | LinkedHashMap |
| Performance | Slightly Faster | Slightly Slower |
| Memory | Less | More |

---

# ⚖ LinkedHashSet vs TreeSet

| LinkedHashSet | TreeSet |
|---------------|----------|
| Maintains Insertion Order | Maintains Sorted Order |
| O(1) Operations | O(log n) Operations |
| Allows One null | Does Not Allow null |
| Uses LinkedHashMap | Uses TreeMap |

---

# 🌍 Real-World Examples

Use LinkedHashSet for:

- 📜 Browser History
- 🛒 Recently Viewed Products
- 🎵 Playlist
- 📂 Recent Files
- 📰 News Feed History

---

# 📊 Memory Representation

```text
Head

 ▼
Java ⇄ Spring ⇄ Kafka ⇄ Docker

 ▲
Tail
```

Each node is connected using previous and next references.

---

# ⚠ Limitations

- Slightly slower than HashSet.
- More memory due to linked list.
- Not sorted.
- Not thread-safe.

---

# 💡 Best Practices

✅ Use LinkedHashSet when insertion order matters.

✅ Use HashSet if order is not required.

✅ Use TreeSet if sorted order is required.

---

# ❓ Interview Questions

## 1️⃣ What is LinkedHashSet?

A Set implementation that maintains insertion order using LinkedHashMap.

---

## 2️⃣ Does LinkedHashSet allow duplicates?

❌ No.

---

## 3️⃣ Does LinkedHashSet maintain insertion order?

✅ Yes.

---

## 4️⃣ Does LinkedHashSet allow null?

✅ Yes.

Only one null value.

---

## 5️⃣ Is LinkedHashSet sorted?

❌ No.

It preserves insertion order, not sorted order.

---

## 6️⃣ What is the internal data structure?

✅ LinkedHashMap.

---

## 7️⃣ Difference between HashSet and LinkedHashSet?

HashSet does not maintain order, while LinkedHashSet preserves insertion order.

---

## 8️⃣ Is LinkedHashSet thread-safe?

❌ No.

---

## 9️⃣ Why is LinkedHashSet slower than HashSet?

Because it maintains a doubly linked list in addition to the hash table.

---

## 🔟 When should you use LinkedHashSet?

When:

- Duplicate elements are not allowed.
- Insertion order must be preserved.
- Fast lookup is required.

---

# 📝 Summary

| Feature | LinkedHashSet |
|----------|---------------|
| Data Structure | Hash Table + Doubly Linked List |
| Ordered | ✅ Insertion Order |
| Sorted | ❌ No |
| Duplicates | ❌ No |
| Null | ✅ One |
| Thread Safe | ❌ No |
| Internal DS | LinkedHashMap |
| Search | ⭐ O(1) |

---

# 🎯 Key Takeaway

> **LinkedHashSet** combines the speed of **HashSet** with the predictable iteration order of a **LinkedHashMap**. It is the ideal choice when you need **unique elements** while preserving **insertion order**, making it useful for browser history, playlists, recent files, and many backend applications.