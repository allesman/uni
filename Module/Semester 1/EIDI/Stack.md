---
tags:
  - data_structure
  - java
domain: E
finished: true
---
--- 
**Date**: 17.01.26
**Time**: 14:25 

> **Brief Summary**
> A stack is a high-level implementation of a [[Linked List|linked list]] that uses the **LIFO** principle to push and pop elements.

---
# Stack

A stack uses a linked list under the hood, and has two main operations. **`push()`** and **`pop()`**. Stacks are very useful in recursive programming, as they mimick the behavior of a recursive function.

**`push()`**
This **appends** an element at the **end** of the linked list. The new element becomes the tail of the list.

**`pop()`**
This method **removes** the element at the **end** of the linked list, usually the tail.

Stacks operate on the Last In First Out principle which means that the **last** element that was added to the stack is the **first** one to go when invoke pop() on the stack. Just like [[Queue|queues]], there are generally no methods that let you manipulate elements within the stack besides push() and pop().

**`peek()`**
This method lets you look at the **last** element of the linked list without removing it.

---
## Related Topics
- [[Queue]]
- [[Linked List]]







