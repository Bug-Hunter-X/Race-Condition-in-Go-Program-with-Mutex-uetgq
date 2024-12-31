# Race Condition in Go Program with Mutex

This repository demonstrates a subtle race condition in a Go program that uses goroutines and mutexes. The program attempts to increment a counter using multiple goroutines, but the race condition leads to incorrect results.

## Bug Description
The race condition occurs because the `count` variable is accessed and modified by multiple goroutines concurrently, even though a mutex is used. The mutex locks and unlocks around the `count += i` line, preventing concurrent access within that line but not during the access to `i` inside the anonymous function.  The value of `i` is copied after the loop iteration, leading to multiple goroutines potentially using the same value of `i`. 

## Solution
The solution involves ensuring that the `i` value is unique for each goroutine, preventing the race condition.