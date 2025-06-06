# CS-351
# Project-1:
| Program        | Optimization Level      | Real Time (s) | User Time (s) | System Time (s) | Memory Usage (KB) | Throughput | Performance Improvement |
|----------------|-------------------------|---------------|---------------|-----------------|-------------------|------------|-------------------------|
| hash-00 (base) | -g                      | 357.25        | 341.46        | 10.06           | 2896              | 2799.16    | N/A                     |
| hash-01        | -g                      | 21.86         | 16.64         | 2.65            | 2896              | 45745.65   | 16.34                   |
| hash-02        | -g                      | 17.28         | 14.29         | 1.44            | 2900              | 57870.37   | 20.67                   |
| hash-03        | -g                      | 16.04         | 14.18         | 1.34            | 2900              | 62344.13   | 22.27                   |
| hash-04        | -g                      | 12.78         | 12.18         | 0.44            | 5011776           | 78247.26   | 27.95                   |
| hash-00 (base) | -O2                     | 347.00        | 330.18        | 5.14            | 2308              | 2881.84    | N/A                     |
| hash-01        | -O2                     | 14.82         | 7.15          | 2.40            | 2896              | 67476.38   | 23.41                   |
| hash-02        | -O2                     | 8.28          | 6.85          | 1.26            | 2880              | 120772.94  | 41.9                    |
| hash-03        | -O2                     | 8.24          | 6.82          | 1.25            | 2896              | 121359.22  | 42.11                   |
| hash-04        | -O2                     | 7.17          | 6.64          | 0.45            | 5012352           | 139470.01  | 48.39                   |
| hash-00 (base) | -O3 -march=native -flto | 345.27        | 332.26        | 10.42           | 2880              | 2896.28    | N/A                     |
| hash-01        | -O3 -march=native -flto | 10.39         | 7.07          | 2.00            | 2896              | 96246.39   | 33.23                   |
| hash-02        | -O3 -march=native -flto | 8.57          | 6.94          | 1.27            | 2896              | 116686.11  | 40.28                   |
| hash-03        | -O3 -march=native -flto | 8.14          | 6.78          | 1.27            | 3472              | 122850.12  | 42.41                   |
| hash-04        | -O3 -march=native -flto | 7.29          | 6.69          | 0.52            | 5012360           | 137174.21  | 47.36                   |

# Questions:
1. This operation accounts for most of hash-00's runtime: input >> numHashes;. This operation reads in values and formats them one at a time, which is part of the reason why this program takes so long.
2. There is a difference in the time hash-01 and hash-02 take to allocate memory because hash-01 uses new[] and delete[], while hash 2 uses alloca(). hash-02 is faster because alloca() is generally faster than using new[] and delete[], although it does have a risk of stack overflow.
3. There is an appreciable speed difference from hash-03 using a fixed array because it does not need to allocate or deallocate when hashing. This method is good for when you know the size of your input and are sure you do not need to make the array bigger.
4. The memory usage of hash-04 is so much larger than the others because it uses mmap, which takes the entire input file and puts it into memory, while the other functions only store small amounts of the file in memory at a time.
5. I tried these compiler options: -O3 -march=native -flto. They made all the programs run faster than with no optimizations. Only hash-01 performed significantly better than when it was run using -O2, with the rest of the hashes performing about on par with -O2 optimization.
