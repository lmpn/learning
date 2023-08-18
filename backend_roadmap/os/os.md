# Operating system

An OS is an interface between hardware components and the user. 
The core software component is the kernel.

Types of OSes

- Batch:
- Multi tasking: different users share the same the CPU time
- Real time: short intervals between input and output
- Distributed: resources are distributed providing fast computations to the users
- Network: it provides the capability to serve to manage data, user, groups, security, application, and other networking functions.
- Mobile

Functions: 

- Memory management
- File management
- Process management
- I/O management
- Device management
- Secondary storage management
- Security
- Command interpretation
- Networking
- Communication management
- Job accounting : keep tracking of what and when a action happens

## Kernel

Central component whose task is to interact with the physical components directly.

Features

- IPC
- process synchronization
- context switching
- low level scheduling of processes
  
## Memory management

A program requires memory to run to:
- load its code
- store data
- load run time systems

Memory management is required to:
- allocate and deallocate memory
- track memory space by process
- minimize fragmentation
- maintain data integrity

There are different types of memory:
- Stack:
  - LIFO
  - Very fast
  - Static and finite (its size must be known at compile time)
  - A stack per thread
  - Stores local variables, pointers, and functions frames
- Heap
  - Slow
  - Shared among threads
  - Sensation of no limit of memory
  - Stores globals, references, maps, and other complex structures

RAM is finite, thus, consuming memory without releasing it may crash the program or OS. Several programming languages do automatic memory management to prevent the crashes.

### Manual memory management

It is the developer's responsibility to allocate and free memory.
IE: C/C++ provide malloc/free and new/delete.

### Garbage collection
Automatic heap management that frees unused memory allocations

- Mark & sweep:
  - 1st pass to mark objects that are alive
  - 2nd pass to free not marked objects
- Reference Counting
  - every object has a reference count
  - when reference count is zero the object is deleted

### RAII
The object memory allocation is tied to its lifetime, from construction to destruction

### Automatic reference counting
Similar to reference counting GC but relies on the developer to call retain and release.

### Onwership
Combination of RAII with an onwership model. A value always has a variable as owner and when it goes out of scope then the memory is freed.

### Swapping
Process of swapping a process's memory from the main memory to the secondary memory. Degrades performance.
### Fragmentation
Hole created after a program has been loaded and removed from memory this hole may not be assigned to another process because they can't combine or do not fulfill the memory requirements.

- Internal fragmentation: a process requires 2MB but there are only 3, 6, 7 MB blocks. In any of the blocks there will be memory wasted
- External fragmentation: given 2 processes of 2MB and 4MB allocated in 3MB and 6MB, there is a total of 3MB that aren't used however if a new process with the requirement of 3MB is executed the free memory cannot be used.

### Paging
Process of retrieving processes in form of pages from the secondary to main memory allowing the memory of a process to be non-contiguous. This process reduces extrenal fragmentation and improves memory utilization.

## Inter process communication (IPC)
Mechanism that allows processes to communicate, synchronize their actions, or manage shared data

Approaches:
- File
- Signal
- Socket
- Message queue
- Anonymous pipe
- Name pipe
- Shared memory
- Message passing
- Memory-mapped file