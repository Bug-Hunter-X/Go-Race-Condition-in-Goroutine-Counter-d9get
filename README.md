# Go Race Condition in Goroutine Counter

This repository demonstrates a common race condition in Go when using goroutines to increment a shared counter without proper synchronization.  The `bug.go` file contains code that exhibits this race condition, resulting in an unpredictable final count.  The `bugSolution.go` file provides a corrected version using a mutex to synchronize access to the shared counter.

## How to Reproduce

1. Clone this repository.
2. Run `go run bug.go`  You'll notice that the final count is usually less than 1000.
3. Run `go run bugSolution.go`. The count will consistently be 1000.

## Explanation

The race condition occurs because multiple goroutines concurrently access and modify the `count` variable.  Without proper synchronization, the increments can be lost or overwritten, leading to an incorrect final count.  The solution uses a `sync.Mutex` to protect the `count` variable, ensuring that only one goroutine can access and modify it at a time.