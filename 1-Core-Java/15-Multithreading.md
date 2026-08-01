# 🧵 Multithreading in Java

> 💡 **Multithreading** is the ability of a program to execute multiple threads concurrently, improving application performance, responsiveness, and resource utilization.

---

# 🎯 Why Do We Need Multithreading?

Imagine an online shopping application.

Without Multithreading:

- ❌ User waits while payment is processed.
- ❌ Notifications are delayed.
- ❌ Inventory updates block other operations.

With Multithreading:

- 🛒 Order Processing
- 💳 Payment Processing
- 📧 Email Notifications
- 📦 Inventory Updates

All run simultaneously.

---

# 📚 What is a Process?

A **Process** is an independent program in execution.

Examples:

- Google Chrome
- IntelliJ IDEA
- VS Code
- Spotify

Each process has its own memory.

---

# 🧵 What is a Thread?

A **Thread** is the smallest unit of execution within a process.

Multiple threads share the same process memory.

---

# 📊 Process vs Thread

| Process | Thread |
|----------|---------|
| Independent program | Smallest execution unit |
| Separate memory | Shared memory |
| Heavyweight | Lightweight |
| Slow creation | Fast creation |

---

# 🏗️ Thread Lifecycle

```text
                NEW
                 │
                 ▼
             RUNNABLE
                 │
        ┌────────┴────────┐
        ▼                 ▼
     RUNNING          BLOCKED
        │                 │
        └────────┬────────┘
                 ▼
            TERMINATED
```

---

# 🚀 Creating Threads

Java provides two ways.

```text
          Thread Creation
                │
      ┌─────────┴─────────┐
      ▼                   ▼
 Extend Thread      Implement Runnable
```

---

# 🔹 Method 1: Extend Thread Class

```java
class MyThread extends Thread {

    @Override
    public void run() {

        System.out.println("Thread is Running");

    }

}

public class Demo {

    public static void main(String[] args) {

        MyThread thread = new MyThread();

        thread.start();

    }

}
```

---

# 🔹 Method 2: Implement Runnable Interface

```java
class MyTask implements Runnable {

    @Override
    public void run() {

        System.out.println("Runnable Thread");

    }

}

public class Demo {

    public static void main(String[] args) {

        Thread thread = new Thread(new MyTask());

        thread.start();

    }

}
```

---

# 📌 start() vs run()

| start() | run() |
|----------|--------|
| Creates a new thread | Executes in current thread |
| Calls JVM scheduler | Normal method call |

---

# 🔒 Synchronization

Synchronization prevents multiple threads from accessing shared resources simultaneously.

---

## Without Synchronization

```java
class Counter {

    int count = 0;

    void increment() {

        count++;

    }

}
```

Race conditions may occur.

---

## With Synchronization

```java
class Counter {

    int count = 0;

    synchronized void increment() {

        count++;

    }

}
```

Only one thread can execute the synchronized method at a time.

---

# 🔐 Synchronized Block

```java
class Counter {

    void display() {

        synchronized(this) {

            System.out.println("Thread Safe");

        }

    }

}
```

---

# 🛡️ Deadlock

Deadlock occurs when two or more threads wait indefinitely for each other to release resources.

---

## Example

```text
Thread A
Locks Resource 1
Waiting for Resource 2

Thread B
Locks Resource 2
Waiting for Resource 1

❌ Deadlock
```

---

# 💨 volatile Keyword

The `volatile` keyword ensures that changes made by one thread are immediately visible to other threads.

```java
class Flag {

    volatile boolean running = true;

}
```

---

# 📞 wait(), notify(), notifyAll()

These methods are defined in the **Object** class and are used for thread communication.

---

## wait()

Suspends the current thread until another thread notifies it.

```java
obj.wait();
```

---

## notify()

Wakes up one waiting thread.

```java
obj.notify();
```

---

## notifyAll()

Wakes up all waiting threads.

```java
obj.notifyAll();
```

---

# 🏊 Thread Pool

Instead of creating new threads repeatedly, Java provides thread pools.

Benefits:

- Better Performance
- Thread Reuse
- Reduced Overhead

---

# 🚀 ExecutorService

```java
import java.util.concurrent.*;

ExecutorService executor = Executors.newFixedThreadPool(3);

executor.submit(() -> System.out.println("Task Executed"));

executor.shutdown();
```

---

# ⚖️ Thread vs Runnable

| Thread | Runnable |
|----------|----------|
| Class | Interface |
| Single Inheritance | Supports Multiple Inheritance |
| Less Flexible | Preferred Approach |

---

# ⚖️ synchronized vs volatile

| synchronized | volatile |
|---------------|----------|
| Ensures mutual exclusion | Ensures visibility |
| Thread-safe | Not thread-safe by itself |
| Locks object | No locking |

---

# 🌍 Real-World Analogy

Imagine a restaurant.

👨‍🍳 Chef → Thread

🍽️ Kitchen → Shared Resource

Only one chef can use a specific cooking station at a time.

This is **Synchronization**.

---

# 📊 Thread Execution Flow

```text
Program Starts
      │
      ▼
Create Thread
      │
      ▼
start()
      │
      ▼
Runnable
      │
      ▼
Running
      │
      ▼
Completed
```

---

# ❓ Interview Questions

## 1️⃣ What is Multithreading?

Executing multiple threads concurrently within the same process.

---

## 2️⃣ Difference between Process and Thread?

Processes have separate memory, while threads share the same memory.

---

## 3️⃣ Difference between start() and run()?

- `start()` creates a new thread.
- `run()` executes like a normal method.

---

## 4️⃣ Why is Runnable preferred over Thread?

Because Java supports single inheritance.

Using Runnable allows your class to extend another class if needed.

---

## 5️⃣ What is Synchronization?

A mechanism that allows only one thread to access a shared resource at a time.

---

## 6️⃣ What is Deadlock?

A situation where two or more threads wait forever for each other to release resources.

---

## 7️⃣ What is the volatile keyword?

It ensures visibility of shared variable updates across threads.

---

## 8️⃣ Difference between wait() and sleep()?

| wait() | sleep() |
|----------|----------|
| Releases lock | Does not release lock |
| Object class | Thread class |
| Used for communication | Used for delay |

---

## 9️⃣ Why use ExecutorService?

To efficiently manage and reuse threads through thread pools.

---

## 🔟 Which is better: Thread or Runnable?

✅ **Runnable** is generally preferred because it promotes better design and avoids Java's single inheritance limitation.

---

# 💡 Best Practices

✅ Prefer `ExecutorService` over manually creating threads.

✅ Use `Runnable` or `Callable` instead of extending `Thread`.

✅ Minimize synchronized blocks to improve performance.

✅ Always shut down `ExecutorService`.

✅ Avoid nested locks to prevent deadlocks.

---

# 📝 Summary

| Concept | Description |
|----------|-------------|
| 🧵 Thread | Smallest unit of execution |
| 🚀 start() | Starts a new thread |
| 🔒 synchronized | Prevents concurrent access |
| 💨 volatile | Ensures visibility |
| 📞 wait() | Suspends thread |
| 🔔 notify() | Wakes one thread |
| 📢 notifyAll() | Wakes all waiting threads |
| 🏊 ExecutorService | Manages thread pools |
| 🛡️ Deadlock | Threads waiting indefinitely |

---

# 🎯 Key Takeaway

> **Multithreading** enables Java applications to execute multiple tasks concurrently, improving performance and responsiveness. Understanding **Thread Lifecycle**, **Synchronization**, **Deadlocks**, **volatile**, **wait/notify**, and **ExecutorService** is essential for building scalable backend applications and succeeding in Java interviews.