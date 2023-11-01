## C realloc() method

**“realloc”** or **“re-allocation”** method in C is used to dynamically change the memory allocation of a previously allocated memory. In other words, if the memory previously allocated with the help of malloc or calloc is insufficient, realloc can be used to **dynamically re-allocate memory**. re-allocation of memory maintains the already present value and new blocks will be initialized with the default garbage value.

### Syntax of realloc() in C
```c
ptr = realloc(ptr, newSize);
where ptr is reallocated with new size 'newSize'.
```

![[Pasted image 20230913124446.png]]