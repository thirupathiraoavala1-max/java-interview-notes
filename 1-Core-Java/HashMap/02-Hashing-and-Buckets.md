# 🔐 Hashing and Buckets in Java HashMap

> 💡 **Hashing** is the core concept behind HashMap. It converts a key into a unique integer (hash code), which helps HashMap quickly locate the correct bucket to store or retrieve data.

---

# 🎯 Learning Objectives

After completing this chapter, you will understand:

- ✅ What is Hashing?
- ✅ Why Hashing is Needed?
- ✅ What is hashCode()?
- ✅ What is equals()?
- ✅ Bucket Concept
- ✅ Bucket Index Calculation
- ✅ Internal hash() Function
- ✅ Why Capacity is Always Power of 2?
- ✅ Memory Representation
- ✅ Time Complexity
- ✅ Best Practices
- ✅ Interview Questions

---

# 🤔 Why Do We Need Hashing?

Imagine a library with **1 million books**.

Without any organization:

```text
📚 Book 1
📚 Book 2
📚 Book 3
...
📚 Book 1000000
```

To find one book, you may need to search through all books.

```text
Search Time = O(n)
```

Now imagine each book is placed into a specific shelf based on its category.

```text
Programming  → Shelf 1
Science      → Shelf 2
History      → Shelf 3
Mathematics  → Shelf 4
```

Now finding a book is much faster.

This is exactly what **Hashing** does.

---

# 📚 What is Hashing?

**Hashing** is a technique that converts a key into a numeric value called a **Hash Code**.

```text
Key
 │
 ▼
Hash Function
 │
 ▼
Hash Code
```

Example:

```java
String language = "Java";

System.out.println(language.hashCode());
```

Output

```text
2301506
```

HashMap uses this hash code to decide where to store the key-value pair.

---

# 🧠 What is hashCode()?

Every Java object inherits the `hashCode()` method from the `Object` class.

```java
public int hashCode()
```

It returns an integer value representing the object.

Example

```java
String str = "Spring";

System.out.println(str.hashCode());
```

Output

```text
-1808118735
```

---

# 💡 Important Rules of hashCode()

✅ Same object → Same hashCode

```java
String s = "Java";

System.out.println(s.hashCode());
System.out.println(s.hashCode());
```

Output

```text
2301506
2301506
```

---

Different objects **can** have the same hash code.

```text
Object A → 12345

Object B → 12345
```

This is called a **Collision**.

---

# 🤝 What is equals()?

The `equals()` method checks whether two objects are logically equal.

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1.equals(s2));
```

Output

```text
true
```

---

# 🔗 Relationship Between hashCode() and equals()

HashMap first compares **hashCode()**.

If the hash codes match, then it compares **equals()**.

```text
Key
 │
 ▼
hashCode()
 │
 ▼
Find Bucket
 │
 ▼
equals()
 │
 ▼
Same Key?
```

If `equals()` returns **true**, the value is updated.

Otherwise, a new entry is inserted.

---

# 📦 What is a Bucket?

A **Bucket** is a location in the internal HashMap array where entries are stored.

```text
Bucket Array

+----+----+----+----+----+
| 0  | 1  | 2  | 3  | 4  |
+----+----+----+----+----+
```

Each box is called a **Bucket**.

---

# 🪣 Bucket Example

```java
map.put(101, "John");
map.put(102, "Alice");
map.put(103, "Bob");
```

Internally

```text
Bucket 0

Bucket 1

Bucket 2
   │
   ▼
101 → John

Bucket 3
   │
   ▼
102 → Alice

Bucket 4
   │
   ▼
103 → Bob
```

---

# 🧠 How Bucket Index is Calculated?

HashMap calculates the bucket index using:

```text
Bucket Index = (n - 1) & hash
```

Where

```text
n = Capacity
```

---

## Example

Capacity

```text
16
```

Hash Code

```text
2301506
```

Formula

```text
(16 - 1) & 2301506

15 & 2301506
```

Result

```text
Bucket 2
```

The entry is stored in **Bucket 2**.

---

# ⚙️ Internal hash() Method

HashMap doesn't directly use `hashCode()`.

It first applies an additional hash function to improve distribution.

Simplified implementation:

```java
static final int hash(Object key) {

    int h;

    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);

}
```

---

# 🧠 Why Apply Extra Hashing?

Suppose the original hash code has poor distribution.

```text
10000000

10000001

10000010
```

Many keys may end up in the same bucket.

The extra hash spreads the bits more evenly, reducing collisions.

---

# 📊 Complete Flow

```text
Key
 │
 ▼
hashCode()
 │
 ▼
hash()
 │
 ▼
Bucket Index
 │
 ▼
Store in Bucket
```

---

# 🔢 Why Capacity is Always a Power of 2?

Default capacities are:

```text
16

32

64

128

256
```

This allows HashMap to use the efficient bitwise calculation:

```text
(n - 1) & hash
```

instead of

```text
hash % capacity
```

Bitwise operations are faster than modulo operations.

---

# 📊 Memory Representation

```text
HashMap

          │
          ▼

+------+------+------+------+
|  0   |  1   |  2   |  3   |
+------+------+------+------+
                  │
                  ▼
             (101, John)
                  │
                  ▼
             (117, Alice)
```

If multiple keys map to the same bucket, they are connected together.

---

# 📈 Time Complexity

| Operation | Average | Worst |
|------------|---------|--------|
| Calculate Hash | O(1) | O(1) |
| Find Bucket | O(1) | O(1) |
| Search | O(1) | O(n) |

---

# 🌍 Real-World Examples

Hashing is used in:

- 🌐 DNS Lookup
- 💾 Database Indexing
- 🔑 Password Storage
- 📧 Email Systems
- 🛒 Shopping Cart
- 🗄️ Cache Storage
- 🔍 Search Engines

---

# 💡 Best Practices

✅ Use immutable objects as keys.

✅ Override both `equals()` and `hashCode()` for custom objects.

✅ Ensure equal objects return the same hash code.

---

# ⚠️ Common Mistakes

❌ Overriding `equals()` without overriding `hashCode()`.

❌ Assuming hash codes are always unique.

❌ Using mutable objects as keys.

---

# 🎯 Interview Notes

📌 Hashing converts a key into an integer hash code.

📌 HashMap uses `hashCode()` to find the bucket.

📌 `equals()` confirms whether keys are actually equal.

📌 Bucket index is calculated using:

```text
(n - 1) & hash
```

📌 Default capacity is **16**.

📌 Capacity is always a power of **2**.

---

# ❓ Interview Questions

### 1. What is hashing?

A technique to convert a key into an integer hash code for efficient storage and retrieval.

---

### 2. What is a hash code?

An integer value returned by the `hashCode()` method.

---

### 3. Why does HashMap use `equals()`?

To verify whether two keys are logically equal after they land in the same bucket.

---

### 4. What is a bucket?

A storage location inside the internal HashMap array.

---

### 5. How is the bucket index calculated?

```text
(n - 1) & hash
```

---

### 6. Why is capacity always a power of 2?

To enable efficient bucket calculation using bitwise AND instead of modulo.

---

### 7. Can two different keys have the same hash code?

✅ Yes. This is called a collision.

---

### 8. What happens if two keys have the same hash code?

They are placed in the same bucket, and `equals()` is used to distinguish them.

---

### 9. Does HashMap use `hashCode()` directly?

❌ No. It first applies an internal `hash()` function to improve distribution.

---

### 10. Why is hashing important?

It enables fast insertion, lookup, and deletion by reducing search time from **O(n)** to **O(1)** on average.

---

# 📝 Summary

| Concept | Description |
|----------|-------------|
| Hashing | Converts a key into a hash code |
| hashCode() | Returns integer hash value |
| equals() | Compares object equality |
| Bucket | Storage location in HashMap |
| Bucket Index | `(n - 1) & hash` |
| Default Capacity | 16 |
| Power of 2 | Enables fast bucket calculation |

---

# 🎯 Key Takeaway

> **Hashing** is the foundation of HashMap's performance. By converting keys into hash codes, calculating bucket indices efficiently, and using `equals()` to resolve logical equality, HashMap achieves fast average-case operations. Understanding hashing and bucket allocation is essential before learning about **collisions**, **rehashing**, and **treeification**, which we'll cover in the next chapter.