# **NavigableSet Interface** 🧭

**Definition:**
`NavigableSet` is a **subinterface of `SortedSet`** in Java that provides **navigation methods** to traverse the set in ascending or descending order and to find closest matches for given elements.

📍 **Package:** `java.util`
📍 **Implementations:**

* ✅ `TreeSet` 🌳 (most common)
* ❌ `ConcurrentSkipListSet` (for concurrent, sorted sets)

---

### **Key Features** ⚡

* Maintains **sorted order** of elements.
* Supports **navigation methods** like:

    * Find **lower**, **floor**, **ceiling**, **higher** elements.
    * Reverse order iteration.
    * Get subsets based on element range.
* No duplicates allowed ❌.

---

### **Important Methods** 📜

| **Method**                                                                         | **Description**                                   | **Example**                 |
| ---------------------------------------------------------------------------------- | ------------------------------------------------- | --------------------------- |
| `E lower(E e)`                                                                     | Returns greatest element **less than** `e`.       | lower(50) → 40              |
| `E floor(E e)`                                                                     | Returns greatest element **≤** `e`.               | floor(50) → 50              |
| `E ceiling(E e)`                                                                   | Returns smallest element **≥** `e`.               | ceiling(50) → 50            |
| `E higher(E e)`                                                                    | Returns smallest element **greater than** `e`.    | higher(50) → 60             |
| `E pollFirst()`                                                                    | Removes & returns **first (lowest)** element.     | pollFirst() → 10            |
| `E pollLast()`                                                                     | Removes & returns **last (highest)** element.     | pollLast() → 90             |
| `NavigableSet<E> descendingSet()`                                                  | Returns elements in **reverse order**.            | —                           |
| `Iterator<E> descendingIterator()`                                                 | Returns reverse order iterator.                   | —                           |
| `NavigableSet<E> subSet(E from, boolean fromInclusive, E to, boolean toInclusive)` | Returns range view with control over inclusivity. | subSet(20, true, 50, false) |

---

### **Example Code** 💻

```java
import java.util.*;

public class NavigableSetExample {
    public static void main(String[] args) {
        NavigableSet<Integer> numbers = new TreeSet<>(Arrays.asList(10, 20, 30, 40, 50, 60));

        System.out.println("Original Set: " + numbers);
        System.out.println("Lower than 30: " + numbers.lower(30));       // 20
        System.out.println("Floor of 30: " + numbers.floor(30));         // 30
        System.out.println("Ceiling of 35: " + numbers.ceiling(35));     // 40
        System.out.println("Higher than 40: " + numbers.higher(40));     // 50

        System.out.println("Descending Set: " + numbers.descendingSet());
        System.out.println("SubSet (20 inclusive to 50 exclusive): " + 
                           numbers.subSet(20, true, 50, false));

        System.out.println("Poll First: " + numbers.pollFirst()); // Removes 10
        System.out.println("Poll Last: " + numbers.pollLast());   // Removes 60
        System.out.println("After Poll: " + numbers);
    }
}
```

---

### **When to Use NavigableSet?** 🎯

* When you need a **sorted, unique collection** ✅.
* When you need **quick lookups for nearest elements** (e.g., auto-suggestions, range queries).
* When **range-based operations** are required (e.g., between two dates).

---

### **Best Practices** 💡

* Use **TreeSet** when you need ordering with navigation methods.
* For **concurrent** needs → use `ConcurrentSkipListSet`.
* Avoid `null` elements in `NavigableSet` — `TreeSet` doesn’t allow them.
* Use **custom Comparator** if you want custom ordering.

---

### **Real-World Analogy** 🌍

Think of `NavigableSet` like **Google Maps search**:

* `lower()` → find the next smaller city before your target.
* `higher()` → find the next city after your target.
* `subSet()` → list all cities between CityA and CityB.
* `descendingSet()` → reverse the route order.

