---
tags:
  - java
  - data_structure
  - network
  - file_system
domain: E
finished: false
---
--- 
**Date**: 24.01.26
**Time**: 19:54 

> **Brief Summary**
> In Computer Science, Buffers are a special data structure that is meant to store temporary data that is generated from an input, and will eventually be consumed by an output. The main use case is for situations when the rate at which inputs are generated differs from the rate at which the output consumes the data. 

---
# Buffers

The main examples of Buffers in Java are the **BufferedInputReader** and the **BufferedOutputWriter**. These have briefly been convered in [[Java Class - Socket]] and [[Java File System]]. The Java file system library uses **Input/Output Streams** under the hood to manipulate files. Buffers are **ideal** for networking & file environments because it allows us to prevent **all** of the data being loaded **simultaneously**, and instead transfers data in chunks. The [[Producer Consumer Problem]] relies on the use of Buffers and a **Blocking Queue**, which allows us to efficiently handle Buffers in memory. 

#### Why Buffers?

**An Overview of Java's I/O Stream Class Heierarchy**
![[Pasted image 20260124201751.png]]

The main use case for buffers is to allow us to read data from a source in a more human-readable way. Using **buffered** readers and writers we can read larger chunks of data instead of **byte for byte**. Buffers let us store the chunk in memory preventing numerous calls for reading byte by byte. Since the data is stored in memory this also means that stream data can **sit** in our buffer. Therefore we use the **`InputStream/OutputStream.flush()`** method to ensure that all data that is currently in the buffer gets stored in its destination before continuing. 

Without buffers we would need to write byte for byte sind we can't store anything in memory, and therefore reading large files would tremendously slow down a computer.

See [[Producer Consumer Problem]] for a good example on why buffers are vital. 







---
## Related Topics
- [[]]







