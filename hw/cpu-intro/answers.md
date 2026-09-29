# CPU Intro Answers

## 1) Predict for `-l 5:100,5:100`

Two processes run sequentially because both are CPU-only jobs and the scheduler switches only when a process finishes.

- Process 0 runs for 5 CPU bursts
- Process 1 runs for 5 CPU bursts after Process 0 is done

Predicted trace:

```text
Process 0
  cpu
  cpu
  cpu
  cpu
  cpu

Process 1
  cpu
  cpu
  cpu
  cpu
  cpu
```

## 2) Checked result with `-c`

Verified behavior from the simulator:

```text
Time        PID: 0        PID: 1           CPU           IOs
  1        RUN:cpu         READY             1
  2        RUN:cpu         READY             1
  3        RUN:cpu         READY             1
  4        RUN:cpu         READY             1
  5        RUN:cpu         READY             1
  6           DONE       RUN:cpu             1
  7           DONE       RUN:cpu             1
  8           DONE       RUN:cpu             1
  9           DONE       RUN:cpu             1
 10           DONE       RUN:cpu             1
```

## Conclusion

For this workload, the scheduler runs Process 0 to completion first, and then runs Process 1 to completion. No I/O occurs, so there is no blocking state in this example.
