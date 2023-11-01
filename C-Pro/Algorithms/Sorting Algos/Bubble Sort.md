```c
for (int i = 0; i < n; i++) { 
	for (int j = 0; j < n-1; j++) { 
		if (array[j] > array[j+1]) { 
			swap(array[j],array[j+1]); 
			} 
		} 
	}
```
The way bubble sort works is that we just swap the larger element of the array which is on the left side of a smaller element and we do this for n times to fully sort the array because in the worst case that is if the array is totally in descending order it will swap n,n-1....1 times hence we use the top for loop for n times. **We put the larger element on each iteration on it's respective position unlike selection sort.**