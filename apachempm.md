# Apache MPM (Multi-Processing Module)

## 💡 What is MPM?

MPM = Multi-Processing Module

👉 It defines how Apache HTTP Server handles incoming requests internally

Think of it as:

```bash
“How Apache creates processes/threads to serve users”
```

## 🧠 Why MPM Exists

When users send requests:

```bash
User1 → ?
User2 → ?
User3 → ?
```

Apache needs a strategy:

```bash
How many processes?
How many threads?
How to manage memory?
```

👉 That strategy = MPM

## 🔥 Types of MPM (Very Important)

Apache mainly has 3 types:

```bash
1. Prefork
2. Worker
3. Event
```

## 1️⃣ Prefork MPM

### 💡 Concept

```bash
1 request = 1 process
```

### Architecture

```bash
Master
 ├ Process1 → User1
 ├ Process2 → User2
 ├ Process3 → User3
```

### Characteristics

```bash
✔ No threads (only processes)
✔ Very stable
✔ Compatible with mod_php
```

### ❌ Problems

```bash
High memory usage
Not scalable
Slow under heavy load
```

### When Used?

```bash
Old systems
PHP with mod_php
Stability-critical apps
```

## 2️⃣ Worker MPM

### 💡 Concept

```bash
1 process → multiple threads
```

### Architecture

```bash
Master
 ├ Process1
 │    ├ Thread1 → User1
 │    ├ Thread2 → User2
 ├ Process2
 │    ├ Thread3 → User3
```

### Characteristics

```bash
✔ Uses threads → less memory
✔ Better performance than prefork
```

### ❌ Problems

```bash
Thread safety issues
Not ideal with mod_php
```

## 3️⃣ Event MPM (Modern Apache)

### 💡 Concept

```bash
Non-blocking + threads
```

### Architecture

```bash
Master
 ├ Worker Process
 │    ├ Threads
 │    ├ Event handling (keep-alive optimized)
```

### Key Feature

👉 Handles keep-alive connections efficiently

Example:

```bash
User keeps connection open → Event MPM handles without blocking thread
```

### Characteristics

```bash
✔ Best performance in Apache
✔ Handles many connections
✔ Closer to NGINX model
```

### ❌ Still not as efficient as NGINX

Because:

```bash
Still thread-based (not fully event-driven)
```

### 🔥 How to Check Your MPM

```bash
apachectl -V | grep MPM
```

## 🎯 Interview Questions

### Q1: What is MPM?

```
A module in Apache that defines how it handles requests using processes and threads.
```

### Q2: Which MPM is best?

```
👉 Event MPM
```

### Q3: Why Prefork is outdated?

```
High memory usage and poor scalability.
```

### Q4: Difference between Worker and Event?

```
Worker → thread-based
Event → thread + non-blocking optimization
```
