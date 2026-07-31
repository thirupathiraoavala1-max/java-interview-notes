# 🚨 Exception Handling in Java

> 💡 **Exception Handling** is a mechanism in Java used to handle runtime errors gracefully, ensuring that the normal flow of the application is maintained.

---

# 🎯 Why Do We Need Exception Handling?

Imagine you're withdrawing money from an ATM.

If an unexpected issue occurs:

- ❌ Card not inserted
- ❌ Incorrect PIN
- ❌ Network failure

The ATM shouldn't crash.

Instead, it should display an appropriate error message.

Similarly, Java uses **Exception Handling** to handle unexpected situations without terminating the application.

---

# 📚 What is an Exception?

An **Exception** is an event that occurs during program execution and interrupts the normal flow of the program.

Example:

```java
int result = 10 / 0;
```

Output

```text
Exception in thread "main"
java.lang.ArithmeticException: / by zero
```

---

# 🏗️ Exception Hierarchy

```text
                    Object
                       │
                   Throwable
                  /          \
                 /            \
            Error          Exception
                               │
               ┌───────────────┴──────────────┐
               ▼                              ▼
      Checked Exceptions          RuntimeException
                                            │
                              Unchecked Exceptions
```

---

# 📌 Types of Exceptions

Java exceptions are classified into two categories.

```text
              Exceptions
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
   Checked             Unchecked
```

---

# ✅ Checked Exceptions

Checked exceptions are checked by the compiler.

The programmer must handle or declare them.

Examples:

- IOException
- SQLException
- FileNotFoundException
- ClassNotFoundException

Example

```java
import java.io.*;

public class Demo {

    public static void main(String[] args) throws IOException {

        FileReader file = new FileReader("data.txt");

    }

}
```

---

# ❌ Unchecked Exceptions

Unchecked exceptions occur at runtime.

Examples:

- ArithmeticException
- NullPointerException
- ArrayIndexOutOfBoundsException
- NumberFormatException

Example

```java
int result = 10 / 0;
```

---

# 📊 Checked vs Unchecked Exceptions

| Feature | Checked | Unchecked |
|----------|----------|------------|
| Checked by Compiler | ✅ | ❌ |
| Occurs | Compile Time | Runtime |
| Must Handle | ✅ Yes | ❌ No |
| Parent Class | Exception | RuntimeException |

---

# 🛠️ Exception Handling Keywords

Java provides five keywords.

| Keyword | Purpose |
|----------|----------|
| `try` | Wrap risky code |
| `catch` | Handle exception |
| `finally` | Cleanup code |
| `throw` | Throw an exception manually |
| `throws` | Declare exceptions |

---

# 🔹 try-catch

```java
try {

    int result = 10 / 0;

} catch (ArithmeticException e) {

    System.out.println("Cannot divide by zero");

}
```

Output

```text
Cannot divide by zero
```

---

# 🔹 try-catch-finally

```java
try {

    System.out.println("Inside try");

} catch (Exception e) {

    System.out.println("Inside catch");

} finally {

    System.out.println("Finally always executes");

}
```

Output

```text
Inside try
Finally always executes
```

---

# 🔹 throw Keyword

Used to throw an exception manually.

```java
public class Demo {

    public static void main(String[] args) {

        throw new ArithmeticException("Invalid Operation");

    }

}
```

---

# 🔹 throws Keyword

Used to declare exceptions.

```java
public void readFile() throws IOException {

}
```

---

# ⚖️ throw vs throws

| throw | throws |
|---------|---------|
| Throws an exception | Declares exceptions |
| Used inside method | Used in method signature |
| Throws one exception | Can declare multiple exceptions |

---

# 🔹 Multiple Catch Blocks

```java
try {

    int[] arr = new int[2];

    System.out.println(arr[5]);

} catch (ArithmeticException e) {

    System.out.println("Arithmetic Error");

} catch (ArrayIndexOutOfBoundsException e) {

    System.out.println("Array Error");

}
```

Output

```text
Array Error
```

---

# 🔹 Multi-Catch (Java 7+)

```java
try {

    // risky code

} catch (ArithmeticException | NullPointerException e) {

    System.out.println("Handled");

}
```

---

# 🔹 Nested try Block

```java
try {

    try {

        int result = 10 / 0;

    } catch (ArithmeticException e) {

        System.out.println("Inner Catch");

    }

} catch (Exception e) {

    System.out.println("Outer Catch");

}
```

---

# 🔹 Custom Exception

```java
class InvalidAgeException extends Exception {

    InvalidAgeException(String message) {

        super(message);

    }

}
```

Usage

```java
public class Demo {

    static void validateAge(int age) throws InvalidAgeException {

        if (age < 18) {

            throw new InvalidAgeException("Age must be 18 or above");

        }

    }

}
```

---

# 🔄 Exception Propagation

```text
method3()
     │
     ▼
method2()
     │
     ▼
method1()
     │
     ▼
main()
```

If an exception is not handled, it propagates up the call stack until it is caught or the program terminates.

---

# 🌍 Real-World Example

Imagine ordering food online.

🍽️ Order Placed

⬇

💳 Payment Failed

⬇

Instead of crashing,

the application displays:

> "Payment Failed. Please try again."

This is exception handling.

---

# ⚖️ Error vs Exception

| Error | Exception |
|---------|------------|
| Serious problem | Recoverable problem |
| Cannot usually be handled | Can be handled |
| Example: OutOfMemoryError | Example: IOException |

---

# ❓ Interview Questions

## 1️⃣ What is Exception Handling?

A mechanism to handle runtime errors without stopping the program.

---

## 2️⃣ Difference between Checked and Unchecked Exceptions?

Checked exceptions are verified by the compiler, whereas unchecked exceptions occur at runtime.

---

## 3️⃣ Difference between throw and throws?

- `throw` is used to throw an exception.
- `throws` is used to declare exceptions.

---

## 4️⃣ Does finally always execute?

✅ Yes.

Except in situations like:

- JVM crash
- `System.exit()`
- Power failure

---

## 5️⃣ Can we have try without catch?

✅ Yes.

```java
try {

    // code

} finally {

}
```

---

## 6️⃣ Can we have catch without try?

❌ No.

---

## 7️⃣ Can we have multiple catch blocks?

✅ Yes.

---

## 8️⃣ What is Exception Propagation?

Passing an exception from one method to its caller until it is handled.

---

## 9️⃣ Can we throw checked exceptions manually?

✅ Yes.

Using the `throw` keyword.

---

## 🔟 What is a Custom Exception?

A user-defined exception created by extending `Exception` or `RuntimeException`.

---

# 💡 Best Practices

✅ Catch the most specific exception first.

✅ Never catch generic `Exception` unless necessary.

✅ Always close resources using **try-with-resources**.

✅ Use custom exceptions for business logic.

✅ Provide meaningful exception messages.

---

# 📝 Summary

| Concept | Description |
|----------|-------------|
| 🚨 Exception | Runtime abnormal condition |
| ✅ Checked Exception | Checked by compiler |
| ❌ Unchecked Exception | Occurs at runtime |
| 🛠️ try | Risky code |
| 🎯 catch | Handles exception |
| 🧹 finally | Cleanup code |
| 🚀 throw | Throws exception |
| 📢 throws | Declares exception |

---

# 🎯 Key Takeaway

> **Exception Handling** enables Java applications to recover gracefully from unexpected situations. Mastering **checked vs unchecked exceptions**, **try-catch-finally**, **throw vs throws**, **custom exceptions**, and **exception propagation** is essential for writing robust, production-ready Java applications and excelling in Java backend interviews.