# Gas Station Problem

## Overview
This C program solves the **Gas Station Problem**, where you have a circular route with gas stations. Each station provides a certain amount of gas, and it requires a specific cost to travel to the next station. The program determines if there exists a starting station from which you can complete the circuit.

## Problem Statement
Given two arrays:
- `gas[i]`: The amount of gas available at station `i`.
- `cost[i]`: The amount of gas required to travel from station `i` to the next station `(i + 1) % n`.

The program finds the **starting gas station index** from which you can complete the entire circuit, or returns `-1` if it's not possible.

## Algorithm
The solution follows these steps:
1. **Calculate the total gas and cost**: If the total gas available is less than the total cost, the journey is impossible.
2. **Find a valid starting index**: 
   - Keep track of the remaining fuel (`tank`) as you iterate.
   - If at any point `tank` becomes negative, reset it and set the next station as the new potential start.

## Code Explanation
```c
int complete(const int *gas, const int *cost, int n) {
    int total_gas = 0, total_cost = 0, tank = 0, index = 0;

    for (int i = 0; i < n; i++) {
        total_gas += gas[i];
        total_cost += cost[i];
        tank += gas[i] - cost[i];

        if (tank < 0) {
            index = i + 1;
            tank = 0;
        }
    }
    return (total_gas >= total_cost) ? index : -1;
}
```

### **Main Function**
- Reads `n`, the number of gas stations.
- Takes input for `gas` and `cost` arrays.
- Calls the `complete()` function to determine the starting index.
- Prints the result.

## Compilation & Execution
To compile and run the program:
```sh
gcc gas_station.c -o gas_station
./gas_station
```

## Example Usage
### **Input**
```
5
1 2 3 4 5
3 4 5 1 2
```
### **Output**
```
3
```
This means starting at station index `3` (0-based), you can complete the full circuit.

## License
This project is open-source and free to use under the MIT License.

## Author
Developed by Samanyu Pattanayak
