# Resource Exhaustion and Abuse Test Snippets

It involve pushing the system to its limits in terms of CPU, memory, recursion, I/O, and other system resources, helping to identify weaknesses or points where the system might crash or degrade in performance.

---

## 1. Infinite Loops  
Infinite loops that consume CPU resources indefinitely:

```java
class InfiniteLoop {
    public static void main(String[] args) {
        while (true) {
            // Infinite loop consuming 100% CPU
        }
    }
}
```

Or:

```java
class InfiniteLoop {
    public static void main(String[] args) {
        int i = 0;
        while (i < 1) {
            i--;  // Infinite loop that runs forever
        }
    }
}
```

## 2. Infinite Recursion  
Recursion with no base case, or deep recursion that can crash the program:

```java
class InfiniteRecursion {
    public static void main(String[] args) {
        recursive();
    }

    public static void recursive() {
        recursive();  // Infinite recursion
    }
}
```

Or:

```java
class DeepRecursion {
    public static void main(String[] args) {
        deepRecursion(1);
    }

    public static void deepRecursion(int n) {
        deepRecursion(n + 1);  // Recursion that crashes the program
    }
}
```

## 3. High Memory Consumption (Excessive Array Creation)  
Creating large arrays that consume excessive memory:

```java
class MemoryConsumption {
    public static void main(String[] args) {
        while (true) {
            String[] data = new String[1000000];  // Allocate large arrays repeatedly
        }
    }
}
```

Or:

```java
class LargeArray {
    public static void main(String[] args) {
        int[] largeArray = new int[Integer.MAX_VALUE];  // Try creating an extremely large array
    }
}
```

## 4. Fork Bomb (Creating Subprocesses)  
Spawning an infinite number of processes using `Runtime.getRuntime().exec()`:

```java
class ForkBomb {
    public static void main(String[] args) {
        while (true) {
            try {
                Runtime.getRuntime().exec("/");  // Fork bomb using recursive subprocess
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
}
```

> This code may not work in some environments due to restrictions on creating processes.

## 5. Disk I/O Flooding  
Writing excessive data to disk, causing storage to fill up:

```java
import java.io.*;

class DiskFlood {
    public static void main(String[] args) {
        try {
            BufferedWriter writer = new BufferedWriter(new FileWriter("file.txt"));
            while (true) {
                writer.write("A".repeat(1000000));  // Write 1 million characters infinitely
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## 6. Heavy Computation (CPU Exhaustion)  
Running complex, recursive algorithms that exhaust the CPU:

```java
class HeavyComputation {
    public static void main(String[] args) {
        System.out.println(heavyComputation(1000000));  // CPU-intensive computation
    }

    public static int heavyComputation(int n) {
        if (n == 1) {
            return n;
        }
        return n * heavyComputation(n - 1);  // Recursive computation
    }
}
```

## 7. Memory Leaks  
Deliberately consuming memory by creating objects that are not cleared:

```java
import java.util.ArrayList;

class MemoryLeak {
    public static void main(String[] args) {
        ArrayList<int[]> leakList = new ArrayList<>();
        while (true) {
            leakList.add(new int[1000000]);  // Keep adding large arrays to the list
        }
    }
}
```

## 8. Unnecessary Nested Loops  
Poorly designed nested loops causing performance degradation:

```java
class NestedLoops {
    public static void main(String[] args) {
        for (int i = 0; i < 1000000; i++) {
            for (int j = 0; j < 1000000; j++) {
                // Massive nested loop causing CPU load and delay
                System.out.println("Nested loop i:"+i+" j:"+j);
            }
        }
    }
}
```

## 9. Denial of Service via Networking (DOS)  
Opening too many socket connections can lead to a denial of service:

```java
import java.net.*;
import java.util.*;
import java.io.*;

class DosNetworking {
    public static void main(String[] args) {
        List<Socket> sockets = new ArrayList<>();
        while (true) {
            try {
                Socket s = new Socket("localhost", 8080);  // Connect to the server infinitely
                sockets.add(s);
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

## 10. Resource Starvation through File Descriptors  
Opening file descriptors without closing them can exhaust system resources:

```java
import java.io.*;
import java.util.*;

class FileDescriptorFlood {
    public static void main(String[] args) {
        List<FileWriter> files = new ArrayList<>();
        while (true) {
            try {
                files.add(new FileWriter("file.txt"));  // Open file repeatedly without closing
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

---

## Conclusion
These Java snippets are designed to test the limits of system resources, potentially causing crashes or severe performance degradation. Always run them in controlled environments to avoid unintentional harm to systems.
