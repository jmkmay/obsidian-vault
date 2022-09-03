# Stack and heap

The stack and heap are two different ways a computer program manages memory required for the execution of the program.

When a program runs, it requires a place to store information required for its execution. This is done in system memory (and includes the set of instructions that make up the program itself).

The stack can be thought of as a LIFO queue where data is "pushed" to and "popped" off the stack as a program traces through its set of instructions (sometimes called the [[stack frame]]).

The heap is more like a dictionary of information that can be accessed by address. In the heap, a program needs to request space from the memory allocator (a program itself) in order to store information.

The stack is incredibly fast and efficient, because all of its data can be known at compile time, and it is very reliable in terms of knowning what can be stored.

The heap is used for storing more complex data which may not be known at compile time. It is typically slower to store memory on the heap because of the overhead required by the memory allocator to find space for it.