## Performance Results

### iota.cpu Results

|Vector<br>Length|Wall Clock<br>Time|User Time|System Time|
|:--:|--:|--:|--:|
|10| 0.00| 0.00| 0.00|
|100| 0.00| 0.00| 0.00|
|1000| 0.00| 0.00| 0.00|
|10000| 0.00| 0.00| 0.00|
|100000| 0.00| 0.00| 0.00|
|1000000| 0.00| 0.00| 0.00|
|5000000| 0.03| 0.00| 0.02|
|100000000| 0.55| 0.09| 0.45|
|500000000| 2.78| 0.43| 2.34|
|1000000000| 5.63| 0.87| 4.76|
|5000000000|35.38| 6.25|29.13|

### iota.gpu Results

|Vector<br>Length|Wall Clock<br>Time|User Time|System Time|
|:--:|--:|--:|--:|
|10| 0.29| 0.01| 0.27|
|100| 0.20| 0.01| 0.19|
|1000| 0.20| 0.00| 0.19|
|10000| 0.20| 0.00| 0.19|
|100000| 0.20| 0.01| 0.19|
|1000000| 0.20| 0.00| 0.19|
|5000000| 0.24| 0.02| 0.22|
|100000000| 0.80| 0.16| 0.63|
|500000000| 3.28| 0.78| 2.49|
|1000000000| 6.33| 1.54| 4.78|
|5000000000|39.16| 8.69|30.47|

### Analysis: Is CUDA a good solution for `iota`?

Although CUDA can provide speedups for extremely large vector lengths, it is **not a great solution for the `iota` function** overall. This is because:

- The function is too simple to benefit from parallelism at small sizes.
- GPU overhead (like memory allocation, kernel launch, and memory copies) adds significant cost.
- For small and mid-size vectors (e.g., ≤ 5M), the CPU version is actually faster.

CUDA shines for **compute-heavy** operations, but `iota` is a **memory-bound, lightweight operation**, so the gains are minimal except at very large scales.

![Julia Set](julia.png)

