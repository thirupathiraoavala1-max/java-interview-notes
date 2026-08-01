# 🌳 TreeSet in Java

> 💡 **TreeSet** is an implementation of the **Set** interface that stores **unique elements in sorted order**. It is backed by a **TreeMap**, which internally uses a **Red-Black Tree**.

---

# 🎯 Why Do We Need TreeSet?

Imagine an Employee Management System.

Employee IDs are inserted randomly:

```text
105
101
109
103
102
```

Requirement:

- ✅ No duplicate IDs
- ✅ IDs should always be sorted

TreeSet automatically sorts the data.

---

# 📚 What is TreeSet?

TreeSet is a sorted collection that:

- Stores unique elements
- Automatically sorts elements
- Does not maintain insertion order
- Uses Red-Black Tree internally

```java
Set<Integer> set = new TreeSet<>();
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
                 SortedSet
                    │
                    ▼
              NavigableSet
                    │
                    ▼
                 TreeSet
```

---

# ✨ Features

- ✅ Unique Elements
- ✅ Automatically Sorted
- ✅ Fast Search
- ❌ No Duplicates
- ❌ No null Values
- ❌ Not Thread Safe

---

# 🧠 Internal Working

TreeSet internally uses

```text
TreeMap
```

TreeMap internally uses

```text
Red-Black Tree
```

A Red-Black Tree is a self-balancing Binary Search Tree.

---

# 🌳 Internal Structure

```text
             50
            /  \
          30    70
         / \    / \
       20 40  60 80
```

Whenever a new element is inserted,

the tree automatically balances itself.

---

# 💻 Creating TreeSet

```java
Set<Integer> numbers = new TreeSet<>();
```

---

# 📥 Adding Elements

```java
numbers.add(50);
numbers.add(20);
numbers.add(70);
numbers.add(10);

System.out.println(numbers);
```

Output

```text
[10, 20, 50, 70]
```

Automatically sorted.

---

# ❌ Duplicate Elements

```java
numbers.add(50);
numbers.add(50);
```

Output

```text
[50]
```

Duplicates are ignored.

---

# ❌ Null Values

```java
numbers.add(null);
```

Output

```text
NullPointerException
```

TreeSet does **not allow null** because it cannot compare `null` with other elements.

---

# 🔍 Searching

```java
System.out.println(numbers.contains(20));
```

Output

```text
true
```

---

# ❌ Removing

```java
numbers.remove(20);
```

---

# 📌 Navigation Methods

### First Element

```java
System.out.println(numbers.first());
```

---

### Last Element

```java
System.out.println(numbers.last());
```

---

### Higher Element

```java
System.out.println(numbers.higher(30));
```

Returns the next greater element.

---

### Lower Element

```java
System.out.println(numbers.lower(30));
```

Returns the next smaller element.

---

### Ceiling

```java
System.out.println(numbers.ceiling(25));
```

Returns the smallest element greater than or equal to 25.

---

### Floor

```java
System.out.println(numbers.floor(25));
```

Returns the largest element less than or equal to 25.

---

# 🔄 Iterating

```java
for(Integer number : numbers){

    System.out.println(number);

}
```

---

# 📊 Time Complexity

| Operation | Complexity |
|------------|------------|
| add() | O(log n) |
| remove() | O(log n) |
| contains() | O(log n) |
| first() | O(log n) |
| last() | O(log n) |

---

# ⚖ HashSet vs LinkedHashSet vs TreeSet

| Feature | HashSet | LinkedHashSet | TreeSet |
|----------|----------|---------------|----------|
| Order | ❌ No | ✅ Insertion | ✅ Sorted |
| Duplicates | ❌ No | ❌ No | ❌ No |
| Null | One | One | ❌ No |
| Internal DS | HashMap | LinkedHashMap | TreeMap |
| Complexity | O(1) | O(1) | O(log n) |

---

# 🌍 Real-World Examples

TreeSet is useful for:

- 📈 Leaderboards
- 🏆 Ranking Systems
- 📅 Event Scheduling
- 📊 Sorted Reports
- 🧾 Employee IDs
- 📚 Dictionary Applications

---

# ⚠ Limitations

- Slower than HashSet.
- Does not preserve insertion order.
- Does not allow null.
- Not thread-safe.

---

# 💡 Best Practices

✅ Use TreeSet when sorted data is required.

✅ Use HashSet when speed is more important than ordering.

✅ Use LinkedHashSet when insertion order matters.

---

# 🔀 Natural Ordering

TreeSet sorts elements using **Comparable**.

```java
TreeSet<String> set = new TreeSet<>();

set.add("Banana");
set.add("Apple");
set.add("Orange");

System.out.println(set);
```

Output

```text
[Apple, Banana, Orange]
```

---

# 🔀 Custom Sorting

Using Comparator.

```java
TreeSet<Integer> numbers =
        new TreeSet<>(Comparator.reverseOrder());

numbers.add(10);
numbers.add(30);
numbers.add(20);

System.out.println(numbers);
```

Output

```text
[30, 20, 10]
```

---

# ❓ Interview Questions

## 1️⃣ What is TreeSet?

A sorted Set implementation backed by TreeMap.

---

## 2️⃣ Does TreeSet allow duplicates?

❌ No.

---

## 3️⃣ Does TreeSet maintain insertion order?

❌ No.

It maintains sorted order.

---

## 4️⃣ Does TreeSet allow null?

❌ No.

---

## 5️⃣ What is the internal data structure?

TreeMap using a Red-Black Tree.

---

## 6️⃣ Why is TreeSet slower than HashSet?

Because TreeSet uses a balanced tree with O(log n) operations, whereas HashSet uses hashing with average O(1) operations.

---

## 7️⃣ How does TreeSet sort elements?

By natural ordering (`Comparable`) or a custom `Comparator`.

---

## 8️⃣ Can TreeSet store custom objects?

✅ Yes.

Implement `Comparable` or provide a `Comparator`.

---

## 9️⃣ Difference between TreeSet and HashSet?

- TreeSet stores sorted elements.
- HashSet stores unordered elements.

---

## 🔟 When should you use TreeSet?

When:

- Sorted order is required.
- Duplicate elements are not allowed.
- Range-based operations are needed.

---

# 📝 Summary

| Feature | TreeSet |
|----------|----------|
| Data Structure | Red-Black Tree |
| Ordered | ✅ Sorted |
| Duplicates | ❌ No |
| Null | ❌ No |
| Thread Safe | ❌ No |
| Search | O(log n) |
| Internal DS | TreeMap |

---

# 🎯 Key Takeaway

> **TreeSet** is the ideal choice when you need **unique elements in sorted order**. It is backed by a **TreeMap** and internally uses a **Red-Black Tree**, providing efficient O(log n) operations for insertion, deletion, and searching. It is commonly used in ranking systems, leaderboards, scheduling applications, and interview questions involving sorted collections.