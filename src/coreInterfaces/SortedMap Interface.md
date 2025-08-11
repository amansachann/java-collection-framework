# **SortedMap Interface in Java** 📜

**Definition:**
The **`SortedMap<K, V>`** interface (in `java.util`) is a **sub-interface of Map** that stores its entries **in ascending key order** according to the **natural ordering** of keys or a **custom comparator**.

It’s like a **Map** 📦 but with an **ordered arrangement** of keys.

---

### **Key Points** 🧠

* **Keys are sorted** automatically.
* Sorting is done either by:

    * **Natural ordering** (key must implement `Comparable`).
    * **Custom ordering** (provided via `Comparator` in the constructor).
* **No duplicate keys** allowed.
* **Null keys**:

    * Not allowed in **TreeMap** (most common SortedMap implementation).
* **Null values**: Allowed.
* **Main Implementations**:

    * `TreeMap` 🌳 (most used)
    * `ConcurrentSkipListMap` ⚡ (thread-safe, concurrent version)

---

### **Hierarchy Diagram** 📊

```
Map
│
├── SortedMap
│     └── NavigableMap
│           ├── TreeMap
│           └── ConcurrentSkipListMap
```

---

### **Important Methods in SortedMap** 🛠

| **Method**                                   | **Description**                                                               |
| -------------------------------------------- | ----------------------------------------------------------------------------- |
| `Comparator<? super K> comparator()`         | Returns the comparator used for ordering keys, or `null` if natural ordering. |
| `SortedMap<K, V> subMap(K fromKey, K toKey)` | Returns a view of the map from `fromKey` (inclusive) to `toKey` (exclusive).  |
| `SortedMap<K, V> headMap(K toKey)`           | Returns a view of keys strictly less than `toKey`.                            |
| `SortedMap<K, V> tailMap(K fromKey)`         | Returns a view of keys greater than or equal to `fromKey`.                    |
| `K firstKey()`                               | Returns the **lowest** key in the map.                                        |
| `K lastKey()`                                | Returns the **highest** key in the map.                                       |

---

### **Example 1 — Natural Ordering** 🌱

```java
import java.util.*;

public class SortedMapExample {
    public static void main(String[] args) {
        SortedMap<Integer, String> map = new TreeMap<>();

        map.put(3, "Banana");
        map.put(1, "Apple");
        map.put(2, "Mango");

        System.out.println("SortedMap: " + map);
        System.out.println("First Key: " + map.firstKey());
        System.out.println("Last Key: " + map.lastKey());
        System.out.println("HeadMap (keys < 3): " + map.headMap(3));
        System.out.println("TailMap (keys >= 2): " + map.tailMap(2));
    }
}
```

**Output:**

```
SortedMap: {1=Apple, 2=Mango, 3=Banana}
First Key: 1
Last Key: 3
HeadMap (keys < 3): {1=Apple, 2=Mango}
TailMap (keys >= 2): {2=Mango, 3=Banana}
```

---

### **Example 2 — Custom Comparator** 🎯

```java
import java.util.*;

public class CustomSortedMap {
    public static void main(String[] args) {
        SortedMap<String, Integer> map = new TreeMap<>(Comparator.reverseOrder());

        map.put("Banana", 3);
        map.put("Apple", 1);
        map.put("Mango", 2);

        System.out.println("Reverse Ordered Map: " + map);
    }
}
```

**Output:**

```
Reverse Ordered Map: {Mango=2, Banana=3, Apple=1}
```

---

### **When to Use SortedMap?** ✅

* When you need a **map with predictable sorted order** of keys.
* When **range queries** (`subMap`, `headMap`, `tailMap`) are required.
* When binary search–like performance is useful for lookups.

---

### **Time Complexity (TreeMap)** ⏳

| **Operation**     | **Complexity** |
| ----------------- | -------------- |
| Insert (`put`)    | O(log n)       |
| Search (`get`)    | O(log n)       |
| Delete (`remove`) | O(log n)       |

