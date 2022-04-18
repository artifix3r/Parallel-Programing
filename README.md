# differential-evolution

The following is an example of the output of the algorithm in the console:
```
Please wait --> running DE on CPU
-------------------------------------------------------------------------------------------------------------------------------------------------
configuration: 
populationSize:     4000
maxIterations:      2000
cpu_time:           8673ms
-------------------------------------------------------------------------------------------------------------------------------------------------
    Kernel time |      Total Time |         speedup |        Min cost |                            Best Solution
-------------------------------------------------------------------------------------------------------------------------------------------------
          34 ms |          125 ms |             69x |               0 |    1.67227e-10  -2.59418e-09  -8.13821e-10   1.86889e-09   1.85749e-09
          34 ms |           34 ms |            255x |               0 |   -1.41159e-09  -2.80443e-09   1.68324e-09    -2.186e-09   4.87597e-10
          34 ms |           34 ms |            255x |               0 |    1.26243e-09   4.00216e-09    5.8711e-11  -1.31085e-09  -6.61054e-10
          35 ms |           35 ms |            247x |               0 |   -9.16173e-10   4.36703e-10  -1.15314e-09  -2.47681e-09   4.94631e-09
          34 ms |           34 ms |            255x |               0 |   -2.62808e-10   2.12818e-09   2.34033e-09  -8.40883e-10   1.60565e-09
-------------------------------------------------------------------------------------------------------------------------------------------------
```

The speedup is about 250x over the CPU, as you can see. You can adjust the speedup by changing the
`blocksize` of the cuda kernel. For instance, when I set `int kernelBlockSize = 32;` 
in the `main.cu`, the following results can be seen

```
Please wait --> running DE on CPU
-------------------------------------------------------------------------------------------------------------------------------------------------
configuration: 
populationSize:     4000
maxIterations:      2000
cpu_time:           8696ms
-------------------------------------------------------------------------------------------------------------------------------------------------
    Kernel time |      Total Time |         speedup |        Min cost |                            Best Solution
-------------------------------------------------------------------------------------------------------------------------------------------------
          35 ms |          135 ms |             64x |               0 |   -1.77847e-09   1.17443e-09   3.53284e-09  -1.91858e-09  -2.82963e-09
          35 ms |           35 ms |            248x |               0 |    1.79237e-09    1.5166e-09   1.00202e-09   1.55494e-09   6.01972e-10
          36 ms |           36 ms |            241x |               0 |   -9.61407e-10  -3.48689e-09   3.76303e-09   -1.4582e-09   -3.7136e-09
          32 ms |           32 ms |            271x |               0 |    3.42854e-10  -3.55092e-09  -4.64339e-10  -5.58002e-10   1.90873e-09
          32 ms |           32 ms |            271x |               0 |    2.49433e-09   -9.3311e-10   2.91025e-09   2.91585e-09   3.34526e-09
-------------------------------------------------------------------------------------------------------------------------------------------------
```

# Supported crossovers

There are two major crossovers supported by the code:

- binomial crossover
- exponential crossover

If you want to include the exponential crossover code, compile it with the `EXPONENTIAL_CROSSOVER` defined
 or you could simply
uncomment the `add_compile_definitions(EXPONENTIAL_CROSSOVER)` in the `CMakeLists.txt` file. Note that the exponential variant is slightly slower than the binomial