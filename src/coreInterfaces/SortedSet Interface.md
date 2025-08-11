# **SortedSet Interface** 🗂️

The **`SortedSet<E>`** interface in Java is a **subinterface of `Set`** that maintains elements in **ascending sorted order** (as defined by their **natural ordering** or a specified **`Comparator`**).

It’s part of **`java.util`** package and is commonly implemented by **`TreeSet`** 🌳.

---

### **Key Points** ✨

* Maintains **unique** elements.
* Stores elements in **sorted order** automatically.
* Sorting is based on:

    * Natural ordering (`Comparable`)
    * Or a custom `Comparator` passed during creation.
* Allows efficient **range-based operations**.

---

### **Hierarchy Diagram** 🪜

```
Iterable
  ↑
Collection
  ↑
Set
  ↑
SortedSet
```

💡 Implemented by: **TreeSet**, **ConcurrentSkipListSet**

---

### **Important Methods** 🛠️

| Method                                            | Description                                                                     |
| ------------------------------------------------- | ------------------------------------------------------------------------------- |
| `Comparator<? super E> comparator()`              | Returns the comparator used for sorting, or `null` if natural ordering is used. |
| `E first()`                                       | Returns the first (lowest) element.                                             |
| `E last()`                                        | Returns the last (highest) element.                                             |
| `SortedSet<E> headSet(E toElement)`               | Returns a view of elements strictly less than `toElement`.                      |
| `SortedSet<E> tailSet(E fromElement)`             | Returns a view of elements greater than or equal to `fromElement`.              |
| `SortedSet<E> subSet(E fromElement, E toElement)` | Returns elements between `fromElement` (inclusive) and `toElement` (exclusive). |

---

### **Example** 💻

```java
import java.util.*;

public class SortedSetExample {
    public static void main(String[] args) {
        SortedSet<Integer> numbers = new TreeSet<>();
        
        numbers.add(50);
        numbers.add(10);
        numbers.add(30);
        numbers.add(20);

        System.out.println("SortedSet: " + numbers); // [10, 20, 30, 50]
        System.out.println("First: " + numbers.first()); // 10
        System.out.println("Last: " + numbers.last()); // 50
        System.out.println("HeadSet (<30): " + numbers.headSet(30)); // [10, 20]
        System.out.println("TailSet (>=30): " + numbers.tailSet(30)); // [30, 50]
        System.out.println("SubSet (20 to 50): " + numbers.subSet(20, 50)); // [20, 30]
    }
}
```

---

### **Real-World Analogy** 🌍

Think of **SortedSet** like a **guest list sorted alphabetically** at a wedding:

* No duplicate names allowed 🛑.
* Names are always in alphabetical order 🅰️➡️Z.
* You can easily get guests before or after a certain name.

---

### **Best Practices** 🏆

* ✅ Use **`TreeSet`** if you need sorted & unique elements.
* ✅ Provide a **custom `Comparator`** for non-natural sorting (e.g., reverse order, by length).
* ❌ Don’t use for random access — it’s optimized for **sorted traversal**.
* ⚡ For concurrent environments, use **`ConcurrentSkipListSet`**.

