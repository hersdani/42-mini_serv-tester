# mini_serv_tester

A robust, fully-automated Python test suite for the **Rank 06 Exam** project `mini_serv` (42 School Cursus).

It uses Python's `socket`, `subprocess`, and `select` libraries to simulate multiple concurrent clients, validating your server against all standard project constraints.

## Features

- **Basic Connections & Messages:** Tests client arrivals, messages spanning multiple lines, partial messages (missing newline), and client departures.
- **Stress & Load Testing:** Spawns 250 dummy clients to test server file descriptors and stability under load.
- **Large Payloads:** Transmits continuous message structures larger than typical buffer sizes (8KB+) to ensure chunks are assembled and fragmented efficiently without data corruption.
- **Broadcasting Speed Test:** Benchmarks latency by sending a single broadcast and monitoring propagation to 200 clients under strict timeouts (simulating the exam requirement: "Warning our tester is expecting that you send the messages as fast as you can").

## Requirements

- Python 3.x
- Standard Python libraries (no `pip install` required)
- Your compiled `mini_serv` executable located in the same directory running the script.

## Usage

1. Compile your server and ensure the executable `mini_serv` is present.
2. Run the tester:

```bash
python3 tester.py
```

The script will automatically detect a free port and launch `mini_serv`, connecting multiple simulated clients to run all checks and validations.

## Tests Overview

- **Test 1:** Basic connection & arrival notification
- **Test 2:** Basic message routing
- **Test 3:** Partial message buffering (simulating multiple `recv()` calls logic)
- **Test 4:** Multiple lines concatenated sequentially
- **Test 5:** Client leaving notification
- **Test 6:** Stress connections (250 clients without crashing)
- **Test 7:** Mass messaging & large texts routing to target group
- **Test 8:** Large payload processing (> 8KB)
- **Test 9:** Speed / Latency Broadcast Benchmark (ensuring fast message propagation to avoid "too slow" errors during exam grading)
