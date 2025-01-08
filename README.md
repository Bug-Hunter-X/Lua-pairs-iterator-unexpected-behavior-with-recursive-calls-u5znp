# Lua pairs iterator unexpected behavior with recursive calls

This repository demonstrates a potential issue with Lua's `pairs` iterator when used within a recursive function and tables are modified during iteration.  The core problem lies in how `pairs` interacts with table modifications while iterating.

## The Bug
The provided `bug.lua` file contains a function `foo` that recursively iterates through a nested table using `pairs`. If the table structure changes during the iteration (e.g., an element is added), `pairs` may skip elements or produce unexpected results.

## The Solution
The `bugSolution.lua` file offers a solution using a different approach to handle nested table iteration safely.

## How to reproduce the bug
1. Clone this repository.
2. Run `bug.lua` using a Lua interpreter. (e.g., `lua bug.lua`)
3. Observe the output; it likely won't visit all elements if the table is modified during the function's execution. (This would only occur if you modify the nested tables during the execution of foo.)

## How to use the solution
1.  Run `bugSolution.lua` using a Lua interpreter.
2. Observe the output; the solution correctly iterates through all elements, even when a table element is added to the nested tables during runtime. 

This example highlights the importance of careful table manipulation when using iterators in Lua, especially within recursive functions.