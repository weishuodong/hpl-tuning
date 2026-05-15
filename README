# HPL Benchmarking Report

## Limitations

This benchmarking project was **not run on the SoC Compute Cluster** due to lack of cluster access at the time of experimentation. All experiments were instead conducted locally on a laptop equipped with an Intel Core Ultra 9 285H processor with 16 CPU cores.


*Results obtained are therefore representative only of a single-node CPU-only setup.*


$\color{orange}{\text{DO NOT ATTEMPT TO DEPLOY THE PROJECT.
IT HAS NOT BEEN TESTED OUTSIDE LOCAL ENV}}$

## Background Knowledge

I possess foundational experience in the following areas:

- Linux OS + Windows dual boot laptop
- C  
- Linux Command Line

My primary development environment is Linux-based, specifically:

> I use Arch btw (No pun intended, seriously)

However, prior to this project, I had no practical experience with:
- HPL benchmarking
- MPI programming
- HPC cluster workflows
- distributed linear algebra
- process topology tuning

---

## Task Requirements

Objective:
> Maximize HPL FLOPS performance

subject to the constraints defined in the problem statement.

HPL (High Performance Linpack) benchmarks floating-point computational throughput by solving large dense systems of linear equations using distributed LU decomposition.

The FLOPS score is mainly influenced by:
- matrix size (`N`)
- block size (`NB`)
- MPI process topology (`P × Q`)
- Many more factors that are not tested ... ...

---

## Approach Taken

### Initial Understanding

I spent 1 week to understand the following ... ...
- MPI fundamentals
- distributed process execution
- HPL build systems
- the meaning of HPL configuration variables

... and deployed the following commands on my local CPU ...:
- `MPI_Send`
- `MPI_Recv`
- `MPI_Bcast`
- `MPI_Reduce`

... only to realize that HPL does not require coding in C (I am retarded).


### FLOPS Analysis

By studying the HPL benchmark formulation, I identified that computational workload approximately scales as:

```math
\frac{2}{3}N^3
```

while the reported FLOPS score is approximately proportional to:

```math
\frac{N^3}{\text{time}}
```

For a double in N, 
 - Score x8
 - Workload x4

Hence, for a better score, the clusters have to perform 4x the workload in less than twice the time as before, which is not probable as N increases significantly.

Therefore, increasing N blindly is not a good idea.


---

### Parameter Tuning

The main parameters explored during experimentation were:
- Matrix Size (`N`)
- Block Size (`NB`)
- Process Grid (`P × Q`) (Not altered significantly as 4x4 crashes my laptop)

Testing was conducted iteratively by modifying one parameter at a time while observing changes in resulting GFLOPS.


---

## Results

### FLOPS vs Matrix Size (N)

![GFLOPS vs N](./img/gflops_vs_n.png)




### FLOPS vs Block Size (NB)

![GFLOPS vs NB](./img/gflops_vs_nb.png)

Observations:
- Both functions are not increasing functions. There exists a theoretical max for each of the 6 functions, and possibly all functions that exist out there.
---

## Conclusions

Blindly increasing any variable is not smart in HPC.

---

## Future Plans and Testing
1) Get access to NUS SOC HPC Cluster and perform testing there.

## Appendix

### Raw Benchmark Images

![WR00L2L2_1024_N_2_2](./img/WR00L2L2_1024_N_2_2.png)

![WR00L2L2_1024_N_3_3](./img/WR00L2L2_1024_N_3_3.png)

![WR00L2L2_2048_N_3_3](./img/WR00L2L2_2048_N_3_3.png)

![WR00L2L2_4196_N_3_3](./img/WR00L2L2_4196_N_3_3.png)

![WR00L2L2_N_4_2_2](./img/WR00L2L2_N_4_2_2.png)

![WR00L2L2_N_6_2_2](./img/WR00L2L2_N_6_2_2.png)

![WR00L2L2_N_6_3_3](./img/WR00L2L2_N_6_3_3.png)
