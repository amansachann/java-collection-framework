# **Set Interface in Java** 🗂️

### **Definition** 📜

* **Set** is a **Collection** that does **not allow duplicate elements**.
* At most **one null** element is allowed (depends on implementation).
* Elements are **unordered** (except in special cases like `LinkedHashSet` or `TreeSet`).

---

## **Hierarchy** 🏛️

```
Iterable
   ↑
Collection
   ↑
  Set
```

---

## **Key Points** 📌

| Feature                | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| **Duplicates**         | ❌ Not allowed                                                |
| **Order**              | ❌ No guarantee (depends on implementation)                   |
| **Null**               | ✅ 1 null allowed (except TreeSet if sorted by natural order) |
| **Index-based Access** | ❌ Not supported                                              |
| **Implementations**    | `HashSet`, `LinkedHashSet`, `TreeSet`                        |

---

## **Important Implementations** 🛠️

### **1. HashSet** 🧱

* **Backed by**: HashMap
* **Order**: ❌ No guaranteed order
* **Performance**: O(1) for add, remove, contains (average)
* **Nulls**: ✅ 1 allowed

```java
import java.util.*;

public class HashSetDemo {
    public static void main(String[] args) {
        Set<String> set = new HashSet<>();
        set.add("Apple");
        set.add("Banana");
        set.add("Apple"); // Duplicate ignored
        set.add(null);
        
        System.out.println(set); // Order not guaranteed
    }
}
```

---

### **2. LinkedHashSet** 🔗

* **Backed by**: LinkedHashMap
* **Order**: ✅ Maintains insertion order
* **Performance**: Slightly slower than HashSet due to linked list maintenance

```java
Set<String> set = new LinkedHashSet<>();
set.add("Apple");
set.add("Banana");
set.add("Cherry");
System.out.println(set); // [Apple, Banana, Cherry]
```

---

### **3. TreeSet** 🌳

* **Backed by**: TreeMap (Red-Black Tree)
* **Order**: ✅ Sorted (natural order or custom Comparator)
* **Performance**: O(log n) for add, remove, contains
* **Nulls**: ❌ Not allowed (NullPointerException for add)

```java
Set<Integer> set = new TreeSet<>();
set.add(30);
set.add(10);
set.add(20);
System.out.println(set); // [10, 20, 30] (sorted order)
```

---

## **When to Use What?** 🤔

| Use Case                       | Recommended Set   |
| ------------------------------ | ----------------- |
| Need fast lookup & no order    | **HashSet**       |
| Need insertion order preserved | **LinkedHashSet** |
| Need sorted elements           | **TreeSet**       |

---

## **Best Practices** 🏆

* Always choose the right Set implementation for **performance vs ordering** needs.
* Avoid using `TreeSet` when large data + no sorting needed (performance hit).
* Prefer `Collections.unmodifiableSet()` for read-only sets.

