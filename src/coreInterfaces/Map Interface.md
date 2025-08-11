# **Map Interface** 🗺️

The **`Map<K, V>`** interface in Java represents a **collection of key-value pairs** where:

* **Keys** are unique (no duplicates allowed 🚫).
* **Values** can be duplicated ✅.
* Each key maps to at most **one value**.

📦 **Package:** `java.util`  
📜 **Declaration:**  

```java
public interface Map<K, V>
```

---

### **Key Characteristics** 🌟

| Feature                    | Description                                                                                             |
| -------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Duplicates in Keys** ❌   | Keys must be unique.                                                                                    |
| **Duplicates in Values** ✅ | Multiple keys can have the same value.                                                                  |
| **Null Support**           | `HashMap` → 1 null key, multiple null values; `Hashtable` → no null key or null value.                  |
| **Order**                  | Depends on the implementation (`HashMap` unordered, `LinkedHashMap` insertion order, `TreeMap` sorted). |
| **Performance**            | Lookup, insert, delete in O(1) for hash-based maps.                                                     |

---

### **Core Methods** 🛠️

| Method                                         | Description                                    |
| ---------------------------------------------- | ---------------------------------------------- |
| `V put(K key, V value)`                        | Inserts/updates a key-value pair.              |
| `V get(Object key)`                            | Returns the value for the given key.           |
| `boolean containsKey(Object key)`              | Checks if key exists.                          |
| `boolean containsValue(Object value)`          | Checks if value exists.                        |
| `V remove(Object key)`                         | Removes key-value pair by key.                 |
| `Set<K> keySet()`                              | Returns all keys as a `Set`.                   |
| `Collection<V> values()`                       | Returns all values as a `Collection`.          |
| `Set<Map.Entry<K, V>> entrySet()`              | Returns all entries as a `Set` of `Map.Entry`. |
| `void putAll(Map<? extends K, ? extends V> m)` | Copies all entries from another map.           |
| `void clear()`                                 | Removes all mappings.                          |
| `int size()`                                   | Returns number of entries.                     |
| `boolean isEmpty()`                            | Checks if map has no entries.                  |

---

### **Example Usage** 💻

```java
import java.util.*;

public class MapExample {
    public static void main(String[] args) {
        Map<Integer, String> map = new HashMap<>();

        // Adding elements
        map.put(1, "Apple");
        map.put(2, "Banana");
        map.put(3, "Cherry");

        // Accessing elements
        System.out.println(map.get(2)); // Banana

        // Iterating over keys
        for (Integer key : map.keySet()) {
            System.out.println(key + " => " + map.get(key));
        }

        // Using entrySet
        for (Map.Entry<Integer, String> entry : map.entrySet()) {
            System.out.println(entry.getKey() + " -> " + entry.getValue());
        }
    }
}
```

---

### **Common Implementations** 🏗️

| Class                 | Ordering        | Null Key  | Null Values      | Thread-Safe          |
| --------------------- | --------------- | --------- | ---------------- | -------------------- |
| **HashMap**           | No order        | 1 allowed | Multiple allowed | ❌                    |
| **LinkedHashMap**     | Insertion order | 1 allowed | Multiple allowed | ❌                    |
| **TreeMap**           | Sorted by key   | ❌         | Multiple allowed | ❌                    |
| **Hashtable**         | No order        | ❌         | ❌                | ✅                    |
| **ConcurrentHashMap** | No order        | ❌         | ❌                | ✅ (high concurrency) |

---

### **Best Practices** 💡

* Use **`HashMap`** for general-purpose lookups when order doesn’t matter.
* Use **`LinkedHashMap`** when you need predictable iteration order.
* Use **`TreeMap`** for sorted keys.
* For multi-threaded environments → **`ConcurrentHashMap`**.
* Avoid `Hashtable` in modern code (legacy).

