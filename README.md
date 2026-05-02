# Sudoku Solver 🧩
 
A backtracking algorithm-based Sudoku solver implemented in Java, built as part of Data Structures & Algorithms coursework.
 
---
 
## 📌 Overview
 
This project demonstrates constraint satisfaction and recursive backtracking — two fundamental techniques used throughout computer science and, notably, in areas like SAT solvers and network analysis tools used in cybersecurity.
 
The solver reads a 9×9 board from a file, validates placements against row, column, and 3×3 block constraints, and recursively finds the solution or correctly determines that no solution exists.
 
---
 
## ⚙️ How It Works
 
The solver uses a classic **backtracking algorithm**:
 
1. Scan the board left-to-right, top-to-bottom for the first empty cell (`0`)
2. Try placing values `1–9` in the cell
3. Check three constraints before placing:
   - ✅ Value not already in the **row**
   - ✅ Value not already in the **column**
   - ✅ Value not already in the **3×3 block**
4. If valid → place it and recurse to the next cell
5. If no value works → **backtrack**, reset to `0`, try the next value in the previous cell
6. If all 81 cells are filled → puzzle solved ✅
---
 
## 🧱 Project Structure
 
```
SudokuSolver/
├── SudokuBoard.java        # Core solver logic + board loading + display
├── SudokuBoardTest.java    # JUnit 5 test suite (4 test cases)
├── board1.txt              # Sample solvable board
├── board2.txt              # Second solvable board
├── emptyboard.txt          # Empty board (many valid solutions)
├── badboard.txt            # Unsolvable board
└── README.md
```
 
---
 
## 🚀 How to Run
 
```bash
# Compile
javac -d out src/com/datastructures/SudokuBoard.java
 
# Run
java -cp out com.datastructures.SudokuBoard
```
 
**Board input format** (`board1.txt`):
```
0 0 3 0 2 0 6 0 0
9 0 0 3 0 5 0 0 1
0 0 1 8 0 6 4 0 0
...
```
Use `0` for empty cells, space-separated, 9 rows of 9 values.
 
---
 
## 🧪 Test Cases
 
| Test | Board | Expected |
|------|-------|----------|
| `testSolveEmptyBoard` | All zeros | `true` (solved) |
| `testSolveBoard1` | Standard puzzle | `true` (solved) |
| `testSolveBoard2` | Second puzzle | `true` (solved) |
| `testbadBoard` | Invalid puzzle | `false` (no solution) |
 
Run tests with JUnit 5:
```bash
javac -cp .:junit-platform-console-standalone.jar SudokuBoardTest.java
java -jar junit-platform-console-standalone.jar --select-class=com.datastructures.SudokuBoardTest
```
 
---
 
## 📊 Sample Output
 
```
-------------------------
| 0 0 3 | 0 2 0 | 6 0 0 |
| 9 0 0 | 3 0 5 | 0 0 1 |
| 0 0 1 | 8 0 6 | 4 0 0 |
-------------------------
...
 
Solution found:
-------------------------
| 4 8 3 | 9 2 1 | 6 5 7 |
| 9 6 7 | 3 4 5 | 8 2 1 |
| 2 5 1 | 8 7 6 | 4 9 3 |
-------------------------
...
```
 
---
 
## 💡 Why Backtracking Matters in Security
 
Constraint satisfaction and search algorithms aren't just puzzles — they're foundational to:
 
- **Password cracking tools** that systematically try credential combinations
- **SAT solvers** used in formal verification of security protocols
- **Network path analysis** that enumerates possible routes through a topology
Understanding these algorithms at the implementation level builds intuition for how exhaustive search attacks work — and why constraints and rate limiting help defend against them.
 
---
