# memory-management

This project is a short example about how to analyze memory management in Rust, working with both stack and heap.

****
**Instalation**
``cargo install``

**Running**
``cargo run``

**Building**
``cargo build``
*target* folder as default output
****
For debugging purposes, gdb will be used to analyze the memory management process

**Start GDB with TUI**
``gbd -tui``

**Load Symbol Table from compiled file to set Debuggers with GDB**
``file target/debug/memory-management``

**List Functions and Code**
``list``
*with loaded symbols from file command*

**Place Breakpoint using gdb**
``b stack_only``

**Run file with gdb after placing Breakpoints**
``r``
*with loaded symbols from file command*
*the file should run and should stop in your first breakpoint*
![Code ran and stopped at first breakpoint](./debug-snapshots/debugger.png)

**Inspect Stack in a given moment**
``bt <number of stacked calls>``
![Inspecting Stack](./debug-snapshots/stack.png)

**Inspect Local Variables**
``info locals``

**Inspect Arguments in a given Function**
``info args``

**Proceed with gdb to next line**
``n``

****
Difference between a variable in stack and a variable allocated in heap
![Difference between a variable in stack and a variable allocated in heap](./debug-snapshots/heapxstack-variables.png)
*For the dynamic allocation, we're using Box, which is a smart pointer in Rust*
*e is actually showing his address on the heap*

Dereference to read a dynamically stored variable
``x  0x55555559ead0``
*output: 0x55555559ead0: 0x00000007*
*The read can automatically format the value as a digit for example, using: x /d 0x55555559ead0*

Continue to next breakpoint
``c``