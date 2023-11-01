1. **“calloc”** or **“contiguous allocation”** method in C is used to dynamically allocate the specified number of blocks of memory of the specified type. it is very much similar to malloc() but has two different points and these are:
2. It initializes each block with a default value ‘0’.
3. It has two parameters or arguments as compare to malloc().

### Syntax of calloc() in C

```c
ptr = (cast-type*)calloc(n, element-size);
here, n is the no. of elements and element-size is the size of each element.

For Example:

 ptr = (float*) calloc(25, sizeof(float));  
 This statement allocates contiguous space in memory for 25 elements each with the size of the float.
 ```
