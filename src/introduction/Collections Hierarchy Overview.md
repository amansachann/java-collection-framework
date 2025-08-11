# **📌 Java Collections Hierarchy Overview**

The **Java Collections Framework (JCF)** is built on **interfaces** at the top, with **implementations** (classes) underneath, organized in a tree-like structure.

---

### **1️⃣ Root of the Hierarchy**

* **`Iterable`** *(java.lang)* → The **root interface** for all collection classes that can be iterated with `for-each`.

    * `for (T item : collection) { ... }`
    * Methods: `iterator()`

---

### **2️⃣ Branch 1 – The `Collection` Interface**

*(extends `Iterable`)*
Represents a group of **individual objects**.

#### **Main Subinterfaces of `Collection`**

| Interface    | Description                                      | Key Implementations                          |
| ------------ | ------------------------------------------------ | -------------------------------------------- |
| **List** 📜  | Ordered collection (allows duplicates).          | `ArrayList`, `LinkedList`, `Vector`, `Stack` |
| **Set** 🚫   | Unordered, unique elements (no duplicates).      | `HashSet`, `LinkedHashSet`, `TreeSet`        |
| **Queue** 📥 | Ordered by processing order (FIFO/LIFO).         | `PriorityQueue`, `ArrayDeque`                |
| **Deque** ↔️ | Double-ended queue (insert/remove at both ends). | `ArrayDeque`, `LinkedList`                   |

---

### **3️⃣ Branch 2 – The `Map` Interface**

*(NOT a child of `Collection`, but part of JCF)*
Stores **key-value pairs**, where keys are unique.

| Interface           | Description                             | Key Implementations                                |
| ------------------- | --------------------------------------- | -------------------------------------------------- |
| **Map** 🗺️         | Unique keys, values may duplicate.      | `HashMap`, `LinkedHashMap`, `TreeMap`, `Hashtable` |
| **SortedMap** 📈    | Keys in sorted order.                   | `TreeMap`                                          |
| **NavigableMap** 🧭 | Extended sorting & navigation features. | `TreeMap`                                          |

---

### **4️⃣ Complete Hierarchy Diagram**

```
          Iterable
             ↑
        Collection
        /    |    \
     List   Set   Queue
     ↑      ↑      ↑
 ArrayList  ↑   PriorityQueue
 LinkedList HashSet  ArrayDeque
 Vector   LinkedHashSet
 Stack    SortedSet
          ↑
        TreeSet

 Map
 ↑
SortedMap
 ↑
NavigableMap
 ↑
TreeMap
```

---

### **5️⃣ Key Points to Remember**

* **`Collection`** → deals with **elements** (single values).
* **`Map`** → deals with **key-value pairs**.
* Interfaces define the contract 📜, classes provide the implementation 🔧.
* Use **interfaces for type reference** and **classes for instantiation**.

---

💡 **Real-life Analogy**

* **Collection** → A shopping bag 🛍️ (you put items one after another).
* **Map** → A dictionary 📖 (each word maps to a meaning).

