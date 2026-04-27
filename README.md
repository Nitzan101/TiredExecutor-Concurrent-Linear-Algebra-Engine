# TiredExecutor - Concurrent Linear Algebra Engine

A high-performance, custom thread pool implementation designed to power a concurrent Linear Algebra Engine. This project focuses on sophisticated resource scheduling, thread lifecycle management, and the mitigation of common concurrency pitfalls in a multi-threaded Java environment.

## Project Architecture
The core of the system is the **TiredExecutor**, which replaces standard Java executor services with a "fatigue-aware" scheduling logic. It ensures that no single worker thread is overwhelmed by calculating a workload-based fatigue factor before dispatching tasks.

* **Custom Thread Pool:** Manages a fixed set of worker threads with advanced lifecycle controls.
* **Priority Scheduling:** Utilizes a `PriorityBlockingQueue` to order tasks based on their computational weight and the current state of worker fatigue.
* **Synchronization Strategy:** Implements robust thread safety using `ReentrantLock`, `Condition` variables, and atomic primitives to prevent race conditions.
* **Task Handling:** Supports asynchronous task submission with a **Callback Pattern** for result retrieval.

## Key Features & Logic
* **Fatigue Factor:** A proprietary scheduling algorithm that balances tasks by tracking the cumulative workload of each thread.
* **Task Poisoning:** Implements a clean shutdown mechanism using "Poison Pill" tasks to ensure all threads terminate gracefully after completing their current work.
* **Linear Algebra Integration:** Optimized to handle concurrent matrix operations (multiplication, addition, and transformations) by breaking them into parallelizable sub-tasks.
* **Maven Lifecycle:** Managed via `pom.xml` for dependency resolution and automated builds.

## Skills & Concepts Implemented
* **Advanced Multithreading:** Manual management of thread states (Wait, Run, Terminate) and synchronization.
* **System-Level Concurrency:** Deep dive into the Java Memory Model and the prevention of deadlocks.
* **Algorithm Optimization:** Implementing efficient scheduling in $O(\log n)$ using priority-based structures.
* **Resource Management:** Ensuring minimal memory overhead and efficient CPU utilization under heavy computational loads.

---

## Project Structure
```text
.
├── src/
│   ├── main/
│   │   └── java/
│   │       ├── executor/    # Custom TiredExecutor implementation
│   │       ├── math/        # Linear Algebra Engine logic
│   │       └── tasks/       # Concurrent task definitions
├── input_files/             # Sample matrix and operation data
├── example.json             # Configuration for task scheduling
├── pom.xml                  # Maven project configuration
└── README.md