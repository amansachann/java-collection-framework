# 📜 **List Interface in Java**

* **Package**: `java.util`
* **Inheritance**:
  `Iterable` → `Collection` → **`List`**
* **Nature**: Ordered, **index-based** collection that allows **duplicate elements**.
* **Type**: Interface (must be implemented by classes like `ArrayList`, `LinkedList`, etc.).

---

### 🚀 **Key Features**

| Feature                | Description                                                     |
| ---------------------- | --------------------------------------------------------------- |
| **Order Maintained**   | Insertion order is preserved.                                   |
| **Index Based Access** | Elements can be accessed, inserted, or removed via index.       |
| **Allows Duplicates**  | Same element can appear multiple times.                         |
| **Allows Null**        | Multiple `null` values are allowed.                             |
| **Generic Support**    | Can store specific types using Generics (e.g., `List<String>`). |

---

### 🛠 **Commonly Used Implementations**

| Implementation | Description                                                      | When to Use                     |
| -------------- | ---------------------------------------------------------------- | ------------------------------- |
| **ArrayList**  | Dynamic array, fast random access, slow insert/remove in middle. | Read-heavy operations.          |
| **LinkedList** | Doubly linked list, fast insert/remove, slow random access.      | Frequent insert/delete.         |
| **Vector**     | Synchronized version of ArrayList (legacy).                      | Thread-safe needs, legacy code. |
| **Stack**      | LIFO (Last-In-First-Out) based on Vector.                        | Stack data structure needs.     |

---

### 🏗 **Important Methods**

| Method                      | Description                                           |
| --------------------------- | ----------------------------------------------------- |
| `add(E e)`                  | Appends element at the end.                           |
| `add(int index, E e)`       | Inserts element at a specific index.                  |
| `get(int index)`            | Retrieves element by index.                           |
| `set(int index, E e)`       | Updates element at given index.                       |
| `remove(int index)`         | Removes element at given index.                       |
| `indexOf(Object o)`         | Returns first occurrence index.                       |
| `lastIndexOf(Object o)`     | Returns last occurrence index.                        |
| `listIterator()`            | Returns a `ListIterator` for bidirectional traversal. |
| `subList(int from, int to)` | Returns a portion of the list.                        |

---

### 💻 **Example**

```java
import java.util.*;

public class ListExample {
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>();

        // Adding elements
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Mango");
        fruits.add("Banana"); // duplicate allowed
        fruits.add(null); // null allowed

        // Access by index
        System.out.println("First Fruit: " + fruits.get(0));

        // Update
        fruits.set(1, "Orange");

        // Remove
        fruits.remove(2);

        // Traversal
        for (String fruit : fruits) {
            System.out.println(fruit);
        }

        // Sublist
        System.out.println("First Two: " + fruits.subList(0, 2));
    }
}
```

**Output:**

```
First Fruit: Apple
Apple
Orange
Banana
null
First Two: [Apple, Orange]
```

---

### 📊 **Hierarchy Diagram**

```
Iterable
   ↑
Collection
   ↑
List
 ┌───────────────┬──────────────┬─────────┬────────────┐
ArrayList    LinkedList     Vector     Stack
```

---

### 🏆 **Best Practices**

* ✅ Use **`ArrayList`** for **random access**.
* ✅ Use **`LinkedList`** for **frequent insert/delete**.
* ✅ Use **Generics** to avoid `ClassCastException`.
* ✅ For **thread-safe** lists, use `Collections.synchronizedList()` or `CopyOnWriteArrayList`.
* ⚠ Avoid `Vector` unless working with **legacy** code.

