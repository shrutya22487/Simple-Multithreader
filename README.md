# 🧵 SimpleMultithreader (C++ / Pthreads)

A **header-only multithreading abstraction** built on top of **POSIX Pthreads**, designed to make parallel programming **simple, concise, and reusable**.
This project abstracts away low-level thread management while exposing an intuitive **`parallel_for` API using C++11 lambdas**.
---

## ✨ Key Features

✅ Header-only implementation (`simple-multithreader.h`)
✅ Uses **Pthreads** (no `std::thread`, no thread pool)
✅ Supports **1D and 2D parallel for-loops**
✅ C++11 **lambda-based API**
✅ Exact number of threads as specified (including main thread)
✅ Threads are created **per invocation** and destroyed after use
✅ Prints **execution time** for every `parallel_for` call

---

## 📂 Repository Structure

```
.
├── simple-multithreader.h   # Header-only multithreading library
├── example1.cpp             # Sample program (1D parallel_for)
├── example2.cpp             # Sample program (2D parallel_for)
├── Makefile                 # Build configuration
├── README.md                # Documentation
```

---

## ⚙️ System Requirements

* Linux / WSL (Unix APIs required)
* GCC / G++
* GNU Make
* POSIX Threads (`pthread`)

> ⚠️ macOS is **not recommended** for OS-level assignments relying on Unix internals 

---

## 🚀 How to Compile & Run

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/shrutya22487/OS_Assignment_5.git
cd OS_Assignment_5
```

### 2️⃣ Compile

```bash
make
```

(Manual compilation)

```bash
g++ -std=c++11 example1.cpp -pthread -o example1
g++ -std=c++11 example2.cpp -pthread -o example2
```

### 3️⃣ Run

```bash
./example1
./example2
```

---

## 🧠 API Overview

### 🔹 1D Parallel Loop

```cpp
void parallel_for(
    int low,
    int high,
    std::function<void(int)> &&lambda,
    int numThreads
);
```

### 🔹 2D Parallel Loop

```cpp
void parallel_for(
    int low1, int high1,
    int low2, int high2,
    std::function<void(int, int)> &&lambda,
    int numThreads
);
```

---

## 🧪 Example Usage

### 1D Parallel Loop

```cpp
parallel_for(0, n, [&](int i) {
    sum[i] = arr[i] * 2;
}, 4);
```

### 2D Parallel Loop

```cpp
parallel_for(0, n, 0, m, [&](int i, int j) {
    matrix[i][j] += 1;
}, 8);
```

---

## ⏱️ Performance Reporting

For every `parallel_for` call, the library automatically prints:

* Total execution time
* Number of threads used

This helps in **benchmarking parallel vs sequential performance**.

---

## ⚠️ Design Constraints & Limitations

* ❌ No thread pool (threads are created per call)
* ❌ No `std::thread`, `std::async`, or OpenMP
* ❌ No dynamic task scheduling
* ✔️ Strictly follows assignment specifications

These constraints are **intentional** and mandated by the assignment rubric .

---

## 🧩 Concepts Applied

* POSIX Threads (`pthread_create`, `pthread_join`)
* Work partitioning
* Lambda capture & invocation
* Synchronization through structured execution
* Execution time measurement


Tell me what you want next.
