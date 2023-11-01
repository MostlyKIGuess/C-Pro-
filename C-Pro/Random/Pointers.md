
- They store the [[Memory Address]] of a variable.
- Usually if it's a 32 bit pointer it has the size of 4 bytes.
- It is somewhat of a data type. It's format specifier is "%p".
- If we use "%d" specifier it would print the hexadecimal address to an integer address.
```c
#include <stdio.h>

int main(){
    int a=5;
	    printf("%p\n",&a); outputs : 00000000005ffe9c
	    printf("%d\n",&a);  outputs : 6291100
    return 0;
}
```

```c
int *a = &b;
and 
int *a;
a = &b;
while those both are same but 
int *a;
*a = &b;

is a different thing.
```

### Array Pointer
Name of [[Arrays]] is a **constant** pointer to the address of the first element of the array.
```c
arr = &arr[0]
```

You can not modify/change that pointer that is it uses
const type of stuff so you can't add 1 or perform operations on it.



It kind of points the whole array so when we print
```c
printf("%d\n"&a + 1)
```
This will give out the output of memory address of a + 4*(size of array)

assuming array is of int type that's why it is multiplied by 4.


![[pointers.excalidraw]]

```c
   Pointer to an integer`

    int *p;

    Pointer to an array of 5 integers

    int (*ptr)[5];

    int arr[5];

     Points to 0th element of the arr.

    p = arr;

    Points to the whole array arr.

    ptr = &arr;
```


[[Double Pointers]]

```c
#include <stdio.h>



int main(){

    int a[3][4] = {{1,2,3,4},{5,6,7,8},{9,10,11,12}};

    int (*ptr)[3][4];

  

    ptr = &a;

  

    printf("%d %d %d\n",*ptr,*(ptr+1),*(ptr+2));

    printf("%d %d %d\n",*(*ptr),*(*(ptr+1)),*(*(ptr+2)));

    printf("%d %d %d\n",***ptr,**(*(ptr+0)+1),*(*(*(ptr+0)+2)+1));

}
```
```c
OUTPUT: 6291040 6291088 6291136
        6291040 6291088 6291136
         1 5 10
``` 
It output's $+48$ because the array has 12 elements are ptr+1 points to another array.


here $*ptr$ points to the first row of the array of a 2D array.

![[Recording 20230913120639.webm]]
Is this clear? Is this clear to everybody? Similarly, can you do the third thing? Again, this is pt after 0, so since pt is here, then I will start pt here, which means it points to the 0th row of the array. Plus 2, which means it points to the last row. The row starting with 20. And then... Again... Wait, wait, wait. Before I do this... If pt after 0 star gives me the pointer pointing to the first row, plus 2 pointers pointing to the third row, and star of that gives me the pointer pointing to the address of 30, plus 1 gives me a pointer pointing to the address of 40. Then I do a dereferencing once more, that gives me the value 40. Is this clear step by step?

![[Recording 20230913121229.webm]]
input to the decimal dimension will be less than you want it to be this is a value code so you declare the array that you want to pass you pass the name of the array and in that function you define float whatever, num, whatever and that that's an array, that's again an array so the name of the array is again a pointer it's the same pointer that points to the same address as q and y I mean, please note that this num and this num are not the same thing with this I can replace this by abc and then say abc of i coincidentally is this clear? what? oh, if I want to print only the first two decimals I mean, let's leave that I don't want to print 6


[[Pointers vs Array]]

- (void * )0 is basically NULL pointer which is used for many purposes in C. 
- Please note that no matter what is the type of pointer, each pointer holds some address and the size of every pointer is equal to **sizeof(int)**.

















