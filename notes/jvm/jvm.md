### JVM Memory Structure Overview

JVM memory is mainly divided into:

 -  Heap
 -  Stack
 -  Metaspace
 -  PC Register
 -  Native Method Stack

Heap stores objects and is managed by GC, 
Stack is thread-specific and stores method calls and local variables, 
and Metaspace stores class metadata in native memory. Efficient memory management and GC tuning are critical for application performance.

 
### 📦 1. Heap Memory (Shared)

👉 Used to store **objects and instance variables**

### Key Points:

-   Shared across all threads
-   Managed by **Garbage Collector**
-   Divided into:

Heap  
 ├── Young Generation  
 │    ├── Eden  
 │    ├── Survivor S0  
 │    └── Survivor S1  
 └── Old Generation

----------

### 🔄 How it works:

1.  New objects → created in **Eden**
2.  Survive GC → move to **Survivor**
3.  Long-lived → move to **Old Gen**

----------

### ⚠️ Issues:

-   **OutOfMemoryError: Java heap space**
-   Frequent GC → performance issues

----------

### 🧠 Interview Tip:

> Heap is used for object storage and is managed by GC. Improper object creation or memory leaks can cause performance degradation.

----------

### 🧵 2. Stack Memory (Thread-Specific)

👉 Each thread has its own **Stack**

### Stores:

-   Method calls
-   Local variables
-   References (not actual objects)

----------

### 🔄 How it works:

Every method call creates a **stack frame**

void  main() {  
  int  a  =  10; // stored in stack  
  method1();  
}

----------

### ⚠️ Issues:

-   **StackOverflowError**
    -   Caused by deep recursion or infinite calls

----------

### 🧠 Key Point:

> Stack is fast and automatically managed (LIFO - Last In First Out)

----------

### 🧬 3. Metaspace (Class Metadata)

👉 Stores **class-level information**

Before Java 8 → **PermGen**  
After Java 8 → **Metaspace**

----------

### Stores:

-   Class definitions
-   Method metadata
-   Static variables
-   Constant pool

----------

### Key Difference:

-   Stored in **native memory (outside heap)**
-   Dynamically grows

----------

### ⚠️ Issues:

-   **OutOfMemoryError: Metaspace**
    -   Too many classes loaded (e.g., dynamic proxies
