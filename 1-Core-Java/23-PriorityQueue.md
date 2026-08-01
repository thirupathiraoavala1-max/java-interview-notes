# ⚡ PriorityQueue in Java

> 💡 **PriorityQueue** is a queue implementation in the Java Collections Framework where elements are ordered based on their **priority** rather than their insertion order. Internally, it is implemented using a **Binary Heap**.

---

# 🎯 Why Do We Need PriorityQueue?

Imagine a hospital emergency room.

Patients arrive in this order:

```text
👤 Patient A (Priority 3)
👤 Patient B (Priority 1)
👤 Patient C (Priority 2)
```

Treatment order:

```text
Patient B
Patient C
Patient A
```

Priority is more important than arrival order.

This is exactly how **PriorityQueue** works.

---

# 📚 What is PriorityQueue?

PriorityQueue stores elements according to their priority.

By default,

- Smallest element has highest priority.
- Uses Min Heap.
- Does not maintain insertion order.

```java
Queue<Integer> queue = new PriorityQueue<>();
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
                  Queue
                    │
                    ▼
              PriorityQueue
```

---

# ✨ Features

- ✅ Automatically Sorted by Priority
- ✅ Uses Binary Heap
- ✅ Fast Insert/Delete
- ❌ Does Not Maintain Insertion Order
- ❌ Not Thread Safe
- ❌ Does Not Allow null

---

# 🧠 Internal Working

PriorityQueue internally uses a **Binary Heap**.

Default implementation:

```text
Min Heap
```

Root always contains the smallest element.

---

# 🌳 Min Heap Structure

```text
          10
         /  \
       20    30
      / \    /
    40  50 60
```

Smallest element is always at the root.

---

# 💻 Creating PriorityQueue

```java
Queue<Integer> queue = new PriorityQueue<>();
```

---

# 📥 Adding Elements

```java
queue.offer(50);
queue.offer(10);
queue.offer(30);
queue.offer(20);

System.out.println(queue);
```

Output

```text
[10, 20, 30, 50]
```

*(Internal representation may vary, but `peek()` and `poll()` always return the highest-priority element.)*

---

# 👀 peek()

Returns the highest-priority element.

```java
System.out.println(queue.peek());
```

Output

```text
10
```

---

# 📤 poll()

Removes and returns the highest-priority element.

```java
System.out.println(queue.poll());
```

Output

```text
10
```

Queue becomes

```text
[20, 50, 30]
```

---

# 📥 offer() vs add()

| offer() | add() |
|----------|--------|
| Preferred for Queue | Collection Method |
| Returns false if insertion fails | Throws Exception |

---

# ❌ Null Values

```java
queue.offer(null);
```

Output

```text
NullPointerException
```

PriorityQueue does **not allow null values**.

---

# 🔄 Iterating

```java
for(Integer number : queue){

    System.out.println(number);

}
```

⚠️ Iteration order is **not guaranteed to be sorted**.

Use `poll()` repeatedly to retrieve elements in priority order.

---

# 🔀 Max Heap

By default,

PriorityQueue is a Min Heap.

To create a Max Heap

```java
Queue<Integer> queue =
        new PriorityQueue<>(Comparator.reverseOrder());

queue.offer(10);
queue.offer(50);
queue.offer(20);

System.out.println(queue.poll());
```

Output

```text
50
```

---

# 📊 Time Complexity

| Operation | Complexity |
|------------|------------|
| offer() | O(log n) |
| add() | O(log n) |
| poll() | O(log n) |
| remove() | O(log n) |
| peek() | O(1) |
| contains() | O(n) |

---

# 📌 Common Methods

| Method | Description |
|----------|-------------|
| offer() | Inserts element |
| add() | Inserts element |
| poll() | Removes highest-priority element |
| peek() | Returns highest-priority element |
| remove() | Removes specified element |
| contains() | Checks existence |

---

# 🌍 Real-World Examples

PriorityQueue is used in:

- 🏥 Hospital Emergency Systems
- 💻 CPU Scheduling
- 📶 Network Packet Routing
- 📧 Email Prioritization
- 🚖 Cab Booking
- 📈 Stock Market Processing
- 🤖 Task Scheduling

---

# 📊 Memory Representation

```text
          5
        /   \
      10     20
     / \    /
   30 40  50
```

Every parent node has higher priority than its children.

---

# ⚖ Queue vs PriorityQueue

| Queue | PriorityQueue |
|--------|---------------|
| FIFO | Priority-Based |
| Arrival Order | Sorted by Priority |
| LinkedList | Binary Heap |

---

# ⚖ PriorityQueue vs TreeSet

| PriorityQueue | TreeSet |
|---------------|----------|
| Allows Duplicates | No Duplicates |
| Heap | Red-Black Tree |
| O(log n) | O(log n) |
| No Sorted Iteration | Sorted Iteration |

---

# ⚠ Limitations

- Does not preserve insertion order.
- Does not allow null values.
- Not synchronized.
- Iterator is not sorted.

---

# 💡 Best Practices

✅ Use PriorityQueue for scheduling tasks.

✅ Use Comparator for custom priority.

✅ Use poll() instead of iteration when priority order matters.

---

# ❓ Interview Questions

## 1️⃣ What is PriorityQueue?

A queue implementation that orders elements by priority using a Binary Heap.

---

## 2️⃣ What is the default ordering?

Ascending order (Min Heap).

---

## 3️⃣ Does PriorityQueue maintain insertion order?

❌ No.

---

## 4️⃣ Does PriorityQueue allow duplicates?

✅ Yes.

---

## 5️⃣ Does PriorityQueue allow null values?

❌ No.

---

## 6️⃣ What is the internal data structure?

Binary Heap.

---

## 7️⃣ Difference between peek() and poll()?

| peek() | poll() |
|----------|----------|
| Returns head | Removes and returns head |

---

## 8️⃣ How do you create a Max Heap?

```java
PriorityQueue<Integer> queue =
    new PriorityQueue<>(Comparator.reverseOrder());
```

---

## 9️⃣ Is PriorityQueue thread-safe?

❌ No.

Use `PriorityBlockingQueue` for thread-safe scenarios.

---

## 🔟 When should you use PriorityQueue?

When tasks must be processed based on priority rather than arrival order.

---

# 📝 Summary

| Feature | PriorityQueue |
|----------|---------------|
| Data Structure | Binary Heap |
| Ordered | Priority Order |
| Duplicates | ✅ Yes |
| Null | ❌ No |
| Thread Safe | ❌ No |
| peek() | O(1) |
| offer()/poll() | O(log n) |

---

# 🎯 Key Takeaway

> **PriorityQueue** is the best choice when elements need to be processed according to **priority** instead of insertion order. It is implemented using a **Binary Heap**, providing efficient **O(log n)** insertion and deletion while keeping the highest-priority element readily available.