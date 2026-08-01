# 🗑️ Garbage Collection (GC)

> 💡 **Garbage Collection (GC)** is an automatic memory management process in Java that removes unused objects from the **Heap Memory**, freeing memory and preventing memory leaks.

---

# 🎯 Why Do We Need Garbage Collection?

Imagine an application continuously creating objects.

```java
Employee emp = new Employee();
```

If these unused objects are never removed:

- ❌ Heap memory fills up.
- ❌ Application performance degrades.
- ❌ Eventually, an `OutOfMemoryError` occurs.

👉 **Garbage Collection automatically removes unreachable objects**, making memory available for new objects.

---

# 🏗️ How Garbage Collection Works

```text
        new Employee()
              │
              ▼
        🟩 Heap Memory
              │
              ▼
     Object becomes Unreachable
              │
              ▼
      🗑️ Garbage Collector
              │
              ▼
      Memory is Reclaimed
```

---

# 💾 Heap Memory Structure

The JVM divides Heap Memory into different generations.

```text
                    🟩 Heap Memory
                          │
       ┌──────────────────┼──────────────────┐
       ▼                  ▼                  ▼
 🌱 Young Generation   🧓 Old Generation   ♾️ Metaspace
```

---

# 🌱 Young Generation

The Young Generation stores **newly created objects**.

It consists of:

- 🌿 Eden Space
- 🌿 Survivor Space S0
- 🌿 Survivor Space S1

```text
        Young Generation

+-------------------------------+
|          Eden Space           |
+-------------------------------+
| Survivor S0 | Survivor S1     |
+-------------------------------+
```

### 📌 Process

- Objects are created in **Eden Space**.
- Surviving objects move between **Survivor Spaces**.
- Long-lived objects are promoted to the **Old Generation**.

---

# 🧓 Old Generation

Stores objects that survive multiple garbage collection cycles.

### 💻 Example

```java
Employee employee = new Employee();
```

If `employee` remains in use for a long time, it is moved from the Young Generation to the Old Generation.

---

# ♾️ Metaspace

Introduced in **Java 8**.

Stores:

- Class Metadata
- Method Information
- Runtime Constant Pool

> 📌 Before Java 8, this area was called **PermGen (Permanent Generation)**.

---

# 🔄 Garbage Collection Process

```text
Create Object
      │
      ▼
🌱 Young Generation
      │
      ▼
Minor GC
      │
      ▼
Object Survives?
    /       \
 Yes         No
 │            │
 ▼            ▼
🧓 Old Gen   🗑️ Memory Reclaimed
      │
      ▼
Major GC
      │
      ▼
🗑️ Memory Reclaimed
```

---

# 🗑️ Types of Garbage Collection

## 🌱 1. Minor GC

- Cleans the Young Generation.
- Fast and frequent.
- Moves surviving objects to Survivor Space or Old Generation.

---

## 🧓 2. Major GC

- Cleans the Old Generation.
- Slower than Minor GC.
- Triggered less frequently.

---

## 🌍 3. Full GC

- Cleans the entire Heap.
- Includes Young Generation, Old Generation, and may involve Metaspace cleanup.
- Most expensive GC operation.

---

# 🚀 Popular Garbage Collectors

| Garbage Collector | Best For |
|-------------------|----------|
| 🟢 Serial GC | Small Applications |
| 🔵 Parallel GC | Multi-core Systems |
| 🟣 G1 GC | Large Heap Applications *(Default from Java 9+)* |
| 🟡 ZGC | Low-Latency Applications |
| 🔴 Shenandoah GC | Large Memory with Low Pause Time |

---

# 📌 When Does an Object Become Eligible for GC?

## 1️⃣ Null Reference

```java
Employee emp = new Employee();

emp = null;
```

---

## 2️⃣ Reassigning Reference

```java
Employee emp1 = new Employee();
Employee emp2 = new Employee();

emp1 = emp2;
```

The first object becomes eligible for Garbage Collection.

---

## 3️⃣ Anonymous Object

```java
new Employee();
```

Since no reference points to it, it becomes eligible immediately.

---

## 4️⃣ Local Variable Goes Out of Scope

```java
public void display() {

    Employee emp = new Employee();

}
```

After `display()` finishes, the object may become eligible for Garbage Collection.

---

# ❌ Can We Force Garbage Collection?

```java
System.gc();
```

❌ **No.**

`System.gc()` only **requests** the JVM to perform Garbage Collection.

The JVM may choose to ignore this request.

---

# 🌍 Real-World Analogy

Imagine a **hotel**.

| Hotel | JVM |
|--------|-----|
| 🏨 Rooms | Heap Memory |
| 👤 Guests | Objects |
| 🧹 Housekeeping | Garbage Collector |

When a guest checks out (object becomes unreachable), housekeeping cleans the room so it can be used again.

---

# ⚖️ Minor GC vs Major GC vs Full GC

| Feature | 🌱 Minor GC | 🧓 Major GC | 🌍 Full GC |
|----------|------------|------------|------------|
| Memory Area | Young Generation | Old Generation | Entire Heap |
| Speed | Fast | Slower | Slowest |
| Frequency | Frequent | Less Frequent | Rare |

---

# ❓ Interview Questions

## 1️⃣ What is Garbage Collection?

Garbage Collection is the automatic process of removing unreachable objects from Heap Memory.

---

## 2️⃣ Which memory area is managed by the Garbage Collector?

✅ Heap Memory

---

## 3️⃣ What is the difference between Minor GC and Major GC?

| Minor GC | Major GC |
|-----------|-----------|
| Cleans Young Generation | Cleans Old Generation |
| Faster | Slower |
| Frequent | Less Frequent |

---

## 4️⃣ What replaced PermGen?

✅ **Metaspace** (Java 8 onwards)

---

## 5️⃣ Does `System.gc()` guarantee Garbage Collection?

❌ No.

It only requests the JVM to perform Garbage Collection.

---

## 6️⃣ Which Garbage Collector is the default in modern Java?

✅ **G1 Garbage Collector** (Default from Java 9 onwards)

---

# 💡 Best Practices

✅ Remove unnecessary object references.

✅ Close resources using **try-with-resources**.

✅ Avoid memory leaks caused by static collections or lingering references.

✅ Monitor Heap usage in production applications.

✅ Choose an appropriate Garbage Collector based on application requirements.

---

# 📝 Summary

| Concept | Description |
|---------|-------------|
| 🗑️ Garbage Collection | Automatic memory cleanup |
| 🌱 Young Generation | Stores newly created objects |
| 🧓 Old Generation | Stores long-lived objects |
| ♾️ Metaspace | Stores class metadata |
| ⚡ Minor GC | Cleans Young Generation |
| 🐢 Major GC | Cleans Old Generation |
| 🌍 Full GC | Cleans the entire Heap |

---

# 🎯 Key Takeaway

> Java's **Garbage Collector** automatically manages Heap Memory by removing unreachable objects. Understanding **Heap Generations**, **GC Types**, and **Object Lifecycle** is essential for writing efficient Java applications and performing well in Java backend interviews.