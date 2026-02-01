---
tags:
domain: E
finished: false
---
--- 
**Date**: 15.01.26
**Time**: 18:42 

> **Brief Summary**


---
# JVM Intricacies


**On the topic of "Monitors" and "Locks"**

Quote from [Inside the Java Virtual Machine](https://www.artima.com/insidejvm/ed2/threadsynchP.html)

> A thread in the Java virtual machine requests a lock when it arrives at the beginning of a monitor region. In Java, there are two kinds of monitor regions: synchronized statements and synchronized methods.

**Monitor**

> A monitor is like a building that contains one special room that can be occupied by only one thread at a time. The room usually contains some data. From the time a thread enters this room to the time it leaves, it has exclusive access to any data in the room. Entering the monitor building is called "entering the monitor." Entering the special room inside the building is called "acquiring the monitor." Occupying the room is called "owning the monitor," and leaving the room is called "releasing the monitor." Leaving the entire building is called "exiting the monitor."
> 
> In addition to being associated with a bit of data, a monitor is associated with one or more bits of code, which in this book will be called monitor regions.
> 
> As mentioned earlier, the language provides two built-in ways to identify monitor regions in your programs: synchronized statements and synchronized methods. These two mechanisms, which implement the mutual exclusion aspect of synchronization, are supported by the Java virtual machine's instruction set.

**Lock**

> To implement the mutual exclusion capability of monitors, the Java virtual machine associates a lock (sometimes called a mutex) with each object and class. A lock is like a privilege that only one thread can "own" at any one time.
> 
> A single thread is allowed to lock the same object multiple times. For each object, the Java virtual machine maintains a count of the number of times the object has been locked. An unlocked object has a count of zero. When a thread acquires the lock for the first time, the count is again incremented to one. Each time the thread acquires a lock on the same object, the count is again incremented.

[Zane XY](https://stackoverflow.com/questions/9848616/whats-the-meaning-of-an-objects-monitor-in-java-why-use-this-word)






---
## Related Topics
- [[]]







