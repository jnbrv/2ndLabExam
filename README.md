# CPU Scheduling & Banker's Algorithm

Two console programs written in Python 3 that simulate core operating-system concepts.

| File | What it does |
|------|--------------|
| `cpu_scheduling.py` | Simulates **FCFS** (non-preemptive) and **Round Robin** (preemptive) |
| `bankers_algorithm.py` | Checks if a system is in a **safe state** and prints the safe sequence (no input needed) |

## Requirements

- Python 3.7 or newer (no extra libraries needed)

## How to Run

Open a terminal in the project folder, then run either program:

```bash
python cpu_scheduling.py
python bankers_algorithm.py
```

(On some systems use `python3` instead of `python`.)

---

## 1. CPU Scheduling (`cpu_scheduling.py`)

### Input (typed in the console)
1. Number of processes
2. Arrival time and burst time of each process
3. Time quantum (used by Round Robin)

Both algorithms run on the same input so you can compare the results.

### Output (for each algorithm)
- Gantt chart (with `Idle` blocks when the CPU waits for a process to arrive)
- Table with completion, turnaround and waiting time per process
- Average Waiting Time
- Average Turnaround Time

### Formulas
- Turnaround Time = Completion Time − Arrival Time
- Waiting Time = Turnaround Time − Burst Time

### Sample run
```
Enter number of processes: 3
Process P0
  Arrival time : 0
  Burst time   : 5
Process P1
  Arrival time : 1
  Burst time   : 3
Process P2
  Arrival time : 2
  Burst time   : 8
Enter time quantum (for Round Robin): 2
```

---

## 2. Banker's Algorithm (`bankers_algorithm.py`)

This program needs **no typing**. The system data (Allocation, Maximum and
Available) is written at the top of the file, so just run it and it prints
the result.

### Output
- Need matrix (`Need = Max − Allocation`)
- Whether the system is in a **Safe** or **Unsafe** state
- The safe sequence of processes (if one exists)

### Sample output
```
Need Matrix:
P0: [7, 4, 3]
P1: [1, 2, 2]
P2: [6, 0, 0]
P3: [0, 1, 1]
P4: [4, 3, 1]

System is in a Safe State.
Safe Sequence: P1 → P3 → P4 → P0 → P2
```

### Testing a different system
Open `bankers_algorithm.py` and edit the `allocation`, `maximum` and
`available` values in the **SYSTEM DATA** section, then run it again.

---

## Notes
- Every important step in the code is explained with comments.
- The CPU scheduling program validates its input: non-numbers and invalid
  values are rejected and it asks again.
- Banker's Algorithm reports an error if any Allocation value is greater
  than its Maximum (that would make Need negative).
