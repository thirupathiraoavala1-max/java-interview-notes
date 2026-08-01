# 🔗 LinkedList in Java

> 💡 **LinkedList** is a doubly linked list implementation of the **List** and **Deque** interfaces in the Java Collections Framework. It provides efficient insertion and deletion operations while maintaining insertion order.

---

# 🎯 Why Do We Need LinkedList?

Imagine a music playlist.

```text
🎵 Playlist

Song 1
Song 2
Song 3
Song 4
```

Users frequently:

- ➕ Add songs
- ❌ Remove songs
- 🔄 Reorder songs

Using an ArrayList requires shifting elements.

Using a LinkedList only updates the links.

---

# 📚 What is LinkedList?

A LinkedList stores elements as **nodes**.

Each node contains:

- Data
- Address of Previous Node
- Address of Next Node

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
               LinkedList
```

LinkedList also implements:

```text
Deque
Queue
```

---

# ✨ Features

- ✅ Dynamic Size
- ✅ Maintains Insertion Order
- ✅ Allows Duplicate Elements
- ✅ Allows Multiple null Values
- ✅ Fast Insert/Delete
- ❌ Slow Random Access

---

# 🧠 Internal Working

LinkedList uses a **Doubly Linked List**.

Each node stores:

```text
Previous Address
Current Data
Next Address
```

---

# 📦 Internal Structure

```text
null
 │
 ▼
+------+------+      +------+------+      +------+------+
|Prev |Data | Next-->|Prev |Data | Next-->|Prev |Data |Next
|null |Java |        |Java |Spring|        |Spring|Kafka|null
+------+------+      +------+------+      +------+------+
```

---

# 💻 Creating LinkedList

```java
List<String> list = new LinkedList<>();
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
list.remove("Spring Boot");
```

Output

```text
[Java, Kafka]
```

---

# 🔄 Queue Operations

```java
LinkedList<String> queue = new LinkedList<>();

queue.offer("Java");

queue.offer("Spring");

System.out.println(queue.poll());
```

Output

```text
Java
```

---

# 🔄 Deque Operations

```java
LinkedList<Integer> deque = new LinkedList<>();

deque.addFirst(10);

deque.addLast(20);

System.out.println(deque);
```

Output

```text
[10, 20]
```

---

# 🔄 Iterating LinkedList

### Enhanced For Loop

```java
for(String language : list){

    System.out.println(language);

}
```

---

### Iterator

```java
Iterator<String> iterator = list.iterator();

while(iterator.hasNext()){

    System.out.println(iterator.next());

}
```

---

### ListIterator

```java
ListIterator<String> iterator = list.listIterator();

while(iterator.hasNext()){

    System.out.println(iterator.next());

}
```

---

# 📊 Time Complexity

| Operation | Complexity |
|------------|------------|
| addFirst() | O(1) |
| addLast() | O(1) |
| removeFirst() | O(1) |
| removeLast() | O(1) |
| get(index) | O(n) |
| contains() | O(n) |
| set(index) | O(n) |

---

# 📌 Common Methods

| Method | Description |
|----------|-------------|
| add() | Adds element |
| addFirst() | Adds at beginning |
| addLast() | Adds at end |
| getFirst() | Returns first element |
| getLast() | Returns last element |
| removeFirst() | Removes first node |
| removeLast() | Removes last node |
| peek() | Retrieves head element |
| poll() | Retrieves and removes head |
| offer() | Inserts element |

---

# 🌍 Real-World Example

Imagine a train.

```text
🚆 Engine ⇄ Coach 1 ⇄ Coach 2 ⇄ Coach 3 ⇄ Coach 4
```

Adding or removing a coach only changes the links.

No shifting of all coaches is required.

This is exactly how a **LinkedList** works.

---

# ⚖ ArrayList vs LinkedList

| Feature | ArrayList | LinkedList |
|----------|-----------|------------|
| Data Structure | Dynamic Array | Doubly Linked List |
| Random Access | ⭐ Fast O(1) | ❌ Slow O(n) |
| Insert/Delete | Slow | Fast |
| Memory | Less | More |
| Cache Friendly | Yes | No |

---

# 📊 Memory Representation

```text
Head

 ▼
+------+------+
|Java |  •────┐
+------+------+
             ▼
       +------+------+
       |Spring| •────┐
       +------+------+
                  ▼
            +------+------+
            |Kafka | null |
            +------+------+
```

---

# ⚠ Limitations

- More memory consumption due to node references.
- Slow random access.
- Not suitable for frequent index-based operations.
- Not synchronized.

---

# 💡 Best Practices

✅ Use LinkedList when insertion and deletion are frequent.

✅ Prefer ArrayList for random access.

✅ Use LinkedList for Queue and Deque implementations.

✅ Access elements sequentially instead of repeatedly using `get(index)`.

---

# ❓ Interview Questions

## 1️⃣ What is LinkedList?

A doubly linked list implementation of the List and Deque interfaces.

---

## 2️⃣ Does LinkedList maintain insertion order?

✅ Yes.

---

## 3️⃣ Does LinkedList allow duplicates?

✅ Yes.

---

## 4️⃣ Can LinkedList store null values?

✅ Yes.

---

## 5️⃣ Why is insertion O(1)?

Because only node references are updated.

---

## 6️⃣ Why is get(index) O(n)?

Because the list must traverse nodes to reach the requested index.

---

## 7️⃣ Difference between ArrayList and LinkedList?

- **ArrayList** is better for reading.
- **LinkedList** is better for inserting and deleting.

---

## 8️⃣ Does LinkedList implement Queue?

✅ Yes.

It implements both **Queue** and **Deque** interfaces.

---

## 9️⃣ Is LinkedList thread-safe?

❌ No.

Use external synchronization if multiple threads access it.

---

## 🔟 When should you use LinkedList?

Use it when:

- Frequent insertions/deletions are required.
- Queue or Deque operations are common.
- Random access is not a priority.

---

# 📝 Summary

| Feature | LinkedList |
|----------|------------|
| Data Structure | Doubly Linked List |
| Ordered | ✅ Yes |
| Duplicates | ✅ Yes |
| Null Values | ✅ Yes |
| Thread Safe | ❌ No |
| Random Access | ❌ Slow |
| Insert/Delete | ⭐ Fast |

---

# 🎯 Key Takeaway

> **LinkedList** is ideal for applications that require **frequent insertions and deletions**. It provides efficient node manipulation using a **doubly linked list**, making it a great choice for implementing **queues**, **deques**, and dynamic data structures where random access is not the primary requirement.