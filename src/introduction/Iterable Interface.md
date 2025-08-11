# Iterable Interface

---
## **`Iterable` Interface in Java** 🔄

### **📜 Definition**

* **Package:** `java.lang`
* **Purpose:**
  The **root interface** for all collection classes that can be iterated using the **enhanced for-loop** (`for-each loop`) or an **Iterator**.
  It’s a **generic interface**:

  ```java
  public interface Iterable<T>
  ```

---

### **📌 Key Points**

| Feature                   | Description                                                                                           |
| ------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Root Interface**        | All collection interfaces (`Collection`, `List`, `Set`, `Queue`) extend `Iterable`.                   |
| **Method**                | It has **only one abstract method**: `Iterator<T> iterator()`                                         |
| **For-each Support**      | Enables use of the `for-each` loop.                                                                   |
| **Functional Interface?** | No ❌ (It has a single abstract method but also a default method, so it’s not a functional interface). |
| **Default Methods**       | Java 8 added `forEach(Consumer<? super T> action)` and `spliterator()`.                               |

---

### **📂 Methods in `Iterable`**

| Method                                             | Description                                               | Since |
| -------------------------------------------------- | --------------------------------------------------------- | ----- |
| `Iterator<T> iterator()`                           | Returns an **Iterator** over elements of type `T`.        | 1.5   |
| `default void forEach(Consumer<? super T> action)` | Performs the given action for each element.               | 1.8   |
| `default Spliterator<T> spliterator()`             | Creates a **Spliterator** for parallel stream processing. | 1.8   |

---

### **⚙️ How it Works**

The **Enhanced for-loop**:

```java
for (ElementType element : iterableCollection) {
    // process element
}
```

is internally converted by the compiler into:

```java
Iterator<ElementType> it = iterableCollection.iterator();
while (it.hasNext()) {
    ElementType element = it.next();
    // process element
}
```

---

### **💻 Example**

```java
import java.util.*;

public class IterableExample {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("🍎 Apple", "🍌 Banana", "🍇 Grape");

        // Using for-each loop (Iterable)
        for (String fruit : fruits) {
            System.out.println(fruit);
        }

        // Using iterator() directly
        Iterator<String> itr = fruits.iterator();
        while (itr.hasNext()) {
            System.out.println("Iterator: " + itr.next());
        }

        // Using forEach() method (Java 8)
        fruits.forEach(f -> System.out.println("forEach: " + f));
    }
}
```

**Output:**

```
🍎 Apple
🍌 Banana
🍇 Grape
Iterator: 🍎 Apple
Iterator: 🍌 Banana
Iterator: 🍇 Grape
forEach: 🍎 Apple
forEach: 🍌 Banana
forEach: 🍇 Grape
```

---

### **📊 Where `Iterable` Fits in JCF Hierarchy**

```
Iterable (root)
   ↑
Collection
   ↑
List / Set / Queue
```

---

### **🛠 Real-world Analogy**

Think of `Iterable` like a **remote control interface** 📺 —
It doesn’t care about *what* device you’re controlling (TV, AC, Speaker),
it just ensures you have a **next button** and a **way to loop** over stuff.

---

### **✅ Best Practices**

* Always prefer **for-each loop** when you **don’t need index manipulation**.
* Use `iterator()` when you need **custom traversal** or **safe removal** during iteration.
* Use `forEach()` for concise, **Java 8+ lambda-friendly** iteration.

---
