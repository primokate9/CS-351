# Project 1 - Hash Function Performance

## Performance Results (no optimization)

| Program | Optimization | Real Time | User Time | Sys Time | Memory (KB) | Speedup over hash-00 |
|---------|--------------|-----------|-----------|----------|-------------|------------------------|
| hash-00 | -g           | 355.59 s  | 342.46 s  | 10.63 s  | 2884        | 1.00×                 |
| hash-01 | -g           | 22.88 s   | 16.71 s   | 2.99 s   | 2880        | 15.54×                |
| hash-02 | -g           | 15.47 s   | 14.06 s   | 1.06 s   | 2880        | 22.98×                |
| hash-03 | -g           | 16.35 s   | 15.13 s   | 1.10 s   | 3456        | 21.75×                |
| hash-04 | -g           | 14.46 s   | 13.85 s   | 0.41 s   | 501120      | 24.59×                |

## Notes
- These tests were compiled with `-g` and no optimization.
- hash-04 uses memory mapping, which explains its high memory usage.

## Performance Results (with -O2 optimization)

| Program | Optimization | Real Time | User Time | Sys Time | Memory (KB) | Speedup over hash-00 |
|---------|--------------|-----------|-----------|----------|-------------|------------------------|
| hash-00 | -O2          | 342.17 s  | 329.48 s  | 9.73 s   | 2880        | 1.00×                 |
| hash-01 | -O2          | 9.54 s    | 6.89 s    | 1.39 s   | 2880        | 35.86×                |
| hash-02 | -O2          | 6.83 s    | 6.85 s    | 1.26 s   | 2884        | 50.07×                |
| hash-03 | -O2          | 8.23 s    | 6.82 s    | 1.23 s   | 2880        | 41.57×                |
| hash-04 | -O2          | 6.95 s    | 6.39 s    | 0.45 s   | 5007168     | 49.22×                |

## Analysis Questions

**1. What operation do you think accounts for most of hash-00's runtime?**  
The repeated parsing and reading of values from `Data.txt` adds significant overhead, especially since it’s done 1,000,000 times using standard input operations. File I/O and text-to-number conversion dominate the runtime.

**2. hash-01 and hash-02 both dynamically allocate memory. Is there much difference time-wise?**  
Yes. `hash-02` is faster than `hash-01` because it uses `alloca()` to allocate memory on the stack, which is faster than heap allocation used in `hash-01`.

**3. hash-03 avoids the allocation by using a fixed-size array. Is there an appreciable speed difference?**  
Yes, it's slightly slower than `hash-02` but faster than `hash-01`. Fixed arrays reduce overhead compared to dynamic allocation, but `alloca()` still outperforms due to lower overhead and reuse.

**4. Why is hash-04's memory usage so much larger than the others?**  
Because it memory-maps the entire binary file into the program's address space. This avoids manual reads but results in the entire file being loaded and mapped, increasing memory consumption significantly.

**5. What other compiler options did you try, and did they help at all?**  
I used `-O2`, which significantly improved performance. Additional flags like `-funroll-loops` or `-march=native` could be tested for further tuning.

