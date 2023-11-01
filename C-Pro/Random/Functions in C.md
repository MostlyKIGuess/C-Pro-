
- Functions are of 2 types, return and void.
- **Return** function returns the data type which it was specified in. 
- For eg, int function(){} would return an integer.
- **Void** function doesn't have to return anything, they just compile the code which was inside the function.


### Arguments and Parameters

```c
int function(int a,int b,char c,float r)
```
here int a, int b, c ,r are called local parameters.
when we call the function to be used again in the main function we need to give it's arguments to it.

so if I want to use it I would call it as :
```c
int useoffunction = function(aint,b,car,road)
```
where they should be their respective data-types, function will automatically change their name to it's argument inside it's code. 


This is what we call pass by value and when we pass the data by reference by using it's own [[Memory Address]] then the changes that will be taken will be on the original variables unlike when we pass by value. In pass by value new local variables are formed inside the function which we pass on.

```c
// C program to illustrate Call by Reference
#include <stdio.h>
void swapx(int*, int*);

int main()
{
	int a = 10, b = 20;
		swapx(&a, &b);
			printf("Inside the Caller:\na = %d b = %d\n", a, b);
	return 0;
}

void swapx(int* x, int* y)
{
	int t;

	t = *x;
	*x = *y;
	*y = t;

	printf("Inside the Function:\nx = %d y = %d\n", *x, *y);
}

```
 If you want to do the same thing for value we don't use " * " to pass by value, for that case inside the main function, variables won't change.