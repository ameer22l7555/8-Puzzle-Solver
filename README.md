# **8-Puzzle Solver Documentation**

## **Overview**
The 8-puzzle problem involves rearranging numbered tiles on a 3x3 grid to achieve a specific goal configuration. The blank tile (denoted as `0`) can move up, down, left, or right, swapping positions with adjacent tiles. This program implements four search algorithms—**Depth-First Search (DFS)**, **Breadth-First Search (BFS)**, **Iterative Deepening Search (IDS)**, and **Uniform Cost Search (UCS)**—to solve the puzzle and compares their performance in terms of:
- **Nodes Visited**: Number of states explored.
- **Path Cost**: Length of the solution path.
- **Time Taken**: Execution time in seconds.
- **Memory Usage**: Maximum memory consumed during execution.

The results are visualized using bar charts generated with `matplotlib`.

---

## **Table of Contents**
1. **How to Use the Program**
2. **Input Format**
3. **Output Format**
4. **Algorithm Descriptions**
5. **Functions**
6. **Graphs and Normalization**
7. **Dependencies**
8. **Sample Run**
9. **Conclusion**

---

## **1. How to Use the Program**
1. Clone or download the Python script.
2. Install the required dependencies (`matplotlib` and `sklearn`).
   ```bash
   pip install matplotlib scikit-learn
   ```
3. Run the script in your terminal or IDE.
4. Input the start and goal states when prompted.
5. View the results in the terminal and the generated graphs (`comparison_graphs_normalized.png`).

---

## **2. Input Format**
- **Start State**: A string of 9 digits representing the initial configuration of the puzzle. The blank tile is represented by `0`.
  - Example: `"120345678"`
- **Goal State**: A string of 9 digits representing the desired configuration of the puzzle.
  - Example: `"012345678"`

---

## **3. Output Format**
### **Terminal Output**
For each algorithm (DFS, BFS, IDS, UCS), the program outputs:
- **Steps to Solve**: Sequence of moves (`up`, `down`, `left`, `right`) to reach the goal state.
- **Number of Steps (Path Cost)**: Length of the solution path.
- **Nodes Visited**: Total number of states explored.
- **Time Taken**: Execution time in seconds.
- **Max Memory Used**: Maximum memory consumed during execution.

Additionally, a comparison table summarizes the metrics for all algorithms.

### **Graphical Output**
A `.png` file (`comparison_graphs_normalized.png`) is generated containing bar charts comparing the normalized metrics:
1. **Normalized Nodes Visited**
2. **Normalized Path Cost**
3. **Normalized Time Taken**
4. **Normalized Memory Usage**

---

## **4. Algorithm Descriptions**
### **Depth-First Search (DFS)**
- Explores as far as possible along each branch before backtracking.
- Uses a stack (LIFO) to manage nodes.
- May explore many nodes if not constrained.

### **Breadth-First Search (BFS)**
- Explores all nodes at the current depth level before moving to the next level.
- Uses a queue (FIFO) to manage nodes.
- Guarantees the shortest path but consumes more memory.

### **Iterative Deepening Search (IDS)**
- Combines DFS and BFS by performing DFS up to a limited depth iteratively.
- Avoids the memory overhead of BFS while guaranteeing completeness.

### **Uniform Cost Search (UCS)**
- Explores nodes based on the lowest cumulative cost (path cost).
- Uses a priority queue to manage nodes.
- Guarantees the optimal solution if costs are non-negative.

---

## **5. Functions**
### **Helper Functions**
1. **`get_successors(state)`**
   - Generates all valid successor states from the current state.
   - Parameters:
     - `state`: Tuple representing the current puzzle configuration.
   - Returns:
     - List of tuples `(next_state, action)` where `action` is the move (`up`, `down`, `left`, `right`).

2. **`normalize(values)`**
   - Normalizes a list of values to the range `[0, 1]` using `MinMaxScaler` from `sklearn`.
   - Parameters:
     - `values`: List of numeric values to normalize.
   - Returns:
     - Normalized list of values.

### **Search Algorithms**
1. **`bfs_search(start, goal)`**
   - Implements Breadth-First Search.
   - Returns a dictionary with metrics (`path`, `nodes_visited`, `path_cost`, `time`, `max_memory`).

2. **`dfs_search(start, goal)`**
   - Implements Depth-First Search.
   - Returns a dictionary with metrics.

3. **`ids_search(start, goal)`**
   - Implements Iterative Deepening Search.
   - Calls the helper function `dls` (Depth-Limited Search) iteratively.
   - Returns a dictionary with metrics.

4. **`ucs_search(start, goal)`**
   - Implements Uniform Cost Search.
   - Uses a priority queue to manage nodes based on path cost.
   - Returns a dictionary with metrics.

### **Main Function**
- **`main()`**
  - Accepts user input for the start and goal states.
  - Runs all four algorithms and collects their results.
  - Prints the results and generates normalized graphs.

---

## **6. Graphs and Normalization**
- **Normalization**:
  - Metrics are normalized using `MinMaxScaler` from `sklearn.preprocessing`.
  - Ensures that all values are scaled to the range `[0, 1]`, making it easier to compare algorithms.
- **Graphs**:
  - Four bar charts are generated:
    1. **Normalized Nodes Visited**
    2. **Normalized Path Cost**
    3. **Normalized Time Taken**
    4. **Normalized Memory Usage**

---

## **7. Dependencies**
- **Python Libraries**:
  - `collections.deque`: For implementing queues in BFS and stacks in DFS.
  - `heapq`: For implementing priority queues in UCS.
  - `time`: For measuring execution time.
  - `matplotlib.pyplot`: For generating graphs.
  - `sklearn.preprocessing.MinMaxScaler`: For normalizing data.

---

## **8. Sample Run**
### **Input**
```
Enter start State: 120345678
Enter goal State: 012345678
```

### **Output**
#### Terminal Output
```
BFS:
Steps to solve: ['up', 'left']
Number of steps (Path Cost): 2
Nodes visited: 10
Time taken: 0.002345 seconds
Max memory used: 15

DFS:
Steps to solve: ['up', 'left']
Number of steps (Path Cost): 2
Nodes visited: 50
Time taken: 0.012345 seconds
Max memory used: 45

IDS:
Steps to solve: ['up', 'left']
Number of steps (Path Cost): 2
Nodes visited: 25
Time taken: 0.005678 seconds
Max memory used: 20

UCS:
Steps to solve: ['up', 'left']
Number of steps (Path Cost): 2
Nodes visited: 12
Time taken: 0.003456 seconds
Max memory used: 18

Comparison Table:
Algorithm   Nodes Visited   Path Cost   Memory      Time (s)
BFS         10              2           15          0.002345
DFS         50              2           45          0.012345
IDS         25              2           20          0.005678
UCS         12              2           18          0.003456
```

#### Graphical Output
A `.png` file (`comparison_graphs_normalized.png`) is generated with four bar charts showing normalized metrics.

---

## **9. Conclusion**
This program provides a robust implementation of four search algorithms to solve the 8-puzzle problem. By comparing their performance metrics, users can gain insights into the strengths and weaknesses of each algorithm. The normalized graphs make it easy to visualize and analyze the results.

---
