# **NavigableMap Interface in Java** 🗺️🚦

### **Definition**

* **`NavigableMap<K, V>`** is a subinterface of **`SortedMap<K, V>`**.
* It provides **navigation methods** to **find closest matches** for keys, in addition to normal `SortedMap` functionality.
* Typically implemented by **`TreeMap`**.

---

## **Hierarchy** 📚

```
Map<K, V>
   ↑
SortedMap<K, V>
   ↑
NavigableMap<K, V>
```

**Main Implementation:** ✅ `TreeMap` (Red-Black Tree based, keeps keys sorted in natural order or by a custom Comparator).

---

## **Key Features** 🌟

* **Sorted Order** ➡️ Maintains keys in ascending order (default).
* **Navigation Methods** ➡️ Find nearest keys (lower, higher, floor, ceiling).
* **Submaps** ➡️ Get head/tail/sub maps with flexible bounds.
* **Descending Views** ➡️ Reverse order views.

---

## **Important Methods in NavigableMap** 🛠️

| Method                                                                   | Description                                    | Example Output                |
| ------------------------------------------------------------------------ | ---------------------------------------------- | ----------------------------- |
| `lowerKey(K key)`                                                        | Returns **key < given key** (strictly lower).  | `lowerKey(20)` → `15`         |
| `floorKey(K key)`                                                        | Returns **key ≤ given key**.                   | `floorKey(20)` → `20`         |
| `ceilingKey(K key)`                                                      | Returns **key ≥ given key**.                   | `ceilingKey(20)` → `20`       |
| `higherKey(K key)`                                                       | Returns **key > given key**.                   | `higherKey(20)` → `25`        |
| `descendingMap()`                                                        | Returns map in reverse order.                  | `{50=Z, 40=Y, ...}`           |
| `headMap(K toKey, boolean inclusive)`                                    | All keys less than (or equal if inclusive).    | `headMap(30, true)`           |
| `tailMap(K fromKey, boolean inclusive)`                                  | All keys greater than (or equal if inclusive). | `tailMap(30, false)`          |
| `subMap(K fromKey, boolean fromInclusive, K toKey, boolean toInclusive)` | Keys between two values with bounds control.   | `subMap(20, true, 40, false)` |

---

## **Code Example** 💻

```java
import java.util.*;

public class NavigableMapDemo {
    public static void main(String[] args) {
        NavigableMap<Integer, String> map = new TreeMap<>();
        
        map.put(10, "A");
        map.put(20, "B");
        map.put(30, "C");
        map.put(40, "D");
        map.put(50, "E");

        System.out.println("Map: " + map);
        System.out.println("Lower Key(30): " + map.lowerKey(30));    // 20
        System.out.println("Floor Key(30): " + map.floorKey(30));    // 30
        System.out.println("Ceiling Key(25): " + map.ceilingKey(25));// 30
        System.out.println("Higher Key(30): " + map.higherKey(30));  // 40

        System.out.println("Descending Map: " + map.descendingMap());
        System.out.println("Head Map(30, true): " + map.headMap(30, true));
        System.out.println("Tail Map(30, false): " + map.tailMap(30, false));
        System.out.println("Sub Map(20, true, 40, false): " + 
                           map.subMap(20, true, 40, false));
    }
}
```

---

## **Output** 🖨️

```
Map: {10=A, 20=B, 30=C, 40=D, 50=E}
Lower Key(30): 20
Floor Key(30): 30
Ceiling Key(25): 30
Higher Key(30): 40
Descending Map: {50=E, 40=D, 30=C, 20=B, 10=A}
Head Map(30, true): {10=A, 20=B, 30=C}
Tail Map(30, false): {40=D, 50=E}
Sub Map(20, true, 40, false): {20=B, 30=C}
```

---

## **Real-World Example** 🌍

Imagine you’re building a **train timetable app** 🚆:

* Keys → Departure times (HHMM format)
* Values → Train details
  You can use:
* `ceilingKey()` to find the **next available train** after a given time.
* `floorKey()` to find the **last train before now**.
* `subMap()` to get all trains between **6 AM and 10 AM**.

---

## **Best Practices** ✅

* **Use TreeMap** when you need **sorted keys + navigation methods**.
* Avoid **Null keys** in `TreeMap` (throws `NullPointerException`).
* Prefer **Immutable Maps** for read-only navigation to ensure thread-safety.
* For **concurrent navigation**, use **`ConcurrentSkipListMap`**.


