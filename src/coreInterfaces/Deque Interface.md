# **Deque Interface** 🔄

**Full form** → *Double Ended Queue*
📦 **Package**: `java.util`
🔗 **Extends**: `Queue` interface

A **Deque** allows **insertion and removal from both ends** — front (head) and rear (tail).
It can be used as:

* **Queue** → FIFO (First In First Out)
* **Stack** → LIFO (Last In First Out)

---

### **Key Points** 📌

* Supports **null** elements **only** if implementation allows (e.g., `LinkedList` does; `ArrayDeque` doesn’t).
* More versatile than a normal `Queue`.
* Introduced in **Java 6**.

---

### **Method Summary** 📜

| **Method**        | **Description**                                     |
| ----------------- | --------------------------------------------------- |
| `addFirst(E e)`   | Inserts at the front, throws exception if full.     |
| `addLast(E e)`    | Inserts at the rear, throws exception if full.      |
| `offerFirst(E e)` | Inserts at front, returns `false` if full.          |
| `offerLast(E e)`  | Inserts at rear, returns `false` if full.           |
| `removeFirst()`   | Removes first element, throws exception if empty.   |
| `removeLast()`    | Removes last element, throws exception if empty.    |
| `pollFirst()`     | Removes first element, returns `null` if empty.     |
| `pollLast()`      | Removes last element, returns `null` if empty.      |
| `getFirst()`      | Retrieves first element, throws exception if empty. |
| `getLast()`       | Retrieves last element, throws exception if empty.  |
| `peekFirst()`     | Retrieves first element, returns `null` if empty.   |
| `peekLast()`      | Retrieves last element, returns `null` if empty.    |

---

### **Example** 💻

```java
import java.util.*;

public class DequeExample {
    public static void main(String[] args) {
        Deque<String> dq = new ArrayDeque<>();

        // Adding elements
        dq.addFirst("Aman");
        dq.addLast("Sachan");
        dq.offerFirst("Mr.");
        dq.offerLast("JavaGuru");

        System.out.println("Deque: " + dq);

        // Removing elements
        dq.removeFirst();
        dq.pollLast();

        System.out.println("After removals: " + dq);

        // Peeking
        System.out.println("First: " + dq.peekFirst());
        System.out.println("Last: " + dq.peekLast());
    }
}
```

**Output**:

```
Deque: [Mr., Aman, Sachan, JavaGuru]
After removals: [Aman, Sachan]
First: Aman
Last: Sachan
```

---

### **Real-Life Analogy** 🚌

Think of a **double-door bus** — passengers can **enter or exit from both the front and rear** doors.

* Front door = `First` operations
* Rear door = `Last` operations

---

### **Common Implementations** 🏗️

| **Class**    | **Characteristics**                                                                                                               |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| `ArrayDeque` | Resizable array-based, no capacity limit, **faster than `Stack` & `LinkedList`** for stack/queue operations, **no null allowed**. |
| `LinkedList` | Doubly-linked list-based, allows nulls, slightly slower than `ArrayDeque`.                                                        |

---

### **When to Use Deque?** 🤔

* When you need both **queue and stack** operations in a single structure.
* When you want **fast insertion/removal from both ends**.
* When **thread-safety is not needed** (else, use `ConcurrentLinkedDeque`).

