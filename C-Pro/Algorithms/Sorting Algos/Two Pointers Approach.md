**Q)** Sort an array by negative and positive integers with the negative no. on the left side and positive on the right;
```c
int i=0;
int j=n-1;
while(i<=j){
		if(array[j]>0 && array[i]>0){
				j--;
			}
		else if(array[i]<0 && array[j]<0){
				i++;
			}
		else if(array[i]>0 && array[j]<0){
			swap(i,j);
			}		
		else {
		i++;
		j--;
		}	
}
```
