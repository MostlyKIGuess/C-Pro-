```c
int array[];

for(int i=0;i<n-1;i++){
	int min_index = i;
		for(int j=i+1;j<n;j++){
			if(array[min_index]>array[j]){ 
				min_index = j;
				}
		}
		if(min_index != i){
			swap(array[i],array[min_index]);
		}
}
```
 The philosophy of Selection sort is how we as humans think about sorting, we go through the array **find the minimum element and then swap it with it's respective place**, as the minimum element should be on the lower most index.
 