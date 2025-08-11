# **Queue Interface in Java** 📦🚶

### **Definition**

* `Queue<E>` is part of **Java Collections Framework**.
* **FIFO** (First-In-First-Out) data structure 📤📥 — elements are added at the **rear** and removed from the **front**.
* Located in `java.util` package.
* Extends **Collection** interface.

---

### **Hierarchy** 📊

```
Iterable
   ↑
Collection
   ↑
Queue
   ↑
PriorityQueue / LinkedList / ArrayDeque / etc.
```

---

### **Key Methods** (from `Queue` interface) 📜

| **Method**           | **Description**                                                                             |
| -------------------- | ------------------------------------------------------------------------------------------- |
| `boolean add(E e)`   | Inserts element into the queue. Throws exception if capacity is full.                       |
| `boolean offer(E e)` | Inserts element into the queue. Returns `false` if capacity is full (preferred over `add`). |
| `E remove()`         | Removes and returns head element. Throws exception if queue is empty.                       |
| `E poll()`           | Removes and returns head element. Returns `null` if queue is empty.                         |
| `E element()`        | Retrieves head element without removing. Throws exception if queue is empty.                |
| `E peek()`           | Retrieves head element without removing. Returns `null` if queue is empty.                  |

💡 **Best Practice**: Use `offer()`, `poll()`, and `peek()` to avoid exceptions.

---

### **Types of Queues in Java** 🧩

| **Type**                 | **Class Examples**                          | **Special Feature**                                   |
| ------------------------ | ------------------------------------------- | ----------------------------------------------------- |
| **Normal Queue**         | `LinkedList`, `ArrayDeque`                  | FIFO ordering.                                        |
| **Priority Queue**       | `PriorityQueue`                             | Orders elements based on natural order or comparator. |
| **Deque** (Double-Ended) | `ArrayDeque`, `LinkedList`                  | Insert/remove from both ends.                         |
| **Blocking Queue**       | `ArrayBlockingQueue`, `LinkedBlockingQueue` | Thread-safe, used in concurrency.                     |
| **Concurrent Queue**     | `ConcurrentLinkedQueue`                     | Lock-free thread-safe queue.                          |

---

### **Example – Basic Queue Usage** 🎯

```java
import java.util.*;

public class QueueExample {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();

        // Adding elements
        queue.offer("Aman");
        queue.offer("Sachin");
        queue.offer("Raj");

        System.out.println("Queue: " + queue); // [Aman, Sachin, Raj]

        // Removing head
        System.out.println("Removed: " + queue.poll()); // Aman
        System.out.println("Head: " + queue.peek());    // Sachin
        System.out.println("Updated Queue: " + queue);  // [Sachin, Raj]
    }
}
```

---

### **Real-World Analogy** 🏦

Think of a **bank queue** 🏦:

* First person to join → First person served ✅
* People **leave from the front** and **join from the back**.

---

### **Best Practices** 💡

* **Prefer `offer()`, `poll()`, and `peek()`** over `add()`, `remove()`, and `element()` to avoid exceptions.
* Use **`PriorityQueue`** when you need automatic ordering.
* Use **BlockingQueue** (`ArrayBlockingQueue`, `LinkedBlockingQueue`) in multi-threaded producer-consumer scenarios.


