# Resource Exhaustion and Abuse Test Snippets

It involve pushing the system to its limits in terms of CPU, memory, recursion, I/O, and other system resources, helping to identify weaknesses or points where the system might crash or degrade in performance.

## 1. Infinite Loops
Users could write code with infinite loops that consume CPU resources indefinitely.

```python
while True:
    pass  # Infinite loop that consumes 100% CPU
```

Or:

```python
i = 0
while i < 1:
    i -= 1  # Infinite loop that runs forever
```

## 2. Infinite Recursion
Recursion with no base case or too deep recursion can cause a `RecursionError` and consume memory.

```python
def recursive():
    return recursive()

recursive()  # Infinite recursion
```

Or:

```python
def deep_recursion(n):
    return deep_recursion(n + 1)

deep_recursion(1)  # Recursion that crashes the program with memory exhaustion
```

## 3. High Memory Consumption (Excessive List Creation)
Creating large data structures that require excessive memory can crash the server.

```python
data = []
while True:
    data.append('A' * 10**6)  # Keep appending 1 million characters, consuming memory rapidly
```

Or:

```python
large_list = [0] * 10**9  # Create an extremely large list that eats memory
```

## 4. Fork Bomb
In environments that allow subprocesses, a user could create multiple processes, overwhelming the server with processes.

```python
import os

while True:
    os.fork()  # Creates infinite child processes
```

This example may not work in restricted environments but is dangerous in unrestricted servers.

## 5. Disk I/O Flooding
A user could write excessive data to disk, filling up the server's storage.

```python
with open('file.txt', 'w') as f:
    while True:
        f.write('A' * 10**6)  # Write 1 million characters in an infinite loop
```

## 6. Heavy Computation (CPU Exhaustion)
Users can write code that consumes CPU by executing complex algorithms unnecessarily.

```python
def heavy_computation(n):
    if n == 1:
        return n
    return n * heavy_computation(n - 1)

heavy_computation(10**6)  # Recursive function with huge numbers causing CPU exhaustion
```

## 7. Memory Leaks
Deliberately consuming memory by creating objects that aren't cleared can lead to memory exhaustion.

```python
class MemoryLeak:
    def __init__(self):
        self.data = [1] * (10**6)  # 1 million integers
        
    def create_leak(self):
        while True:
            self.data.append(self.data)  # Keep appending to itself, leading to memory leak

leak = MemoryLeak()
leak.create_leak()
```

## 8. Unnecessary Nested Loops
Poorly designed nested loops that grow exponentially in iterations can slow the system down.

```python
for i in range(10**6):
    for j in range(10**6):
        pass  # Massive nested loop causing CPU load and delay
```

## 9. DOS via Networking
Opening too many connections can cause a Denial of Service (DoS) attack in environments with networking support.

```python
import socket

sockets = []
while True:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.connect(('localhost', 8080))  # Connect to server infinitely
    sockets.append(s)
```

## 10. Resource Starvation through File Descriptors
Opening too many file descriptors without closing them can exhaust available resources.

```python
files = []
while True:
    f = open('file.txt', 'w')  # Open files infinitely without closing them
    files.append(f)
```

---
## Conclusion

Testing with this type of "worst-case" code is essential for building a robust and secure web-based Python compiler.