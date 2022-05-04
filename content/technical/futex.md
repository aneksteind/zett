---
tags: [operating-systems, system-call, threading]
---

A futex (fast userspace mutex) provides userspace applications a mechanism
for thread safety that does not require
a system call when the desired resource is uncontended.

Locking and synchronization primitives can be
built on top of futexes.

When an application wants to use a shared resource,
it can perform an atomic compare and set function
on some variable that will indicate success
in the uncontended case. This check prevents
the potential of expensive context switching perfomed
by the kernel in a system call.

When this operation fails, i.e. when the resource
is contended, the futex system call may be invoked
to let the kernel know that the application
would like to be put to sleep until the resource
is available.

The kernel keeps track of futexes across processes 
in a data structure keyed by futex id (usually its
address). The entry is usually a queue to provide 
FIFO access to wait requests.

When a process or thread is done with the shared 
resource, it will make a futex system call to wake one 
or more waiters. The kernel will remove the waiting 
threads from its internal futex state structure
after they are marked as runnable.

Processes can handle shared resources by memory
mapping the futex address.

#### Further Reading:

- [Basics of Futexes](https://eli.thegreenplace.net/2018/basics-of-futexes/)
- [Futexes are Tricky](https://www.akkadia.org/drepper/futex.pdf)
- [Futexes in Fuschia](https://fuchsia.dev/fuchsia-src/reference/kernel_objects/futex)
- [Robust Futexes](https://docs.kernel.org/locking/robust-futexes.html)
- [Futex Overview and Update](https://lwn.net/Articles/360699/)

