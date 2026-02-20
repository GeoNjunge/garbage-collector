## Mark-and-Sweep Garbage Collector in C

**A simple implementation of a mark-and-sweep garbage collector using C and pointers.**

This project demonstrates the fundamental concepts of **memory management, heap allocation, and object reachability**. Ideal for anyone learning low-level programming, interpreters, or building a small virtual machine.

---

### 🔹 Features

- **Heap management**: Allocate objects dynamically using `malloc`.
- **Stack-based VM simulation**: Track variables currently in scope.
- **Mark phase**: Recursively marks all reachable objects from the stack.
- **Sweep phase**: Frees unmarked objects and reclaims memory.
- **Pairs & integers**: Supports tagged union objects with integers or linked pairs.
- **Dynamic GC triggering**: Garbage collection runs when object count exceeds a threshold.

---

### 🔹 Why This Project Matters

Understanding **manual memory management** and **garbage collection algorithms** is crucial for:

- Programming language interpreters
- Virtual machines
- Systems programming
- Optimizing low-level code for performance

---

### 🔹 Project Structure

```text
gc-c/
├── gc.c            # Core implementation
├── test.sh         # Run the program
└── README.md       # Project documentation
```

---

### 🔹 How to run the program

$ ./tesh.sh

    Enter the name of the C file: gc.c
    🛠️ Compiling 'gc.c'...

---

### 🔹 How It Works

1. **Stack Simulation**:
   Objects are pushed onto the VM stack as variables come into scope.

2. **Mark Phase**:
   - Walk the stack.
   - Recursively mark all reachable objects (avoid cycles).

3. **Sweep Phase**:
   - Traverse the heap list.
   - Free objects not marked in the mark phase.
   - Reset marked flags for the next GC cycle.

4. **Dynamic Threshold**:
   - GC is triggered when `numObjects >= maxObjects`.
   - `maxObjects` doubles after each collection to balance performance.

---

### 🔹 Example Usage

```c
int main() {
    VM *vm = newVM();

    pushInt(vm, 1);
    pushInt(vm, 2);
    pushPair(vm); // creates pair (1,2)

    gc(vm); // runs garbage collection

    return 0;
}
```

---

### 🔹 Future Improvements

- Track the number of objects created over time.
- Implement generational GC (separating young & old objects).
- Add logging and statistics for GC runs.
- Support more complex object types and references.

---

### 🔹 Learning Goals

This project is meant as a **learning exercise**:

- Understand memory management at a low level.
- Learn how garbage collectors work under the hood.
- Gain confidence with pointers, structs, and recursion in C.

---

### 🔹 License

MIT
